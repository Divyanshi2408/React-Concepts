# Prop Drilling in React

## Overview
Prop drilling is the process of passing data from a parent component to deeply nested child components through props.

---

## Problem
When multiple components need access to the same data, prop drilling becomes cumbersome and difficult to maintain.

---

## Example of Prop Drilling

#### `App.js`
```jsx
import React, { useState } from 'react';
import Parent from './Parent';

function App() {
  const [message, setMessage] = useState('Hello from App!');

  return (
    <div>
      <h1>Prop Drilling Example</h1>
      <Parent message={message} />
    </div>
  );
}

export default App;
```

#### `Parent.js`
```jsx
import React from 'react';
import Child from './Child';

function Parent({ message }) {
  return (
    <div>
      <h2>Parent Component</h2>
      <Child message={message} />
    </div>
  );
}

export default Parent;
```

#### `Child.js`
```jsx
import React from 'react';

function Child({ message }) {
  return (
    <div>
      <h3>Child Component</h3>
      <p>{message}</p>
    </div>
  );
}

export default Child;
```

---

## Solution
To avoid prop drilling, consider using:
- Context API
- Redux or Redux Toolkit
