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

Easier Maintenance – When a component has a single responsibility, it’s easier to update.
Better Readability – Developers can quickly understand the purpose of each component.
Improved Reusability – Smaller, focused components can be reused in multiple places.
Simplified Testing – Testing a small, focused component is easier than testing a large, complex one.
