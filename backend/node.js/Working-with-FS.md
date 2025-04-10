# Working with the File System (`fs`) in Node.js

Node.js provides the `fs` module to interact with the file system, allowing you to **create, read, update, and delete** files and directories — both synchronously and asynchronously.

---

## Importing the `fs` Module

```js
const fs = require('fs');
```
## 1. Reading Files
- Asynchronous (Non-blocking)
```
fs.readFile('example.txt', 'utf8', (err, data) => {
  if (err) return console.error(err);
  console.log(data);
});
```
- Synchronous (Blocking)
```
const data = fs.readFileSync('example.txt', 'utf8');
console.log(data);
```
## 2. Writing to Files
- Asynchronous
```
fs.writeFile('example.txt', 'Hello, Node.js!', (err) => {
  if (err) throw err;
  console.log('File written successfully!');
});
```
- Synchronous
```
fs.writeFileSync('example.txt', 'Hello, again!');
```
## 3. Appending Data
```
fs.appendFile('example.txt', '\nNew Line!', (err) => {
  if (err) throw err;
  console.log('Data appended!');
});
```
## 4. Deleting Files
```
fs.unlink('example.txt', (err) => {
  if (err) throw err;
  console.log('File deleted!');
});
```
## 5. Creating Directories
```
fs.mkdir('myFolder', (err) => {
  if (err) throw err;
  console.log('Folder created!');
});
```
## 6. Removing Directories
```
fs.rmdir('myFolder', (err) => {
  if (err) throw err;
  console.log('Folder removed!');
});
```
fs.rmdir() is deprecated in newer versions. Use fs.rm() with { recursive: true }.

7. Checking File/Folder Existence
```
fs.exists('example.txt', (exists) => {
  console.log(exists ? 'Exists' : 'Not found');
});
```
Or use:

```
fs.access('example.txt', fs.constants.F_OK, (err) => {
  console.log(err ? 'File does not exist' : 'File exists');
});
```
## Best Practices
Prefer asynchronous methods for scalability.

Wrap fs operations in Promises using fs.promises or util.promisify().

Handle errors gracefully.

### Bonus: Using fs.promises
```
const fsPromises = require('fs').promises;

async function readFile() {
  try {
    const data = await fsPromises.readFile('example.txt', 'utf8');
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}
readFile();
```
