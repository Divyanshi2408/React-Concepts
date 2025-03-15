# Event Handling and Forms in React

## Overview
React provides a **synthetic event system** to handle user interactions, such as clicks, input changes, and form submissions. Forms in React use **controlled components** to manage input state effectively.

---

## Event Handling in React
React normalizes events to ensure **cross-browser compatibility** and provides a consistent interface similar to native DOM events.

### Basic Event Handling
```jsx
import React from "react";

function EventExample() {
  const handleClick = () => {
    alert("Button Clicked!");
  };

  return <button onClick={handleClick}>Click Me</button>;
}

export default EventExample;
```

### Event Object (`event`)
React provides a **synthetic event object**, which works across all browsers.
```jsx
function EventObjectExample() {
  const handleClick = (event) => {
    console.log("Event Type:", event.type);
    console.log("Button Text:", event.target.textContent);
  };

  return <button onClick={handleClick}>Click Me</button>;
}
```

### Passing Arguments to Event Handlers
```jsx
function EventWithArgs() {
  const handleClick = (message) => {
    alert(message);
  };

  return <button onClick={() => handleClick("Hello, React!")}>Click Me</button>;
}
```

### Handling Keyboard Events
```jsx
function KeyPressExample() {
  const handleKeyPress = (event) => {
    if (event.key === "Enter") {
      alert("Enter Key Pressed!");
    }
  };

  return <input type="text" onKeyPress={handleKeyPress} placeholder="Press Enter" />;
}
```

---

## Forms in React
Forms in React use **controlled components**, meaning form elements are tied to component state.

### Controlled Components
```jsx
import React, { useState } from "react";

function ControlledForm() {
  const [inputValue, setInputValue] = useState("");

  const handleChange = (event) => {
    setInputValue(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert("Submitted: " + inputValue);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" value={inputValue} onChange={handleChange} />
      <button type="submit">Submit</button>
    </form>
  );
}

export default ControlledForm;
```

### Uncontrolled Components
Uncontrolled components use **ref** instead of state to access form values.
```jsx
import React, { useRef } from "react";

function UncontrolledForm() {
  const inputRef = useRef(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    alert("Submitted: " + inputRef.current.value);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={inputRef} />
      <button type="submit">Submit</button>
    </form>
  );
}

export default UncontrolledForm;
```

### Handling Multiple Inputs
```jsx
import React, { useState } from "react";

function MultiInputForm() {
  const [formData, setFormData] = useState({ name: "", email: "" });

  const handleChange = (event) => {
    const { name, value } = event.target;
    setFormData((prev) => ({ ...prev, [name]: value }));
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`Name: ${formData.name}, Email: ${formData.email}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" name="name" value={formData.name} onChange={handleChange} placeholder="Name" />
      <input type="email" name="email" value={formData.email} onChange={handleChange} placeholder="Email" />
      <button type="submit">Submit</button>
    </form>
  );
}

export default MultiInputForm;
```

---

## Key Points
- **Synthetic events** wrap native events for consistency.
- **Controlled components** use state for input values.
- **Uncontrolled components** rely on refs for direct DOM manipulation.
- **Use `event.preventDefault()`** to prevent form reload.

## React Version
Forms and event handling are available in all versions of React.

## References
- [React Docs: Handling Events](https://react.dev/learn/responding-to-events)
- [React Docs: Forms](https://react.dev/reference/react-dom/components/input)
