# Schema & Model in Depth (Mongoose)

Mongoose provides a powerful way to structure and manage data in MongoDB using **Schemas** and **Models**. Understanding how these work is crucial to building robust applications.

---

## What is a Schema?

A **Schema** defines the structure of the documents within a MongoDB collection. It includes:
- Field names
- Data types
- Default values
- Validation rules
- Timestamps and more

### Example:

```js
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  name: { type: String, required: true },
  email: { type: String, required: true, unique: true },
  age: { type: Number, min: 0 },
  isActive: { type: Boolean, default: true },
  createdAt: { type: Date, default: Date.now }
});
```
### What is a Model?
- A Model is a wrapper for the schema and provides an interface to interact with the database collection. It allows:
- Creating and saving documents
- Querying the database
- Updating and deleting documents

### Creating a Model:
```
const User = mongoose.model("User", userSchema);
```

### Mongoose Schema Options

| Option |	Description |
| ------- | ----------- |
| type	| Specifies the data type (String, Number, etc.) |
| required	| Makes the field mandatory |
| default |	Sets a default value |
| unique |	Ensures unique values (not a validator) |
| enum |	Accepts only specified values |
| min / max	| For number and date validation |
| match	| Regex pattern matching for strings |

### Example with Validations
```
const productSchema = new mongoose.Schema({
  name: {
    type: String,
    required: [true, "Product name is required"],
    trim: true
  },
  price: {
    type: Number,
    required: true,
    min: [0, "Price must be positive"]
  },
  category: {
    type: String,
    enum: ["Electronics", "Clothing", "Food"]
  },
  inStock: {
    type: Boolean,
    default: true
  }
});
```

## Summary
- Schema: Blueprint of a document in MongoDB.
- Model: Represents the collection and provides methods to interact with it.
- Schema helps validate and structure data before it gets stored in the database.
