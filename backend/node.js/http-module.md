# HTTP Module in Node.js

Node.js provides a built-in **`http` module** that allows us to create **web servers** and handle **HTTP requests and responses**.

---

## Importing the HTTP Module

```js
const http = require('http');
```
### Creating a Basic Server
```
const http = require('http');

const server = http.createServer((req, res) => {
  res.write('Hello, World!');
  res.end();
});

server.listen(3000, () => {
  console.log('Server is running on http://localhost:3000');
});
```
- This server listens on port 3000 and responds with "Hello, World!" to every request.

### Handling Request Data
You can access the request URL and method using req.url and req.method.
```
const server = http.createServer((req, res) => {
  if (req.url === '/about') {
    res.end('About Page');
  } else if (req.url === '/') {
    res.end('Home Page');
  } else {
    res.end('404 Not Found');
  }
});
```
### Sending JSON Response
```
const server = http.createServer((req, res) => {
  res.setHeader('Content-Type', 'application/json');
  const data = { message: 'Hello from server!' };
  res.end(JSON.stringify(data));
});
```
### Setting HTTP Status Codes
```
res.statusCode = 404;
res.end('Page Not Found');
```
Or combine:
```
res.writeHead(404, { 'Content-Type': 'text/plain' });
res.end('Page Not Found');
```
### Serving HTML Content
```
const fs = require('fs');

const server = http.createServer((req, res) => {
  fs.readFile('index.html', (err, data) => {
    if (err) {
      res.writeHead(500);
      res.end('Server Error');
    } else {
      res.writeHead(200, { 'Content-Type': 'text/html' });
      res.end(data);
    }
  });
});
```
## Key Points

| Feature              | Description                                          |
| -------------------- | ---------------------------------------------------- |
| http.createServer()  | Creates an HTTP server instance                      |
| req                  | Incoming request object                              |
| res                  | Server response object                               |
| res.write()         | Sends data to client (can be used multiple times)    |
| res.end()           | Ends the response                                    |


## Real-World Use Cases

- Building custom backend logic
- Creating mock APIs for testing
- Learning how HTTP works under the hood
