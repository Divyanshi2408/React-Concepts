# `useTransition` Hook in React

## Overview
The `useTransition` hook in React is used to manage state updates with lower priority, allowing the UI to remain responsive during heavy computations or transitions.

## Syntax
```jsx
const [isPending, startTransition] = useTransition();
```

## When to Use `useTransition`
- Deferring expensive state updates to keep the UI responsive.
- Enhancing user experience when rendering large lists or data-heavy components.
- Avoiding UI freezes by marking certain updates as **non-urgent**.

## Example Usage
```jsx
import React, { useState, useTransition } from "react";

function SearchComponent({ data }) {
  const [query, setQuery] = useState("");
  const [filteredData, setFilteredData] = useState(data);
  const [isPending, startTransition] = useTransition();

  const handleSearch = (e) => {
    const value = e.target.value;
    setQuery(value);
    
    startTransition(() => {
      setFilteredData(data.filter(item => item.includes(value)));
    });
  };

  return (
    <div>
      <input type="text" value={query} onChange={handleSearch} placeholder="Search..." />
      {isPending && <p>Loading...</p>}
      <ul>
        {filteredData.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
  );
}

export default SearchComponent;
```

## Key Points
- `useTransition` helps mark certain state updates as **low-priority**.
- `isPending` is a boolean indicating if the transition is ongoing.
- `startTransition` wraps updates that should be deferred.
- Prevents UI freezes by allowing urgent updates (like input changes) to happen first.

## When Not to Use `useTransition`
- For updates that **must happen immediately** (e.g., form submissions, API requests).
- When dealing with critical UI elements where delay is not acceptable.

## React Version
`useTransition` was introduced in **React 18**. Ensure your project is running React 18+ to use this hook.

## References
- [React Docs: useTransition](https://react.dev/reference/react/useTransition)
