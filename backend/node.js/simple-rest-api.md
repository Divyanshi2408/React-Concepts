# Creating a Simple REST API using Node.js & Express

A **REST API** allows different systems to communicate over HTTP using standard HTTP methods like `GET`, `POST`, `PUT`, and `DELETE`.

---

## Requirements

- Node.js installed
- `npm` (Node Package Manager)
- Basic understanding of JavaScript

---

### Step 1: Initialize Project

```
mkdir rest-api
cd rest-api
npm init -y
```
### Step 2: Install Express
```
npm install express
```
### Step 3: Create index.js
```
const express = require('express');
const app = express();

app.use(express.json()); // Middleware to parse JSON

const PORT = 3000;
```

### // Sample data
```
let users = [
  { id: 1, name: 'Divyanshi' },
  { id: 2, name: 'John' }
];

// GET: Read all users
app.get('/api/users', (req, res) => {
  res.json(users);
});

// GET: Read a single user
app.get('/api/users/:id', (req, res) => {
  const user = users.find(u => u.id == req.params.id);
  if (!user) return res.status(404).send('User not found');
  res.json(user);
});

// POST: Create a new user
app.post('/api/users', (req, res) => {
  const newUser = {
    id: users.length + 1,
    name: req.body.name
  };
  users.push(newUser);
  res.status(201).json(newUser);
});

// PUT: Update a user
app.put('/api/users/:id', (req, res) => {
  const user = users.find(u => u.id == req.params.id);
  if (!user) return res.status(404).send('User not found');
  user.name = req.body.name;
  res.json(user);
});

// DELETE: Delete a user
app.delete('/api/users/:id', (req, res) => {
  users = users.filter(u => u.id != req.params.id);
  res.send('User deleted');
});

app.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}`);
});
```
### Step 4: Run the Server
Use nodemon for auto-reload:
```
nodemon index.js
```
### Test with Postman or VSCode REST Client
Method	Endpoint	Description
- GET	/api/users	Get all users
- GET	/api/users/:id	Get single user
- POST	/api/users	Create new user
- PUT	/api/users/:id	Update user name
- DELETE	/api/users/:id	Delete user
  
### Tips
- Use express.json() to parse incoming JSON.
- Always send a response or it will hang.
- Use tools like Postman or Thunder Client to test API endpoints.

