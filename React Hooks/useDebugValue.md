# `useDebugValue` Hook in React

## What is `useDebugValue`?
`useDebugValue` is a React Hook that helps developers debug custom hooks by providing a label that appears in React DevTools.

## Syntax
```javascript
useDebugValue(value, formatFunction);
```
### Parameters:
- **value**: The value to display in React DevTools.
- **formatFunction (optional)**: A function to format the displayed value.

### Usage:
`useDebugValue(value, formatFunction?)` is used inside custom hooks to provide meaningful debugging information in React DevTools.

# Example: Without `useDebugValue`

### Issue:
Without `useDebugValue`, React DevTools does not provide meaningful debugging information for custom hooks.

```javascript
import { useState } from "react";

const useCounter = () => {
  const [count, setCount] = useState(0);
  return [count, () => setCount(count + 1)];
};

export default useCounter;
```
