# Redux

## Overview
Redux is a state management library for JavaScript applications, commonly used with React but also compatible with Angular, Vue, and other frameworks. It helps manage the application state in a predictable way using a single source of truth (a centralized store).

---
### Core Principles of Redux 

**Single Source of Truth:** The entire state of your application is stored in a single object tree within the Redux store, making it easy to track and manage the application's data. 

**State is Read-only:** The state within the Redux store should never be directly modified. Instead, the only way to update the state is to dispatch an action, which describes what happened, and then the reducers, pure functions, handle the state transformation. 

**Changes are Made with Pure Functions:** To specify how the state tree is transformed by actions, you write pure functions called reducers. These reducers take the previous state and an action, and return the next state, ensuring predictable and manageable state updates.

---
### Key Concepts of Redux

**Store:** Holds the application's state.

**Actions:** Objects that describe state changes(what happend) ( { type: "INCREMENT" }) tiny bit of information that is required to mention what has happened .          

**Reducers:**	Pure functions that determine state changes based on actions.

**Dispatch:**	Sends actions to the store to update the state.

**Selectors:**	Functions that retrieve specific data from the store.

---
## Installation
To install Redux and React-Redux:
```sh
npm install redux react-redux
```

---

## Basic Redux Setup
### 1. Create Redux Store
Define a store using `createStore` from Redux.

#### `store.js`
```jsx
import { createStore } from 'redux';
import rootReducer from './reducers';

const store = createStore(rootReducer);

export default store;
```

---

### 2. Create Reducer
A reducer specifies how the state changes in response to an action.

#### `counterReducer.js`
```jsx
const initialState = {
  value: 0,
};

const counterReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { ...state, value: state.value + 1 };
    case 'DECREMENT':
      return { ...state, value: state.value - 1 };
    case 'INCREMENT_BY_AMOUNT':
      return { ...state, value: state.value + action.payload };
    default:
      return state;
  }
};

export default counterReducer;
```

---

### 3. Combine Reducers
Combine multiple reducers if needed.

#### `reducers/index.js`
```jsx
import { combineReducers } from 'redux';
import counterReducer from './counterReducer';

const rootReducer = combineReducers({
  counter: counterReducer,
});

export default rootReducer;
```

---

### 4. Provide Store to Application
Use `Provider` to wrap the app and provide the store.

#### `index.js`
```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import store from './store';
import App from './App';

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```

---

### 5. Using Redux State in Components
Use `connect` to access state and dispatch actions.

#### `App.js`
```jsx
import React from 'react';
import { connect } from 'react-redux';

function App({ count, increment, decrement, incrementByAmount }) {
  return (
    <div>
      <h1>Counter: {count}</h1>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
      <button onClick={() => incrementByAmount(5)}>Increment by 5</button>
    </div>
  );
}

const mapStateToProps = (state) => ({
  count: state.counter.value,
});

const mapDispatchToProps = (dispatch) => ({
  increment: () => dispatch({ type: 'INCREMENT' }),
  decrement: () => dispatch({ type: 'DECREMENT' }),
  incrementByAmount: (amount) => dispatch({ type: 'INCREMENT_BY_AMOUNT', payload: amount }),
});

export default connect(mapStateToProps, mapDispatchToProps)(App);
```

---

## Key Points
✅ Redux manages global state in React apps.
✅ Use `createStore` to create a store.
✅ Reducers define how state changes based on actions.
✅ `connect` connects Redux state and actions to components.

---

## References
- [Redux Docs](https://redux.js.org/)
- [React Redux Docs](https://react-redux.js.org/)
