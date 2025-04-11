# Working with JSON in Node.js

JSON (JavaScript Object Notation) is a lightweight data format used for storing and exchanging data. It's widely used in web development for sending and receiving data from APIs.

---

## What is JSON?

JSON is a **text format** that is easy to read and write. It represents **key-value** pairs and supports nested structures.

```json
{
  "name": "Divyanshi",
  "age": 22,
  "skills": ["JavaScript", "React", "Node.js"]
}
```
### Parsing JSON
Converting a JSON string to a JavaScript object:
```
const jsonString = '{"name": "Divyanshi", "age": 22}';
const user = JSON.parse(jsonString);

console.log(user.name); // Output: Divyanshi
```
### Stringifying JSON
Converting a JavaScript object to a JSON string:
```
const user = { name: 'Divyanshi', age: 22 };
const jsonString = JSON.stringify(user);

console.log(jsonString); // Output: {"name":"Divyanshi","age":22}
```
### Reading & Writing JSON Files
You can work with JSON files using the built-in fs module.

### Read a JSON File
```
const fs = require('fs');

fs.readFile('data.json', 'utf8', (err, data) => {
  if (err) throw err;
  const obj = JSON.parse(data);
  console.log(obj);
});
```
### Write to a JSON File
```
const fs = require('fs');

const newData = {
  name: 'React Guide',
  topics: ['JSX', 'Hooks', 'State']
};

fs.writeFile('data.json', JSON.stringify(newData, null, 2), err => {
  if (err) throw err;
  console.log('Data written to file');
});
```
null, 2 adds indentation for better readability.

### Error Handling
Wrap JSON.parse() in try-catch to avoid crashes on invalid JSON:
```
try {
  const data = JSON.parse('invalid json');
} catch (err) {
  console.error('Invalid JSON:', err.message);
}
```
### Use Cases of JSON in Node.js
- Use Case	Example
- Config files	config.json
- API responses	res.json({ message: "OK" })
- Storing temporary app data	In .json files
- Reading package info	require('./package.json')
