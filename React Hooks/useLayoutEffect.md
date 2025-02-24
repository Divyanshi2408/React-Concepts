# `useLayoutEffect` Hook in React

The `useLayoutEffect` hook is similar to `useEffect`, but it fires synchronously after all DOM mutations. This ensures that updates are applied before the browser paints, preventing visible flickers.

## Example Usage

### Without `useLayoutEffect` (Potential Flicker)
In this example, the effect runs after the browser paint, causing a brief flicker.

```javascript
import React, { useEffect, useState } from "react";

const Example = () => {
  const [width, setWidth] = useState(window.innerWidth);

  useEffect(() => {
    setWidth(window.innerWidth);
  }, []);

  return <h2>Width: {width}</h2>;
};

export default Example;
```
