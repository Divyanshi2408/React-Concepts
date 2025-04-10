# 🔄 Streams & Buffers in Node.js

Streams and Buffers are **core concepts** in Node.js for handling **large amounts of data** efficiently, especially for I/O operations like file reading/writing, network requests, or video/audio processing.

---

## What is a Buffer?

- A **Buffer** is a temporary memory space for **binary data**.
- Used when dealing with raw data streams (e.g., reading from files, TCP streams).
- Comes from Node.js’s `Buffer` class.

### Example: Creating a Buffer

```js
const buffer = Buffer.from('Hello');
console.log(buffer);          // <Buffer 48 65 6c 6c 6f>
console.log(buffer.toString()); // Hello
```
### What is a Stream?
A Stream is a sequence of data that flows in chunks, making it memory-efficient and faster than loading all data at once.

### Four Types of Streams:
Type	Description
- Readable	For reading data (e.g., fs.createReadStream)
- Writable	For writing data (e.g., fs.createWriteStream)
- Duplex	Both readable and writable (e.g., TCP socket)
- Transform	Duplex stream that modifies data (e.g., zlib)
### Readable Stream Example
```
const fs = require('fs');

const readStream = fs.createReadStream('input.txt', 'utf8');

readStream.on('data', (chunk) => {
  console.log('Received chunk:', chunk);
});

readStream.on('end', () => {
  console.log('No more data.');
});
```
### Writable Stream Example
```
const fs = require('fs');

const writeStream = fs.createWriteStream('output.txt');

writeStream.write('Writing to a file...\n');
writeStream.end('Done!');
```
### Pipe Method
You can connect streams using .pipe() — perfect for reading and writing at once.
```
const fs = require('fs');

const readStream = fs.createReadStream('input.txt');
const writeStream = fs.createWriteStream('output.txt');

readStream.pipe(writeStream);
```
- This will copy content from input.txt to output.txt efficiently.

## Transform Streams
Used for modifying data on the fly (e.g., compressing with zlib):
```
const zlib = require('zlib');
const fs = require('fs');

fs.createReadStream('file.txt')
  .pipe(zlib.createGzip())
  .pipe(fs.createWriteStream('file.txt.gz'));
```
## Why Use Streams?
- Efficient for large files or real-time data
- Lower memory footprint
- Asynchronous and non-blocking

