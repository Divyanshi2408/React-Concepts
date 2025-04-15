# CRUD Operations using Mongoose

Mongoose simplifies CRUD (Create, Read, Update, Delete) operations in MongoDB with a clean and structured syntax. Below are examples of how to perform CRUD using Mongoose.

---

## Prerequisites

- MongoDB running locally or on the cloud
- Connected using Mongoose
- A defined model (e.g., `User`)

---

## Sample User Schema

```js
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  name: { type: String, required: true },
  email: { type: String, required: true, unique: true },
  age: Number,
  createdAt: { type: Date, default: Date.now }
});

const User = mongoose.model("User", userSchema);
module.exports = User;
```
## Create
```
const createUser = async () => {
  const user = new User({
    name: "Divyanshi",
    email: "divyanshi@example.com",
    age: 23
  });

  await user.save();
  console.log("User Created:", user);
};
```
## Read
### Find All Users
```
const getUsers = async () => {
  const users = await User.find();
  console.log("All Users:", users);
};
```
### Find One User by ID
```
const getUserById = async (id) => {
  const user = await User.findById(id);
  console.log("User:", user);
};
```

### Find by Field (e.g., email)
```
const getUserByEmail = async (email) => {
  const user = await User.findOne({ email });
  console.log("User:", user);
};
```

## Update
Update by ID
```
const updateUser = async (id) => {
  const updatedUser = await User.findByIdAndUpdate(
    id,
    { age: 24 },
    { new: true }
  );
  console.log("Updated User:", updatedUser);
};
```

## Delete
Delete by ID
```
const deleteUser = async (id) => {
  await User.findByIdAndDelete(id);
  console.log("User Deleted");
};
```
## Notes
- Use new: true in findByIdAndUpdate() to return the updated document.
- Always wrap async operations in try/catch blocks for better error handling.
- Use validation and error messages in your schema for robust models.

## Summary

| Operation	 | Mongoose Method |
| ---------- | --------------- |
| Create	 | Model.create() or new Model().save() |
| Read	| Model.find(), Model.findById(), Model.findOne() |
| Update |	Model.findByIdAndUpdate() |
| Delete	| Model.findByIdAndDelete() |
