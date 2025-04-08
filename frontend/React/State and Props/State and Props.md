# State and Props in React

A deep dive into state and props, their roles, and best practices.

## State and Props in React – What’s the difference and when to use them?

In React, **state** and **props** are two of the most essential concepts when it comes to building interactive UIs.

### **State**
State refers to data or properties that are managed within a component. It can be changed during the component's lifecycle, and when the state changes, the component re-renders to reflect those changes.

#### **Key Features of State:**
- Managed inside the component (using `useState` in functional components or `this.state` in class components).
- Can be updated dynamically.
- Typically used for data that changes over time, such as user input, form data, or fetched API data.

#### **Example of State in a Functional Component:**
```javascript
import React, { useState } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};

export default Counter;
```
### **Props**
Props (short for properties) are the data passed from a parent component to a child component. They are immutable, meaning they cannot be changed by the child component. Props are used to configure a component or pass dynamic data to it.

#### **Key Features of Props:**
- Passed down from a parent component.
- Immutable within the child component.
- Useful for passing data or event handlers to child components.

#### **Example of State in a Functional Component:**
```javascript
import React from 'react';

const Child = ({ message }) => {
  return <h1>{message}</h1>;
};

const Parent = () => {
  return <Child message="Hello from the parent!" />;
};

export default Parent;

```
### State vs Props:

| Feature           | State                                  | Props                                 |
|-------------------|----------------------------------------|---------------------------------------|
| **Mutability**    | Mutable (can change over time)         | Immutable (cannot be changed by child)|
| **Management**    | Managed inside the component           | Passed down from parent to child      |
| **Purpose**       | Used for dynamic, internal data        | Used for passing data between components |

### Best Practices:

- **Use state** for data that changes over time and affects the component’s behavior.
- **Use props** for data that needs to be passed down from a parent component to a child component.
- Never **mutate props** directly; always pass them down as immutable values.
- Keep state as **local as possible**; lift state up when multiple components need to share it.
