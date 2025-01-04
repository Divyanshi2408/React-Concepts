# useEffect Hook: Managing Side Effects in Functional Components

The `useEffect` Hook, introduced in React 16.8, is a powerful tool for managing side effects in functional components. It enables you to handle effects like API calls, DOM manipulation, or subscription management, all within a clean, functional paradigm.

---

## Why useEffect?

- **Handles Side Effects**: Enables functional components to manage side effects like:
  - Interacting with the DOM (e.g., updating the title).
  - Fetching data from APIs.
  - Managing subscriptions (e.g., event listeners, timers).
- **Replaces Lifecycle Methods**: Combines the functionality of `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` into a single API.
- **Modern and Functional**: Eliminates the need for lifecycle methods, promoting simplicity and maintainability.

---

## Core Features

1. **Declarative and Reactive**: React automatically runs the effect at the appropriate time based on dependencies.
2. **Combines Lifecycle Methods**: Use a single `useEffect` for logic that previously required multiple lifecycle methods in class components.
3. **Runs After Rendering**: By default, `useEffect` runs after the component renders, ensuring the DOM is updated before the effect executes.

---

## Syntax

```javascript
useEffect(() => {
  // Side effect logic here
  return () => {
    // Cleanup logic (optional)
  };
}, [dependencies]); // Dependency array (optional)
```
