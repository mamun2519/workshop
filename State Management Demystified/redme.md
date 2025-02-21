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

**Zustand Store**

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
