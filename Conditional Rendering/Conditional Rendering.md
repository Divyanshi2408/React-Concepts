
# Conditional Rendering in React

## Overview
Conditional rendering in React allows you to render different components or elements based on certain conditions.

---

## Using `if` Statement
```jsx
function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  } else {
    return <h1>Please log in.</h1>;
  }
}
```

---

## Using Ternary Operator
```jsx
function Greeting({ isLoggedIn }) {
  return isLoggedIn ? <h1>Welcome back!</h1> : <h1>Please log in.</h1>;
}
```

---

## Using Logical `&&` Operator
```jsx
function Notification({ hasNewMessages }) {
  return (
    <div>
      <h1>Dashboard</h1>
      {hasNewMessages && <p>You have new messages!</p>}
    </div>
  );
}
```

---

## Conditional Rendering with Components
```jsx
function AdminPanel() {
  return <h1>Admin Panel</h1>;
}

function UserPanel() {
  return <h1>User Panel</h1>;
}

function Dashboard({ isAdmin }) {
  return isAdmin ? <AdminPanel /> : <UserPanel />;
}
```

---

## Key Points
✅ Prop drilling occurs when data is passed through multiple nested components.
✅ Conditional rendering allows displaying different components or content based on state or props.
✅ Use Context or Redux to avoid prop drilling.

---

## References
- [React Docs - Conditional Rendering](https://react.dev/learn/conditional-rendering)
