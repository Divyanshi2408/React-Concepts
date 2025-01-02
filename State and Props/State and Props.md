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
