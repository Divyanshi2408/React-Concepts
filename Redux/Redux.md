# Redux

## Overview
Redux is a predictable state container for JavaScript applications. It helps manage the state of an application in a centralized store.

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
