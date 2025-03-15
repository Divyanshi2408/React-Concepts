# React Router DOM

## Overview
React Router DOM is a library that enables navigation and routing in React applications. It provides dynamic routing, allowing users to switch between different views without reloading the page.

---

## Installation
To install React Router DOM, run:
```sh
npm install react-router-dom
```

For projects using React 18:
```sh
npm install react-router-dom@latest
```

---

## Basic Setup
To use React Router, wrap your application inside the `BrowserRouter` component.

### `index.js`
```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import { BrowserRouter } from "react-router-dom";
import App from "./App";

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

---

## Defining Routes
Use the `Routes` and `Route` components to define different pages.

### `App.js`
```jsx
import React from "react";
import { Routes, Route } from "react-router-dom";
import Home from "./pages/Home";
import About from "./pages/About";
import NotFound from "./pages/NotFound";

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
      <Route path="*" element={<NotFound />} />
    </Routes>
  );
}

export default App;
```

---

## Navigation with `Link` and `NavLink`
Instead of using `<a>` tags, use React Router’s `Link` or `NavLink` for navigation.

### Using `Link`
```jsx
import { Link } from "react-router-dom";

function Navbar() {
  return (
    <nav>
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>
    </nav>
  );
}
```

### Using `NavLink` (for active styling)
```jsx
import { NavLink } from "react-router-dom";

function Navbar() {
  return (
    <nav>
      <NavLink to="/" activeclassname="active">Home</NavLink>
      <NavLink to="/about" activeclassname="active">About</NavLink>
    </nav>
  );
}
```

---

## Programmatic Navigation with `useNavigate`
The `useNavigate` hook allows redirection in React components.
```jsx
import { useNavigate } from "react-router-dom";

function Home() {
  const navigate = useNavigate();

  return (
    <div>
      <h1>Home Page</h1>
      <button onClick={() => navigate("/about")}>Go to About</button>
    </div>
  );
}
```

---

## Dynamic Routing with URL Parameters
Use `useParams` to access dynamic route parameters.

### Define Dynamic Route
```jsx
<Route path="/user/:id" element={<User />} />
```

### Access URL Parameter
```jsx
import { useParams } from "react-router-dom";

function User() {
  const { id } = useParams();
  return <h2>User ID: {id}</h2>;
}
```

---

## Protected Routes (Authentication)
Use a wrapper component to protect routes.

### Creating a Protected Route Component
```jsx
import { Navigate } from "react-router-dom";

function ProtectedRoute({ isAuthenticated, children }) {
  return isAuthenticated ? children : <Navigate to="/login" />;
}
```

### Using Protected Route
```jsx
<Route path="/dashboard" element={<ProtectedRoute isAuthenticated={true}><Dashboard /></ProtectedRoute>} />
```

---

## Key Points
✅ React Router DOM enables client-side routing.
✅ Use `Routes` and `Route` to define navigation paths.
✅ Use `Link` and `NavLink` instead of `<a>` tags.
✅ Use `useNavigate` for programmatic navigation.
✅ Use `useParams` for dynamic routing.
✅ Protect routes using authentication logic.

---

## React Version
React Router DOM is supported in **React 16+** and is optimized for **React 18+**.

---

## References
- [React Router Docs](https://reactrouter.com/en/main)
