# `useInsertionEffect` Hook in React

## Overview
The `useInsertionEffect` hook in React is designed for injecting styles dynamically before the browser paints the screen. It runs synchronously before DOM mutations, making it useful for **CSS-in-JS libraries** and **critical style insertions**.

## Syntax
```jsx
useInsertionEffect(() => {
  // Perform synchronous style insertion
  return () => {
    // Cleanup if necessary
  };
}, [dependencies]);
```

## When to Use `useInsertionEffect`
- Injecting styles in **CSS-in-JS libraries** like Emotion or styled-components.
- Ensuring styles are applied before DOM updates to prevent flickering.
- Avoiding performance issues caused by delayed CSS injection.

## Example Usage
```jsx
import React, { useInsertionEffect } from "react";

function DynamicStylesComponent() {
  useInsertionEffect(() => {
    const style = document.createElement("style");
    style.textContent = `
      .dynamic-style {
        color: red;
        font-weight: bold;
      }
    `;
    document.head.appendChild(style);
    
    return () => {
      document.head.removeChild(style);
    };
  }, []);

  return <p className="dynamic-style">Styled with useInsertionEffect</p>;
}

export default DynamicStylesComponent;
```

## Key Points
- Runs **before layout effects (`useLayoutEffect`)** and DOM updates.
- Used for injecting styles **synchronously**.
- Improves performance by preventing unnecessary reflows and flickers.
- Not intended for general side effects (use `useEffect` instead).

## When Not to Use `useInsertionEffect`
- If you’re **not dealing with styles** or injecting CSS.
- When working with **asynchronous side effects** (use `useEffect`).
- If you don’t need to modify styles dynamically at runtime.

## React Version
`useInsertionEffect` was introduced in **React 18**. Ensure your project is running React 18+ to use this hook.

## References
- [React Docs: useInsertionEffect](https://react.dev/reference/react/useInsertionEffect)
