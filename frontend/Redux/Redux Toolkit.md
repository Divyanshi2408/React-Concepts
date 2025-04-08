# Redux Toolkit

## Overview
- Redux Toolkit is the official, opinionated, and powerful toolset for efficient Redux development. It simplifies common Redux tasks and provides utilities to improve developer experience.

- Redux Toolkit is a library that helps you write Redux logic faster, easier, and with less code.
It was introduced by the Redux team to solve the problem of boilerplate and complex setup in traditional Redux.

---

`Redux Toolkit (RTK) simplifies Redux by reducing boilerplate code. It provides utilities like:`
- **configureStore()** → Simplifies store setup
- **createSlice()** → Combines actions & reducers
- **createAsyncThunk()** → Handles async operations

---

## Installation
To install Redux Toolkit and React-Redux:
```sh
npm install @reduxjs/toolkit react-redux
```

---

## Basic Redux Toolkit Setup
### 1. Create Redux Store
Define a store using `configureStore` from Redux Toolkit.

#### `store.js`
```jsx
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './counterSlice';

const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});

export default store;
```

---

### 2. Create a Slice
A slice contains the reducer logic and actions.

#### `counterSlice.js`
```jsx
import { createSlice } from '@reduxjs/toolkit';

const initialState = {
  value: 0,
};

const counterSlice = createSlice({
  name: 'counter',
  initialState,
  reducers: {
    increment: (state) => {
      state.value += 1;
    },
    decrement: (state) => {
      state.value -= 1;
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload;
    },
  },
});

export const { increment, decrement, incrementByAmount } = counterSlice.actions;
export default counterSlice.reducer;
```

---

### 3. Provide Store to Application
Use `Provider` to wrap the app and provide the store.

#### `index.js`
```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import { Provider } from 'react-redux';
import store from './store';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
```

---

### 4. Using Redux Toolkit State in Components
Use `useSelector` to access state and `useDispatch` to dispatch actions.

#### `App.js`
```jsx
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement, incrementByAmount } from './counterSlice';

function App() {
  const count = useSelector((state) => state.counter.value);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>Counter: {count}</h1>
      <button onClick={() => dispatch(increment())}>Increment</button>
      <button onClick={() => dispatch(decrement())}>Decrement</button>
      <button onClick={() => dispatch(incrementByAmount(5))}>Increment by 5</button>
    </div>
  );
}

export default App;
```

---

## Async Redux with Thunk
To handle asynchronous actions, use `createAsyncThunk`.

#### `userSlice.js`
```jsx
import { createSlice, createAsyncThunk } from '@reduxjs/toolkit';

export const fetchUsers = createAsyncThunk('users/fetchUsers', async () => {
  const response = await fetch('https://jsonplaceholder.typicode.com/users');
  return response.json();
});

const userSlice = createSlice({
  name: 'users',
  initialState: { users: [], loading: false, error: null },
  extraReducers: (builder) => {
    builder
      .addCase(fetchUsers.pending, (state) => {
        state.loading = true;
      })
      .addCase(fetchUsers.fulfilled, (state, action) => {
        state.loading = false;
        state.users = action.payload;
      })
      .addCase(fetchUsers.rejected, (state, action) => {
        state.loading = false;
        state.error = action.error.message;
      });
  },
});

export default userSlice.reducer;
```

---

## Key Points
✅ Redux Toolkit simplifies Redux setup.
✅ Use `createSlice` to define reducers and actions.
✅ Use `useSelector` and `useDispatch` for accessing and modifying state.
✅ Handle async operations with `createAsyncThunk`.

---

## References
- [Redux Toolkit Docs](https://redux-toolkit.js.org/)
- [React Redux Docs](https://react-redux.js.org/)
