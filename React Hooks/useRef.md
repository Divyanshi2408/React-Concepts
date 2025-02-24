# `useRef` Hook in React

The `useRef` hook is used to persist values across renders without causing a re-render. It is commonly used to reference DOM elements and store mutable values.

## Parameters  
- **initialValue**: The initial value assigned to the ref object.

## Returns  
- **refObject**: An object with a `.current` property that holds the mutable value.

## Example Usage  

### **1. Referencing a DOM Element**  
The following example demonstrates how `useRef` can be used to access and manipulate a DOM element.

```javascript
import React, { useRef } from "react";

const InputFocus = () => {
  const inputRef = useRef(null);

  const handleFocus = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" placeholder="Type here..." />
      <button onClick={handleFocus}>Focus Input</button>
    </div>
  );
};

export default InputFocus;
```
