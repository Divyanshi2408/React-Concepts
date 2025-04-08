# React Modals and Portals

## Overview
Modals in React are UI components that overlay the main content to display additional information. React Portals allow rendering these modals (or other components) outside the main DOM hierarchy while maintaining their functionality.

### What is Modal?
A modal is a UI overlay component that appears above the current page content and blocks interaction with the background until it is dismissed.
In React, modals are often implemented using portals to avoid layout and z-index issues.

## What is a Portal?
A **React Portal** enables rendering a component **outside** its parent DOM node but keeping it within the React component tree.
- React Portals allow rendering a component into a different part of the DOM tree, outside the root element.
- It’s mainly used for UI elements like modals, tooltips, and popovers that need to appear above other content.

### Syntax
```jsx
ReactDOM.createPortal(child, container)
```
- **`child`**: The React component to render.
- **`container`**: The DOM node where the component should be rendered.

## Creating a Modal Using a Portal
### 1. Setting Up the Portal Container
Add a `div` in your HTML file where the modal will be rendered.
```html
<!-- index.html -->
<body>
  <div id="root"></div>
  <div id="modal-root"></div>
</body>
```

### 2. Creating the Modal Component
```jsx
import React from "react";
import ReactDOM from "react-dom";

function Modal({ isOpen, onClose, children }) {
  if (!isOpen) return null;

  return ReactDOM.createPortal(
    <div className="modal-overlay">
      <div className="modal-content">
        <button onClick={onClose} className="close-btn">Close</button>
        {children}
      </div>
    </div>,
    document.getElementById("modal-root")
  );
}

export default Modal;
```

### 3. Using the Modal Component
```jsx
import React, { useState } from "react";
import Modal from "./Modal";

function App() {
  const [isModalOpen, setModalOpen] = useState(false);

  return (
    <div>
      <h1>React Modal with Portal</h1>
      <button onClick={() => setModalOpen(true)}>Open Modal</button>
      <Modal isOpen={isModalOpen} onClose={() => setModalOpen(false)}>
        <p>This is a modal content.</p>
      </Modal>
    </div>
  );
}

export default App;
```

## Styling the Modal (CSS)
```css
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal-content {
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.close-btn {
  background: red;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}
```

## Key Points
- **Modals should be rendered using portals** to avoid layout issues.
- **Portals keep event bubbling behavior**, meaning events propagate up the React tree as expected.
- **Useful for modals, tooltips, and popups** that need to overlay the UI.

## When to Use Portals
✅ Modals, dialogs, tooltips, and popups.
✅ Rendering elements outside the main DOM tree.
✅ Preventing CSS conflicts or `overflow: hidden` issues.

## React Version
React Portals were introduced in **React 16+**.

## References
- [React Docs: Portals](https://react.dev/reference/react-dom/createPortal)
