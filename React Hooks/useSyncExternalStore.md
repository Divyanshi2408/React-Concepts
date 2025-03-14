# `useSyncExternalStore` Hook in React

## Overview
The `useSyncExternalStore` hook in React is used to subscribe to external stores and ensure that UI updates remain consistent with external state changes.

## Syntax
```jsx
const state = useSyncExternalStore(subscribe, getSnapshot, getServerSnapshot?);
```

## Parameters
- **`subscribe`**: A function that registers a callback to re-run when the store changes.
- **`getSnapshot`**: A function that returns the current state from the store.
- **`getServerSnapshot`** (optional): A function to provide the initial state when rendering on the server.

## When to Use `useSyncExternalStore`
- Managing state from external sources (e.g., Redux, Zustand, browser APIs).
- Keeping UI updates in sync with state management libraries.
- Ensuring consistency in server-side rendering (SSR) environments.

## Example Usage
```jsx
import React, { useSyncExternalStore } from "react";

// A simple store
const store = {
  state: 0,
  listeners: new Set(),
  subscribe(listener) {
    store.listeners.add(listener);
    return () => store.listeners.delete(listener);
  },
  getSnapshot() {
    return store.state;
  },
  increment() {
    store.state += 1;
    store.listeners.forEach(listener => listener());
  }
};

function Counter() {
  const count = useSyncExternalStore(store.subscribe, store.getSnapshot);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={store.increment}>Increment</button>
    </div>
  );
}

export default Counter;
```

## Key Points
- Ensures consistent UI updates with external state.
- Works well with state management libraries like Redux or Zustand.
- Handles **server-side rendering (SSR)** by providing `getServerSnapshot`.
- **More reliable than `useEffect` with subscriptions** in concurrent rendering.

## When Not to Use `useSyncExternalStore`
- When working with local component state (use `useState` instead).
- If managing state within React only (use `useContext` or `useReducer`).
- For complex state updates where libraries like Redux provide better solutions.

## React Version
`useSyncExternalStore` was introduced in **React 18**. Ensure your project is running React 18+ to use this hook.

## References
- [React Docs: useSyncExternalStore](https://react.dev/reference/react/useSyncExternalStore)
