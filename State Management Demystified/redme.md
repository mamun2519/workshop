# Unidirectional State Management

## What is a Unidirectional State?

Unidirectional state means that data flows in one direction, following a predictable pattern. In React and other state management libraries like Redux, Zustand.

This concept ensures that changes in state always follow a clear, structured path.

### How Does Unidirectional State Work?

**Data Flows Down**

- The state is stored in a single source of truth (like Redux store, Zustand store).
- This state is passed down to child components.

**Actions Trigger State Updates**

- A user interacts with the UI (e.g., clicking a button).
- The event dispatches an action (like Redux dispatch).
- The state updates and the changes flow back down to the UI.

There are many popular unidirectional global state management solutions available, such as Redux and Zustand. Let’s see how they work in code with a simple user state.

# Zustand

Zustand is a fast, scalable, and minimalistic state management library for React. Unlike Redux, it doesn’t require reducers, actions, or a lot of boilerplate. It allows you to create a global state using a simple hook-based API.

## **Zustand Store**

```js
import { User } from "../type";
import { create } from "zustand";
import { immer } from "zustand/middleware/immer";
import { persist, createJSONStorage } from "zustand/middleware";

type Store = {
  user: User | null,
  demoString: string | null,
};

type Actions = {
  logIn: (user: User) => void,
  logOut: () => void,
  updateDemoString: (demoString: string) => void,
};

type ComposeStateType = Store & Actions;

// Store
export const useUserStore =
  create <
  ComposeStateType >
  ((set) => ({
    user: null,
    demoString: null,
    logIn: (user: User) => {
      set({ user });
    },

    logOut: () => {
      set({ user: null });
    },
    updateDemoString: (demoString: string) => {
      set((state) => ({ ...state, demoString }));
    },
  }));

// Store Example with persist and immer middleware

export const useUserStore2 = create(
  persist(
    immer <
      ComposeStateType >
      ((set) => ({
        user: null,
        demoString: null,
        logIn: (user: User) => {
          set((state) => {
            state.user = user;
          });
        },

        logOut: () => {
          //   set({ user: null });
          set((state) => {
            state.user = null;
          });
        },
        updateDemoString: (demoString: string) => {
          // set((state) => {});
          set((state) => {
            state.demoString = demoString;
          });
        },
      })),

    {
      name: "user-store",
      storage: createJSONStorage(() => localStorage),
    }
  )
);
```

## Zustand Client code

```js
import { useUserStore } from "./useStore";

export const ZustandUserDetails = () => {
  //   const { user, logIn, logOut, updateDemoString } = useUserStore();
  const user = useUserStore((state) => state.user);
  const logIn = useUserStore((state) => state.logIn);
  const logOut = useUserStore((state) => state.logOut);
  const updateDemoString = useUserStore((state) => state.updateDemoString);

  const handleLogin = async (userId: string) => {
    const response = await fetch(
      `https://jsonplaceholder.typicode.com/users/${userId}`
    );
    const user = await response.json();
    logIn(user);
  };
  return (
    <div>
      <pre>{JSON.stringify(user, null, 2)}</pre>
      <br />
      <button onClick={() => handleLogin("1")}>Log In</button>
      <button onClick={logOut}>Log Out</button>
      <br />
      <button onClick={() => updateDemoString("Hello world" + Math.random())}>
        Update Demo String
      </button>
    </div>
  );
};
```

# Redux Toolkit

Redux Toolkit (RTK) is the official, recommended way to write Redux logic. It simplifies Redux development by reducing boilerplate code, improving performance, and providing built-in tools for handling complex state management.

## Redux Store

```js
import { PayloadAction, createSlice } from "@reduxjs/toolkit";
import { TypedUseSelectorHook, useDispatch, useSelector } from "react-redux";
import { configureStore } from "@reduxjs/toolkit";
import { User } from "../type";

// Define the state type
interface UserState {
  user: User | null;
  demoText: string | null;
}

