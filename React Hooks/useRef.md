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
**Benefit**: The input field gets focused when the button is clicked without causing a re-render.

## Persisting Values Without Re-render

Unlike `useState`, changing a `useRef` value does not trigger a re-render.

```javascript
import React, { useRef, useState } from "react";

const ClickCounter = () => {
  const countRef = useRef(0);
  const [renderCount, setRenderCount] = useState(0);

  const handleClick = () => {
    countRef.current += 1;
    console.log(`Button clicked ${countRef.current} times`);
  };

  return (
    <div>
      <h2>Render Count: {renderCount}</h2>
      <button onClick={handleClick}>Click Me</button>
      <button onClick={() => setRenderCount(renderCount + 1)}>Re-render</button>
    </div>
  );
};

export default ClickCounter;
```
**Benefit**: The click count persists without re-rendering the component.

## Benefits of `useRef`

✅ **Accessing DOM Elements**: Enables direct manipulation of DOM elements.  
✅ **Persisting Values Across Renders**: Stores mutable values without causing re-renders.  
✅ **Optimizing Performance**: Avoids unnecessary state updates.  

## When to Use `useRef`

- When accessing or modifying DOM elements directly.  
- When storing values that should persist between renders but don’t need to trigger a re-render.  
- When using interval or timeout references (e.g., `setTimeout` or `setInterval`).  
