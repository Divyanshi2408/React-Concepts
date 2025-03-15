# React Dynamic Routes

## Overview
Dynamic routing in React Router allows rendering components based on **URL parameters**. This is useful for displaying user profiles, product details, or other pages with variable data.

---

## Prerequisites
Make sure **React Router DOM** is installed:
```sh
npm install react-router-dom
```

---

## Defining Dynamic Routes
Use the `:param` syntax in route paths to capture dynamic segments.

### Example: User Profile Route
```jsx
import { Routes, Route } from "react-router-dom";
import Home from "./pages/Home";
import UserProfile from "./pages/UserProfile";

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/user/:id" element={<UserProfile />} />
    </Routes>
  );
}

export default App;
```

---

## Accessing Route Parameters with `useParams`
Use the `useParams` hook to extract values from the URL.

### `UserProfile.js`
```jsx
import { useParams } from "react-router-dom";

function UserProfile() {
  const { id } = useParams();

  return (
    <div>
      <h1>User Profile</h1>
      <p>User ID: {id}</p>
    </div>
  );
}

export default UserProfile;
```

---

## Navigation to Dynamic Routes
Use `Link` to navigate to dynamic paths.

### Example: Users List with Links
```jsx
import { Link } from "react-router-dom";

const users = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" },
];

function UserList() {
  return (
    <div>
      <h1>User List</h1>
      <ul>
        {users.map((user) => (
          <li key={user.id}>
            <Link to={`/user/${user.id}`}>{user.name}</Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default UserList;
```

---

## Fetching Data Based on Route Params
You can fetch data dynamically using the route parameter.

### Example: Fetch User Data
```jsx
import { useParams } from "react-router-dom";
import { useEffect, useState } from "react";

function UserProfile() {
  const { id } = useParams();
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetch(`https://jsonplaceholder.typicode.com/users/${id}`)
      .then((response) => response.json())
      .then((data) => setUser(data));
  }, [id]);

  if (!user) return <p>Loading...</p>;

  return (
    <div>
      <h1>{user.name}</h1>
      <p>Email: {user.email}</p>
    </div>
  );
}

export default UserProfile;
```

---

## Nested Dynamic Routes
You can define **nested routes** inside parent components.

### Example: Nested Routes in a Dashboard
```jsx
import { Routes, Route } from "react-router-dom";
import Dashboard from "./Dashboard";
import Profile from "./Profile";
import Settings from "./Settings";

function App() {
  return (
    <Routes>
      <Route path="dashboard" element={<Dashboard />}>
        <Route path="profile" element={<Profile />} />
        <Route path="settings" element={<Settings />} />
      </Route>
    </Routes>
  );
}
```

---

## Key Points
✅ Use `useParams()` to access dynamic route parameters.
✅ Use `Link` for navigation with dynamic values.
✅ Fetch data based on the URL parameter.
✅ Implement nested dynamic routes for structured navigation.

---

## React Version
Dynamic routes are supported in **React 16+** and work best with **React Router v6+**.

---

## References
- [React Router Docs](https://reactrouter.com/en/main)
