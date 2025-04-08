# `useCallback` Hook in React  

## Introduction  
The `useCallback` hook is a React Hook that **memoizes** a function, preventing it from being re-created on every render unless its dependencies change. It helps optimize performance by avoiding unnecessary re-renders in components that depend on callback functions.  

---

## Syntax  
```javascript
const memoizedCallback = useCallback(
  () => {
    // Function logic here
  },
  [dependencies]
);
```
# Example Usage of `useCallback`  

## `memoizedCallback` and `dependencies`  
- **`memoizedCallback`**: The function that remains stable between renders unless dependencies change.  
- **`dependencies`**: An array of values that determine when the function should be re-created.  

---

## Without `useCallback` (Inefficient)  
In the example below, the `handleClick` function is **re-created on every render**, which can lead to unnecessary re-renders in child components.  

```javascript
import React, { useState } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
};

export default Counter;
```
## Issue Without `useCallback`  
Every time the component **renders**, `handleClick` is **recreated**, leading to **unnecessary re-renders** in child components.  

---

## ✅ With `useCallback` (Optimized)  
By using `useCallback`, we ensure that `handleClick` is **only re-created when `count` changes**.  

```javascript
import React, { useState, useCallback } from "react";

const Counter = () => {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    setCount(prevCount => prevCount + 1);
  }, []);

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={handleClick}>Increment</button>
    </div>
  );
};

export default Counter;
```
# Benefits of `useCallback`  

✅ **Performance Optimization**: Prevents unnecessary function re-creation, improving performance.  
✅ **Useful in Memoized Components**: Works well with `React.memo` to prevent unnecessary re-renders.  
✅ **Stable Function References**: Ensures child components receive the same function reference if dependencies haven't changed.  
