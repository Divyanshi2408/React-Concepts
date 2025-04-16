# Mongoose Middleware (Hooks)

Mongoose **middleware** (also called **hooks**) are functions that are passed control during execution of asynchronous functions like `save()`, `find()`, `remove()`, etc. They are great for adding logic before or after an action on a document.

---

## Types of Middleware

### 1. **Document Middleware**
Triggered on individual document actions like `.save()`, `.remove()`.

- `pre('save')`
- `post('save')`
- `pre('remove')`
- `post('remove')`

### 2. **Query Middleware**
Triggered on query methods like `.find()`, `.findOne()`, `.updateOne()`, etc.

- `pre('find')`
- `post('find')`
- `pre('findOne')`
- `post('findOne')`

---

## Syntax

```js
schema.pre('action', function (next) {
  // do something before action
  next();
});

schema.post('action', function (doc) {
  // do something after action
});
```
### Example: Using pre and post Hooks
```
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  name: String,
  email: String
});

// Pre-save hook
userSchema.pre("save", function (next) {
  console.log("Before saving:", this.name);
  next();
});

// Post-save hook
userSchema.post("save", function (doc) {
  console.log("After saving:", doc.name);
});

const User = mongoose.model("User", userSchema);
```

### Example: Query Middleware
```
userSchema.pre("find", function (next) {
  console.log("Running before find query...");
  this.startTime = Date.now();
  next();
});

userSchema.post("find", function (docs) {
  console.log(`Query took ${Date.now() - this.startTime}ms`);
});
```

## Notes
- Always call next() in pre middleware to continue execution.
- Use middleware for logging, validation, data manipulation, timestamps, etc.
- Avoid heavy logic in middleware to keep performance smooth.

## Common Use Cases

| Use Case	| Hook Type |
| -------- | ----------- |
| Hashing password |	pre('save') |
| Timestamping updates |	pre('save') or pre('update') |
| Logging query time |	pre('find'), post('find') |
| Auto-populating refs |	pre('find') |