// Create the slice
const userSlice = createSlice({
  name: "user",
  initialState: {
    user: null,
    demoText: null,
  } as UserState,
  reducers: {
    logIn: (state, action: PayloadAction<User>) => {
      state.user = action.payload;
    },
    logOut: (state) => {
      state.user = null;
    },
    updateDemoText: (state, action: PayloadAction<string>) => {
      state.demoText = action.payload;
    },
  },
});

// Configure the store
const store = configureStore({
  reducer: {
    user: userSlice.reducer,
  },
});

// Export actions
export const { logIn, logOut, updateDemoText } = userSlice.actions;

// Infer RootState and AppDispatch types from store
export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;

// Export typed versions of hooks
export const useAppDispatch = () => useDispatch<AppDispatch>();
export const useAppSelector: TypedUseSelectorHook<RootState> = useSelector;

export default store;

```

## Redux client Code

```js
// Redux Provider Component
import React, { FC } from "react";
import { Provider } from "react-redux";
import store from "./useStore";

type ReducerWrapperType = {
  children: React.ReactNode,
};
export const ReduxWrapper: FC<ReducerWrapperType> = ({ children }) => {
  return <Provider store={store}>{children}</Provider>;
};
```

```js
// UserDetail.tsx
import React from "react";
import { logIn, logOut, useAppDispatch, useAppSelector } from "./useStore";

export const ReduxUserDetails = () => {
  const user = useAppSelector((state) => state.user.user);
  const dispatch = useAppDispatch();

  const handleLogin = async () => {
    const response = await fetch(
      "https://jsonplaceholder.typicode.com/users/1"
    );
    const userData = await response.json();
    dispatch(logIn(userData));
  };
  return (
    <div>
      {JSON.stringify(user, null, 2)}
      <button onClick={handleLogin}>Log In</button>
      <button onClick={() => dispatch(logOut())}>Log Out</button>
    </div>
  );
};
```

```js
// App.tsx
<ReduxWrapper>
  <ReduxUserDetails />
</ReduxWrapper>
```

# Atomic State

## What is an Atomic State?

An atomic state is a small, independent piece of state that can be composed together to build complex state management. These atoms are globally accessible, meaning any component can import, read, and write data without causing unnecessary re-renders in unrelated parts of the application.

## When to Use Atomic State (Recoil, Jotai)?

1. Granular State Updates – Only update the necessary pieces of state without rerendering the whole component tree.
2. Independent, Composable State – Small, isolated state units (atoms) that can be combined dynamically.
3. Globally Accessible State – Any component can read/write atoms without prop drilling or context.
4. Shared UI State – Great for managing UI-related states like modals, filters, themes, or form steps.

**There are two popular libraries to manage Atomic State**

1. Jotai
2. Recoil
   Their goal is the same: to maintain an atomic state, but the underlying implementations differ. Let’s see how they work in code with a simple user state.

# Jotai

Jotai is a primitive and flexible atomic state management library for React, designed to be simple yet powerful. Inspired by Recoil, it provides fine-grained reactivity while keeping things minimal and easy to use.

## Jotai Store

```js
// userAtom.ts
import { atomWithStorage } from "jotai/utils";
import { atom } from "jotai";
import { User } from "../../type";

// Notmal Store
export const userAtom = (atom < User) | (null > null);

// Persited
const darkModeAtom = atomWithStorage("darkMode", false);
```

## Jotai Client Code

```js
import { useAtom, useAtomValue, useSetAtom } from "jotai";
import React from "react";
import { userAtom } from "./userAtoms";

export const JotaiUserDetails = () => {
  // normal approach look like react useState
  // const [user, setuser] = useAtom(userAtom);

  // with selector
  const user = useAtomValue(userAtom);
  const setuser = useSetAtom(userAtom);

  const updateuserHandler = () => {
    setuser({ id: 1, name: "rasel", email: "exmaple@example.com" });
  };
  return (
    <div>
      user: {JSON.stringify(user, null, 2)}
      <br />
      <button onClick={updateuserHandler}> Update User</button>
    </div>
  );
};
```

# Recoil

Recoil is a state management library for React that is designed to handle shared state across components efficiently. It introduces the concept of atoms (units of state) and selectors (derived state), allowing fine-grained reactivity with minimal re-renders.
