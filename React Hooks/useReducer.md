# `useReducer` Hook in React  

## Introduction  
The `useReducer` hook is an alternative to `useState` for managing complex state logic in React functional components. It is particularly useful when state transitions involve multiple sub-values or when the next state depends on the previous state.  

## Why `useReducer`?  
- Better suited for complex state logic compared to `useState`.  
- Provides a more structured approach to state management.  
- Helps manage state updates efficiently, reducing unnecessary re-renders.  
- Makes state logic more predictable using reducers and actions.  

---

## Syntax  
```javascript
const [state, dispatch] = useReducer(reducer, initialState);
```

## Parameters  
- **`reducer`**: A function that determines how state updates based on dispatched actions.  
- **`initialState`**: The starting value of the state.  

## Returns  
- **`state`**: The current state value.  
- **`dispatch`**: A function to send actions to the reducer.  

---

## How `useReducer` Works  

### Step 1: Define the Reducer Function  
The reducer function takes the current state and an action, then returns the new state.  

```javascript
const reducer = (state, action) => {
  switch (action.type) {
    case "INCREMENT":
      return { count: state.count + 1 };
    case "DECREMENT":
      return { count: state.count - 1 };
    case "RESET":
      return { count: 0 };
    default:
      return state;
  }
};
