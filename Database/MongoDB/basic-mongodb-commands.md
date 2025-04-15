# Basic MongoDB Commands

This guide covers essential MongoDB shell commands used to interact with databases, collections, and documents.

---

## Start the Mongo Shell
```bash
mongo
```

## Database Commands

| Command	| Description |
| ------- | ------------ |
| show dbs |	Lists all databases |
| use dbName	| Switches to (or creates) a database |
| db |	Shows the current database name |
| db.dropDatabase() |	Deletes the current database |

## Collection Commands

| Command	| Description |
| ------- | ----------- |
| show collections |	Lists all collections in the current database |
| db.createCollection("name") |	Creates a new collection |
| db.collection.drop() |	Deletes a collection |

## Document Commands
### Insert Documents
```
db.users.insertOne({ name: "Divyanshi", role: "Developer" });
db.users.insertMany([
  { name: "Alice" },
  { name: "Bob" }
]);
```

### Read Documents
```
db.users.find();                  // All documents
db.users.find().pretty();         // Nicely formatted
db.users.findOne({ name: "Bob" }); // Find one document
```

### Update Documents
```
db.users.updateOne(
  { name: "Bob" },
  { $set: { role: "Admin" } }
);

db.users.updateMany(
  {},
  { $set: { active: true } }
);
```

### Delete Documents
```
db.users.deleteOne({ name: "Alice" });
db.users.deleteMany({ active: false });
```

### Query Operators

| Operator |	Usage |
| $gt |	Greater than |
| $lt	| Less than |
| $in	 | Matches any value in an array |
| $and, $or	| Logical conditions |

Example:
```
db.users.find({ age: { $gt: 25 } });
```

## Summary
- MongoDB commands are used to manage databases, collections, and documents.
- Common tasks include creating, reading, updating, and deleting data (CRUD).
- Practice these in the Mongo Shell or MongoDB Compass.

