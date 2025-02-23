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
