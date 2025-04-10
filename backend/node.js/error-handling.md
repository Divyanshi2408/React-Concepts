# ❗ Error Handling in Node.js

Error handling is crucial to writing reliable and maintainable Node.js applications. It helps catch unexpected issues and ensures the app doesn't crash abruptly.

---

## 🔹 Types of Errors

| Type              | Description                                       |
|-------------------|---------------------------------------------------|
| **Synchronous**   | Occurs during execution of code (e.g., syntax errors) |
| **Asynchronous**  | Occurs inside callbacks, promises, or async/await |

---

## 🧪 Synchronous Error Example

```js
try {
  let data = fs.readFileSync('file.txt');
  console.log(data.toString());
} catch (err) {
  console.error('Error reading file:', err.message);
}
```
