# Node.js Modules

Modules in Node.js help you organize your code into **separate files and reusable components**. Each file in Node.js is treated as a **module**.

---

## Types of Modules

| Type | Description |
|------|-------------|
| **Core Modules** | Built-in Node.js modules like `fs`, `path`, `http` |
| **Local Modules** | Custom modules you create in your app |
| **Third-party Modules** | Installed via `npm`, e.g., `express`, `mongoose` |

---

## 1 Core Modules

Node.js comes with many useful built-in modules. No need to install them.

### Example: Using `fs` to read a file

```js
const fs = require('fs');

fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) return console.error(err);
  console.log(data);
});
```
**Other Core Modules:**

- path – Handle file paths
- http – Build HTTP servers
- os – System info
- events – Event-driven programming
- url – URL parsing and formatting

## 2 Local Modules (Custom)
You can define and export your own functions or variables.

Example:
math.js
```
function add(a, b) {
  return a + b;
}

module.exports = { add };
```
app.js
```
const math = require('./math');
console.log(math.add(2, 3)); // Output: 5
```
📌 Always use ./ to require local files.

## 3 Third-party Modules (npm)
You can install and use modules created by others via npm.

Example: Using lodash
```
// npm install lodash

const _ = require('lodash');

let arr = [1, 2, 2, 3];
console.log(_.uniq(arr)); // Output: [1, 2, 3]
```
🔄 Exporting & Importing in Node.js
Exporting (in math.js)
```
module.exports = {
  add,
  subtract
};
```
Importing (in app.js)
```
const { add, subtract } = require('./math');
```

🔍 Checking Built-in Modules
You can explore the list of core modules in the official docs:
🔗 https://nodejs.org/api/

