# Aggregation Framework in MongoDB

The **Aggregation Framework** in MongoDB is a powerful tool to process data and perform operations like filtering, grouping, sorting, and transforming documents in a collection.

---

## What is Aggregation?

Aggregation operations process multiple documents and return computed results. It's similar to SQL's `GROUP BY` and `JOIN` operations.

---

## Aggregation Pipeline

MongoDB uses a **pipeline** approach, where each stage transforms the data and passes it to the next stage.

### Basic Syntax

```js
db.collection.aggregate([
  { stage1 },
  { stage2 },
  ...
]);
```

## Common Aggregation Stages

| **Stage**    | **Description** |
|--------------|------------------|
| `$match`     | Filters documents (like `.find()`) based on specified criteria |
| `$group`     | Groups documents by a specified field and allows aggregation functions (sum, avg, etc.) |
| `$sort`      | Sorts the documents in ascending or descending order |
| `$project`   | Reshapes or includes/excludes specific fields in the output |
| `$limit`     | Limits the number of documents passed through the pipeline |
| `$skip`      | Skips the first N documents |
| `$lookup`    | Performs joins with another collection (similar to SQL joins) |
| `$unwind`    | Deconstructs arrays into multiple documents (one per array element) |

### Example: Group & Count
```
db.orders.aggregate([
  { $group: { _id: "$customerId", totalOrders: { $sum: 1 } } }
]);
```
Groups orders by customerId and counts the number of orders.

### Example: Filtering and Projecting
```
db.users.aggregate([
  { $match: { age: { $gte: 18 } } },
  { $project: { name: 1, age: 1, _id: 0 } }
]);
```
Returns only users aged 18+ with selected fields.

### Example: Joining Collections ($lookup)
```
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",
      localField: "customerId",
      foreignField: "_id",
      as: "customerDetails"
    }
  }
]);
```
Joins the orders collection with customers.

## Notes
- Aggregation is optimized for performance.
- Use indexes on fields used in $match, $group, and $sort.
- You can chain multiple stages to form complex queries.

### Use Cases
- Report generation
- Analytics dashboards
- Real-time data summaries
- Merging and transforming datasets
