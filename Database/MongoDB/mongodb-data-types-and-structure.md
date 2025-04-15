# MongoDB Data Types & Document Structure

MongoDB stores data as **BSON** (Binary JSON) documents — flexible, schema-less structures that are similar to JSON. Understanding data types and how documents are structured is key to effectively modeling and querying your data.

---

## MongoDB Document Structure

A **document** in MongoDB is a key-value pair object. It's similar to a JSON object.

```json
{
  "_id": ObjectId("507f191e810c19729de860ea"),
  "name": "Divyanshi",
  "age": 23,
  "isActive": true,
  "skills": ["React", "Node.js"],
  "address": {
    "city": "Delhi",
    "pincode": 110001
  },
  "joinedAt": ISODate("2024-01-01T10:00:00Z")
}
```
## Common MongoDB Data Types

| Type | Example |	Description |
| ---- | -------- | ----------- |
| String | "Divyanshi" |	Text data |
| Number	| 25 |	Integer or floating point |
| Boolean |	true |	true or false values |
| Array	| ["React", "MongoDB"]	| List of values |
| Object |	{ city: "Delhi", zip: 123456 } | Embedded document |
| Null | null |	Represents a missing value |
| Date	| ISODate("2024-01-01") |	Date & time |
| ObjectId	| ObjectId("507f191e...") |	Unique ID assigned by MongoDB |
| Binary |	BinData(0,"...")	| Binary data (e.g., images, files) |

## Special Fields
_id
- A unique identifier automatically generated for each document.
- You can also set it manually.

ObjectId
- 12-byte unique identifier:
- 4-byte timestamp
- 5-byte random value
- 3-byte increment counter

### Document Characteristics
- Dynamic schema: You don’t need to define all fields in advance.
- Nested structures: Documents can contain embedded documents and arrays.
- Flexible data types: Different documents in the same collection can have different fields.

## Best Practices
- Use consistent field names and types across documents.
- Use nested objects for logically grouped data (e.g., address, profile).
- Avoid deeply nested documents beyond 2–3 levels for better performance.
- Keep document size under 16MB (MongoDB’s limit per document).

## Summary
- MongoDB documents are flexible and support a wide range of data types.
- Understanding these types helps in creating efficient schemas and queries.
- The schema-less nature of MongoDB enables rapid and scalable application development.

