# Asynchronous Programming in Node.js

Node.js is built to handle asynchronous operations efficiently. This non-blocking nature is what makes it ideal for high-performance web applications.

---

## 🧠 What is Asynchronous Programming?

It allows your code to **run without waiting** for previous operations (like reading files or fetching data) to complete. This improves performance, especially for I/O-heavy tasks.

---

## Synchronous vs Asynchronous

### Synchronous Example (Blocking)

```js
const fs = require('fs');

const data = fs.readFileSync('file.txt');
console.log(data.toString());
console.log('This runs after reading the file');
```
The second console.log runs only after the file is read.

### Asynchronous Example (Non-Blocking)
```
fs.readFile('file.txt', (err, data) => {
  if (err) throw err;
  console.log(data.toString());
});

console.log('This runs without waiting for the file read');
```
Both operations run concurrently.

### Callback Pattern
Node.js uses callback functions to handle async tasks.
```
setTimeout(() => {
  console.log('Executed after 2 seconds');
}, 2000);
```
### Callback Hell
When callbacks are nested too deeply, it becomes hard to read and maintain:
```
doTask1(() => {
  doTask2(() => {
    doTask3(() => {
      // and so on...
    });
  });
});
```
### Promises
A cleaner way to handle async logic.
```
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve('Data received'), 1000);
  });
};

fetchData()
  .then(data => console.log(data))
  .catch(err => console.error(err));
```
## async/await
Introduced in ES8, it's syntactic sugar over Promises and makes async code look synchronous.

```
const fetchData = () => {
  return new Promise(resolve => {
    setTimeout(() => resolve('Fetched!'), 1000);
  });
};

const getData = async () => {
  try {
    const data = await fetchData();
    console.log(data);
  } catch (err) {
    console.error(err);
  }
};

getData();
```
## Real-Life Use Cases
- Task	Async Nature
- File system operations	Yes
- Network requests	Yes
- Database queries	Yes
- Timers (setTimeout)	Yes
  
## Best Practices
- Prefer async/await over callbacks.
- Always wrap async code in try-catch.
- Avoid deeply nested callbacks (callback hell).
- Use utilities like Promise.all() for parallel execution.
