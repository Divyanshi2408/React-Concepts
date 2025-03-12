# `useId` Hook in React

## Overview
The `useId` hook in React is used to generate unique IDs that remain consistent across renders. It is particularly useful for associating form inputs with labels, generating accessibility attributes, or ensuring unique keys.

## Syntax
```jsx
const id = useId();
```

## When to Use `useId`
- Assigning `id` attributes in forms to link `<label>` and `<input>` elements.
- Generating consistent IDs for elements requiring accessibility attributes like `aria-labelledby`.
- Avoiding ID conflicts when rendering multiple components.

## Example Usage
```jsx
import React, { useId } from "react";

function FormComponent() {
  const id = useId();

  return (
    <div>
      <label htmlFor={id}>Enter your name:</label>
      <input id={id} type="text" placeholder="Name" />
    </div>
  );
}

export default FormComponent;
```

## Key Points
- `useId` generates a unique ID per component instance.
- The generated ID is **stable across re-renders**.
- It is **not suitable for keys in lists** (use array indexes or unique identifiers instead).
- Works only inside **React function components**.
- Avoid using it for server-generated IDs as they might mismatch on hydration.

## Alternative Approaches
If unique IDs are required outside React, consider:
- `uuid` library: `import { v4 as uuidv4 } from 'uuid';`
- `Math.random().toString(36).substr(2, 9)` for quick unique IDs (though not guaranteed unique).

## When Not to Use `useId`
- If you need globally unique IDs across multiple renders or sessions.
- If your ID must be persisted (e.g., stored in a database).

## React Version
`useId` was introduced in **React 18**. Ensure your project is running React 18+ to use this hook.

## References
- [React Docs: useId](https://react.dev/reference/react/useId)
