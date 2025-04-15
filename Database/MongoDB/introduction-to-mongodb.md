# Introduction to MongoDB

MongoDB is a **NoSQL, document-oriented database** that stores data in flexible, JSON-like documents. It’s a core part of the MERN stack and is widely used in modern web applications for handling data.

---

## Why MongoDB?

- Stores data in **BSON** (Binary JSON) format.
- Uses **collections** and **documents** instead of tables and rows.
- Schema-less structure offers **flexibility** and **scalability**.
- Easily deployable in the cloud via **MongoDB Atlas**.
- Works seamlessly with **Node.js** and **Express** using Mongoose.

---

## SQL vs NoSQL

| Feature             | SQL Databases       | MongoDB (NoSQL)       |
|---------------------|---------------------|------------------------|
| Data Format         | Tables & Rows       | Documents (JSON/BSON) |
| Schema              | Strict/Fixed        | Dynamic/Flexible      |
| Joins               | Supported           | Not native (use embedding/referencing) |
| Scalability         | Vertical            | Horizontal             |
| Ideal For           | Complex queries     | Fast & scalable apps   |

---

## Key Concepts

### Database
A container for collections.

### Collection
Similar to a table in SQL. Contains multiple documents.

### Document
The basic unit of data in MongoDB. It is a JSON-like object.
```json
{
  "name": "Divyanshi",
  "role": "Full Stack Developer"
}
```
## Use Cases
- Real-time analytics
- Content management systems (CMS)
- E-commerce apps
- IoT data platforms
- Scalable APIs

## Summary
- MongoDB is a NoSQL database used for high-performance, flexible, and scalable data storage.
- It’s an essential part of the MERN stack and works well with JavaScript/Node.js apps.
- Instead of rows and tables, it uses documents and collections.
