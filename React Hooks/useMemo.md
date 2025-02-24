# `useMemo` Hook in React  

The `useMemo` hook is used to memoize the result of a computation, preventing unnecessary recalculations on each render.  

## Syntax  
```javascript
const memoizedValue = useMemo(() => computeExpensiveValue(dependencies), [dependencies]);
```
# `useMemo` Hook in React  

The `useMemo` hook is used to memoize the result of a computation, preventing unnecessary recalculations on each render.  

## Parameters  
- **computeExpensiveValue**: A function that returns the computed value.  
- **dependencies**: An array of values that determine when the memoized value should be recalculated.  

## Example Usage  

### Without `useMemo` (Inefficient)  
In this example, the `computeExpensiveValue` function runs on every render, even if `count` hasn't changed.  

```javascript
import React, { useState } from "react";

const ExpensiveComponent = ({ num }) => {
  const computeExpensiveValue = (num) => {
    console.log("Computing...");
    return num * 2;
  };

  const [count, setCount] = useState(0);
  const result = computeExpensiveValue(num);

  return (
    <div>
      <h2>Count: {count}</h2>
      <h3>Computed Value: {result}</h3>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};

export default ExpensiveComponent;
```
# Optimized Computation with `useMemo`  

By using `useMemo`, the computation only runs when `num` changes, avoiding unnecessary calculations.  

```javascript
import React, { useState, useMemo } from "react";

const ExpensiveComponent = ({ num }) => {
  const computeExpensiveValue = (num) => {
    console.log("Computing...");
    return num * 2;
  };

  const [count, setCount] = useState(0);
  const memoizedResult = useMemo(() => computeExpensiveValue(num), [num]);

  return (
    <div>
      <h2>Count: {count}</h2>
      <h3>Computed Value: {memoizedResult}</h3>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};

export default ExpensiveComponent;
```
# Benefits of `useMemo`  

✅ **Performance Optimization**: Prevents expensive calculations from running on every render.  
✅ **Useful in Heavy Computations**: Ideal for optimizing functions that require intensive processing.  
✅ **Avoids Unnecessary Re-renders**: Helps in scenarios where a computed value doesn't need to change frequently.  

## When to Use `useMemo`  

- When a component has expensive calculations that don't need to run on every render.  
- When preventing unnecessary re-renders in child components by passing memoized values as props.  
- When working with large lists and filtering/sorting operations.  
