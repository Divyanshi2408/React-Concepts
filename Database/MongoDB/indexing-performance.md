# Indexing & Performance in MongoDB

Indexes in MongoDB are crucial for **query performance optimization**. They allow the database to efficiently locate and retrieve documents without scanning the entire collection.

---

## What is an Index?

An **index** is a special data structure that stores a small portion of the collection's data in an easy-to-traverse form.

Similar to the index in a book — it helps MongoDB quickly find the data it needs.

---

## 🛠Creating an Index

```js
db.collection.createIndex({ fieldName: 1 }); // ascending order
db.collection.createIndex({ fieldName: -1 }); // descending order
```
### Example:
```
db.users.createIndex({ email: 1 });
```
Creates an index on the email field for fast lookup.

## Types of Indexes

| **Index Type**     | **Description**                                 |
|--------------------|-------------------------------------------------|
| **Single Field**   | Indexes a single field in a document            |
| **Compound**       | Indexes multiple fields in a defined order      |
| **Multikey**       | Indexes array values (each element individually)|
| **Text**           | Supports full-text search on string content     |
| **Hashed**         | Indexes hashed values, used mainly for sharding |
| **Geospatial**     | Supports queries on location-based (2D/2DSphere) data |

### Example: Compound Index
```
db.products.createIndex({ category: 1, price: -1 });
```
Index on both category and price fields.

### Analyzing Performance

Use .explain() to analyze query performance:

```
db.users.find({ email: "test@example.com" }).explain("executionStats");
```

### Best Practices
- Always index fields used in queries, sort, or join ($lookup) operations.
- Avoid over-indexing — each index takes extra storage and slows down writes.
- Use compound indexes for multi-field queries.
- Create sparse and partial indexes for filtering null or optional fields.

### Impact Without Indexing
- Full collection scan (COLLSCAN)
- Slow query performance
- Poor scalability for large datasets

## Summary

- Indexes are essential for high-performance queries.
- Use .explain() to diagnose slow operations.
- Choose the right index based on your access patterns.
