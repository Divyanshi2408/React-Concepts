#  Global Objects in Node.js

Node.js provides several **global objects**, functions, and variables that are accessible **anywhere** in your code without needing to import them.

These are different from browser globals like `window` or `document`.

---

## Common Global Objects

| Object/Function | Description |
|-----------------|-------------|
| `__dirname`     | Absolute path of the current directory |
| `__filename`    | Absolute path of the current file |
| `global`        | Like `window` in browsers – global scope |
| `module`        | Info about the current module |
| `exports`       | Used to export objects from a module |
| `require()`     | Function to import modules |
| `process`       | Provides info about the current Node.js process |
| `console`       | Standard logging tool (`log`, `error`, `warn`, etc.) |

---

## Examples

### `__dirname` & `__filename`

```js
console.log(__dirname);   // Outputs: /Users/divyanshi/project
console.log(__filename);  // Outputs: /Users/divyanshi/project/app.js
```
### require() and module
```
// math.js
exports.add = (a, b) => a + b;

// app.js
const math = require('./math');
console.log(math.add(2, 3)); // 5
```
### process
```
console.log(process.pid);          // Process ID
console.log(process.cwd());        // Current working directory
console.log(process.version);      // Node.js version
console.log(process.env.USER);     // Access environment variables
```
### You can also use it to gracefully exit:
```
if (!process.env.API_KEY) {
  console.error("Missing API_KEY");
  process.exit(1); // Exit with error
}
```
### console
```
console.log("Normal log");
console.warn("Warning!");
console.error("Error!");
```
