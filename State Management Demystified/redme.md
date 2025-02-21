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
