# Unidirectional State Management

## What is a Unidirectional State?

Unidirectional state means that data flows in one direction, following a predictable pattern. In React and other state management libraries like Redux, Zustand.

This concept ensures that changes in state always follow a clear, structured path.

### How Does Unidirectional State Work?

**Data Flows Down**

- The state is stored in a single source of truth (like Redux store, Zustand store).
- This state is passed down to child components.
