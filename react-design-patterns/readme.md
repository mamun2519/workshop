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

UI Components handle rendering.
Logic Components handle data-fetching, state management, or API interactions.
Routing, State, and Business Logic are kept modular to improve maintainability.
