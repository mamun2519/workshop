# React Design Pattern

## Container Presentation Pattern

The Container-Presentation Pattern is a design pattern in React that separates UI components (Presentation Components) from logic and data-fetching components (Container Components).

**Importance of Container Presentation Pattern:**

- **Separation of Concerns** – It keeps UI components clean and focused only on rendering while keeping data-fetching and business logic separate.
- **Reusability** – The same presentation component can be reused with different data sources.
- **Easier Maintenance** – Changes in logic don’t affect the UI and vice versa.
- **Better Testing** – You can test UI separately from business logic.

## Separation of Concerns (SoC):

Separation of Concerns (SoC) is a software design principle that suggests dividing a program into distinct sections, where each section addresses a separate concern.

In React, this means breaking an application into independent, reusable parts, where:

- UI Components handle rendering.
- Logic Components handle data-fetching, state management, or API interactions.
- Routing, State, and Business Logic are kept modular to improve maintainability.

## Single Responsibility Pattern (SRP):

The Single Responsibility Principle (SRP) states that a component should have one reason to change—it should do one thing well.

In React, this means:

- UI components should only handle rendering
- Logic components should manage state and data fetching
- Reusable utilities should handle specific tasks (e.g., formatting, API calls)

### Why is SRP Important?

1. **Easier Maintenance** – When a component has a single responsibility, it’s easier to update.
2. **Better Readability** – Developers can quickly understand the purpose of each component.
3. **Improved Reusability** – Smaller, focused components can be reused in multiple places.
4. **Simplified Testing** – Testing a small, focused component is easier than testing a large, complex one.

# Two Most Common Patterns: HOC & Render Props

A Higher-Order Component (HOC) is a pattern in React that allows you to re-use component logic. It's a function that takes a component and returns a new component with additional props or logic.

HOCs are commonly used for:

- Reusing component logic
- Adding extra features like authentication, logging, etc.
- Modifying props or behavior of the wrapped component without changing the original component.

## Render Props

A render prop is a pattern in React where a component uses a function prop to know what to render. This pattern allows you to share code between components using a function that returns a React element.

Instead of the component rendering something directly, it provides a function (a "render prop") to the consumer of the component. This function then returns what the component should render.

### Why is Render Props Important?

1. **Reusable Logic**: Render props allow for code reuse across multiple components. You can share logic between components without using inheritance or mixins.
2. **Separation of Concerns:** By separating logic from presentation, render props help keep components more focused on a single responsibility.
3. **Flexibility:** Render props provide a high level of flexibility. You can change what gets rendered based on the function you pass to the component, and you can control how components behave by passing different functions.
4. **Composability:** You can compose different behaviors by using multiple render prop components. Each component can provide its own logic, and the consumer can decide how to combine them.

### Use Cases for Render Props

1. **Sharing state or logic:** When you need to share logic or state between multiple components (e.g., managing form state or handling mouse position).
2. **Conditional rendering**: When you want to control what gets rendered based on certain conditions or logic.
3. **Code reuse:** When you want to reuse a block of code that renders UI elements in different ways, but with shared logic.
4. **Dynamic content rendering:** When the content or structure needs to be dynamic and controlled from outside the component.

## Function as Children Prop Pattern

The Function as Children Prop (also known as Render Props with children) pattern in React allows passing a function as the children prop to a component. This function receives data or state from the component and returns JSX, making the component flexible and reusable.

### **Why is it Important?**

- **Enhances Reusability** – Instead of duplicating logic, different components can use the same logic but customize rendering.
- **Promotes Separation of Concerns (SoC)** – The logic and UI rendering are decoupled, making maintenance easier.
- **Flexible Component Customization** – The parent component can fully control how the child is rendered.
  **Note:**

- Any time we need hooks we can use Function as Children Prop Pattern. It won’t introduce any junk inside the JSX but provides enhanced functionalities.
- Any time you need complex logic or flow inside JSX use Children Prop Pattern.

## Context API

The Context API in React provides a way to pass data deeply through the component tree without needing to manually pass props at every level (a.k.a. "prop drilling"). It is mainly used for global state management in scenarios where multiple components need access to shared data.

### When to Use Context API?

- **Theme Management** – Light/Dark mode switching.
- **Authentication State** – User login status across the app.
- **Language/Localization** – Multi-language support.
- **Global UI State** – Sidebar visibility, modals, notifications.
- **Application Configurations** – Feature flags, environment settings.
- **Form State Sharing** – Multi-step forms where data is shared across steps.

### Strengths of Context API

- **Removes Prop Drilling** – No need to pass props through multiple levels.
- **Lightweight Alternative to State Management Libraries** – No need for Redux or Zustand for simple state sharing.
- **Built-in and Native to React** – No extra dependencies.
- **Flexible** – Works with any data type (booleans, strings, objects, functions).

### Weaknesses of Context API

- **Re-renders All Consumers When Context Changes** – Even if only part of the context changes, all consuming components render.
- **Not Ideal for High-Frequency Updates** – If data updates frequently (e.g., real-time stock prices), Context API may cause - performance issues.
- **Complex Debugging**– If multiple contexts exist, debugging can become challenging.

## Compound Components

The Compound Component Pattern in React allows multiple related components to work together as a single unit. Instead of passing multiple props to control child components, compound components communicate implicitly through context or React’s children prop.

This pattern is useful when you want to design flexible, reusable UI components that allow users to compose them in different ways.

### When to Use Compound Components? (Use Cases)

- **Building UI libraries** – Tabs, Accordions, Dropdowns, Modals, etc.
- **Designing flexible**, reusable components – Form controls, Wizards.
- **When multiple components share a common state** – Controlled components.
- **Improving code readability & maintainability** – Reducing prop drilling.

## Control Props Pattern

The Control Props Pattern is a flexible way to allow both internal and external control over a component’s state. This is useful when you want to provide default behavior while also allowing consumers of your component to override it when needed.

### What is Control Props Pattern?

In React, components often manage their own state internally. However, sometimes we need to give users the ability to control that state from the outside while keeping an optional internal fallback.

With the **Control Props Pattern**, we:

- Allow state to be controlled internally (default behavior).
- Let consumers control it externally when needed.
- Detect whether a prop is controlled or uncontrolled.
- Fire callbacks (e.g., onChange) to keep the external state in sync.
  Why is it Important?
  More Flexibility – Components can be used in controlled and uncontrolled modes.
  Better Reusability – Works in different use cases without modifying the core logic.
  Avoids Unnecessary State – Lets the consumer manage state only when necessary.
  Keeps Components Declarative – External control makes it easy to manage from the parent.
  When to Use Control Props?
  You need both default internal state and external control.
  Users might want to override the behavior with their own logic.
  You need two-way data binding between the component and parent.
  You want a component to be partially controlled (e.g., controlled by a prop but still has default behavior).
  Provider Pattern
  The Provider Pattern in React is a design pattern that allows state, functions, or dependencies to be shared across a component tree without passing them manually via props at every level.

How It Works
The Provider Pattern in React is implemented using Context API. It enables a centralized store of data or dependencies, which is then accessed by child components using useContext.

Benefits of the Provider Pattern

Removes prop drilling
Encapsulates shared state or dependencies
Encourages separation of concerns
Easier to test and manage dependencies
