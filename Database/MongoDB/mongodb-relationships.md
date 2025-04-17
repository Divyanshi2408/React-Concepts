# MongoDB Relationships

In MongoDB, relationships between documents can be modeled using **References (Normalization)** or **Embedded Documents (Denormalization)**. Understanding these approaches helps you design scalable and efficient schemas.

---

## 1. Embedded Documents (Denormalization)

When related data is stored **within** the same document.

### Use When:
- Data is tightly coupled
- Fast read performance is important
- Subdocument size is manageable

### Example:

```js
const blogPostSchema = new mongoose.Schema({
  title: String,
  content: String,
  comments: [
    {
      user: String,
      text: String,
      createdAt: { type: Date, default: Date.now }
    }
  ]
});
```
Here, comments are embedded inside the blog post.

## 2. Referenced Documents (Normalization)
When documents are stored in separate collections and linked using ObjectId.

### Use When:
- Data is large and reused across documents
- Avoid duplication
- Maintain consistency

### Example:
```
const userSchema = new mongoose.Schema({
  name: String
});

const postSchema = new mongoose.Schema({
  title: String,
  content: String,
  author: { type: mongoose.Schema.Types.ObjectId, ref: "User" }
});
```
The author field references the User document using ObjectId.

### Populating References
Use Mongoose’s .populate() method to fetch referenced data.

```
Post.find()
  .populate("author")
  .then(posts => console.log(posts));
```
This replaces the author ID with the full user document.

## Comparison Table

| Feature |	Embedded Documents |	Referenced Documents |
| --------- | ---------------- | --------------------- |
|  Performance |	Fast reads	| Slower reads (requires joins) |
| Data duplication |	Higher	| Lower |
| Flexibility	| Less (fixed structure) |	More (separate models) |
| Atomic operations |	Easy	| Complex |

## Best Practices
- Embed when data is always accessed together.
- Reference when data is reused or large.
- Avoid deeply nested structures for better performance.

## Summary
- MongoDB supports both embedded and referenced relationships.
- Choosing the right approach depends on use case, data access patterns, and scalability.
