# Connecting MongoDB with Node.js using Mongoose

[Mongoose](https://mongoosejs.com/) is an Object Data Modeling (ODM) library for MongoDB and Node.js. It provides a schema-based solution to model your data, adds structure, and simplifies interactions with MongoDB.

---

## Installation

```bash
npm install mongoose
```

## Basic Setup
Create a new file, e.g., db.js or database.js.

```
const mongoose = require("mongoose");

const connectDB = async () => {
  try {
    await mongoose.connect("mongodb://localhost:27017/myDatabase", {
      useNewUrlParser: true,
      useUnifiedTopology: true,
    });
    console.log("MongoDB Connected");
  } catch (error) {
    console.error("Connection failed:", error.message);
    process.exit(1);
  }
};

module.exports = connectDB;
```
Now, import and run it in your main file (app.js or index.js):

```
const express = require("express");
const connectDB = require("./db");

const app = express();
connectDB();

app.listen(3000, () => {
  console.log("Server is running on port 3000");
});
```

### Define a Mongoose Schema and Model
```
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  name: {
    type: String,
    required: true,
  },
  email: {
    type: String,
    required: true,
    unique: true,
  },
  age: Number,
  createdAt: {
    type: Date,
    default: Date.now,
  },
});

const User = mongoose.model("User", userSchema);
module.exports = User;
```

### CRUD Example
```
const User = require("./models/User");

// Create
const createUser = async () => {
  const user = new User({
    name: "Divyanshi",
    email: "divyanshi@example.com",
    age: 23,
  });
  await user.save();
};

// Read
const getUsers = async () => {
  const users = await User.find();
  console.log(users);
};

// Update
const updateUser = async (id) => {
  await User.findByIdAndUpdate(id, { age: 25 });
};

// Delete
const deleteUser = async (id) => {
  await User.findByIdAndDelete(id);
};
```

## Best Practices
- Keep database URI in environment variables (.env file).
- Use separate folders for models and database config.
- Use Mongoose validation to enforce schema rules.

## Summary
- Mongoose helps structure and manage MongoDB operations in Node.js.
- Define schemas to enforce consistency.
- Use models for CRUD operations.

