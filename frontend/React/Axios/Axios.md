# React Axios

## Overview
Axios is a popular HTTP client for making API requests in React. It supports features like request/response interception, automatic JSON data transformation, and error handling.

---

## Installation
To install Axios, run:
```sh
npm install axios
```

---

## Basic GET Request
Perform a simple GET request using `axios.get()`.

### Example: Fetching Data from an API
```jsx
import React, { useEffect, useState } from "react";
import axios from "axios";

function App() {
  const [data, setData] = useState([]);

  useEffect(() => {
    axios.get("https://jsonplaceholder.typicode.com/posts")
      .then(response => setData(response.data))
      .catch(error => console.error("Error fetching data:", error));
  }, []);

  return (
    <div>
      <h1>Posts</h1>
      <ul>
        {data.map(post => (
          <li key={post.id}>{post.title}</li>
        ))}
      </ul>
    </div>
  );
}

export default App;
```

---

## POST Request
Send data using `axios.post()`.

### Example: Sending Data to API
```jsx
import React, { useState } from "react";
import axios from "axios";

function App() {
  const [title, setTitle] = useState("");

  const handleSubmit = async (e) => {
    e.preventDefault();
    try {
      const response = await axios.post("https://jsonplaceholder.typicode.com/posts", {
        title,
        body: "Sample body content",
        userId: 1,
      });
      console.log("Post created:", response.data);
    } catch (error) {
      console.error("Error posting data:", error);
    }
  };

  return (
    <div>
      <h1>Create Post</h1>
      <form onSubmit={handleSubmit}>
        <input
          type="text"
          value={title}
          onChange={(e) => setTitle(e.target.value)}
          placeholder="Enter title"
        />
        <button type="submit">Submit</button>
      </form>
    </div>
  );
}

export default App;
```

---

## PUT and DELETE Requests
Use `axios.put()` to update data and `axios.delete()` to remove data.

### PUT Example (Update Data)
```jsx
axios.put("https://jsonplaceholder.typicode.com/posts/1", {
  title: "Updated Title",
  body: "Updated Content",
})
.then(response => console.log("Updated:", response.data))
.catch(error => console.error("Error updating data:", error));
```

### DELETE Example (Remove Data)
```jsx
axios.delete("https://jsonplaceholder.typicode.com/posts/1")
  .then(response => console.log("Deleted successfully"))
  .catch(error => console.error("Error deleting data:", error));
```

---

## Using Axios with `async/await`
Axios can be used with `async/await` for cleaner syntax.

### Example: Fetching Data with `async/await`
```jsx
import { useState, useEffect } from "react";
import axios from "axios";

function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await axios.get("https://jsonplaceholder.typicode.com/users");
        setUsers(response.data);
      } catch (error) {
        console.error("Error fetching users:", error);
      }
    };
    fetchData();
  }, []);

  return (
    <div>
      <h1>User List</h1>
      <ul>
        {users.map(user => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default App;
```

---

## Setting Global Axios Defaults
Set default headers, base URL, and other configurations.
```jsx
import axios from "axios";

axios.defaults.baseURL = "https://jsonplaceholder.typicode.com";
axios.defaults.headers.common["Authorization"] = "Bearer token";
axios.defaults.headers.post["Content-Type"] = "application/json";
```

---

## Handling Errors Globally
Use Axios interceptors to catch errors globally.
```jsx
axios.interceptors.response.use(
  response => response,
  error => {
    console.error("API Error:", error.response || error.message);
    return Promise.reject(error);
  }
);
```

---

## Key Points
✅ Axios simplifies API requests in React.
✅ Supports GET, POST, PUT, and DELETE operations.
✅ Works with `async/await` for better readability.
✅ Allows setting global defaults and interceptors.
✅ Provides better error handling and automatic JSON parsing.

---

## React Version
Axios works with **React 16+** and is optimized for **React 18+**.

---

## References
- [Axios Documentation](https://axios-http.com/docs/intro)
