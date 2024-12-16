## Thinking a React

### End of this workshop

- we will have this full-featured CMS for users.
- we will cover almost all the major topics that create issues in the design decision.
- we will know how to structure the codebase in the best possible manner.
- we will know how to delegate responsibilities to other components.
- overall we will change the way we think and write our frontend codes.

**Note**: React Is not a framework

if you are looking for a framework go with

- Next
- Remix
- asto

### React Are not provide

- No Build in routing
- no build in app level state management
- no build in data fetching techniques
- no build response caching and invalidation features
- no build-in session, cookies management features

### indirectly, it is saying how to treat react

- it is one of the best solutions to create complex UIs in the world
- so, while dealing with react forget about other noises.
- and focuses on only single features.

### A senior engineer must do

**functionality:**

- What is the component supposed to do?
- are there any dynamic behaviors are there any APIs called
- can we have any reusable utilities of hooks?

**Data flow**

- what inputs does the component require?
- what output events does it produce?
- how will the data flow from parent to child?
- how many containers are required?

**state management**

- which part of the state should be local, lifted to a parent or stored in a global or context
- is there any state that is communicating with other features?

**Reusability**

- Will this component or child of this feature be resued elsewhere?
- should it be generic or context-specific?
- Do we have any already declared components that we can reuse?
- can we create reusable utilities, hooks, or network calls?

**Performance**

- Are there specific performance constraints (e.g: frequent update, large datasets, blocking UI that required concurrency, do we need virtualization, debounce or memorization)

**Error Handling**

- How to handle errors?
- what are the possible edge-case scenarios?
- Do we need to implement a retry mechanism?
- should we use error conditionally?
