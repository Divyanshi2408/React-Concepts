# Nodemon in Node.js

**Nodemon** is a development tool that automatically restarts your Node.js application whenever you make changes to your code files. It makes your development workflow faster and easier.

---

## Why Use Nodemon?

Normally, you have to stop and restart the server manually after every change:

```
node index.js
```
But with Nodemon:
```
nodemon index.js
```
It automatically restarts the server whenever it detects changes. 

## Installation
### Install Globally
```
npm install -g nodemon
```
Can be run from anywhere on your machine.

### Install as Dev Dependency
```
npm install --save-dev nodemon
```
Ideal for project-specific usage.

### Running with Nodemon
After installing:
```
nodemon app.js
```
This will watch app.js and restart automatically on changes.

### Using with package.json
You can add a script for convenience:
```
"scripts": {
  "start": "node app.js",
  "dev": "nodemon app.js"
}
```
Run it using:
```
npm run dev
```
### How Nodemon Works
- Watches files with .js, .json, etc.
- On changes, it restarts the Node app.
- Default extensions: .js, .mjs, .json

### Customizing Nodemon
Create a nodemon.json file:
```
{
  "watch": ["server"],
  "ext": "js,json",
  "ignore": ["node_modules"],
  "exec": "node server.js"
}
```
## Pro Tips
- Use with dotenv to reload env variables.
- Pair with --inspect for debugging.
- Use nodemon --legacy-watch on Windows WSL for issues.

### Without Nodemon
```
node index.js
```
- Modify code
- Ctrl+C to stop
- Run again
- So repetitive!

### With Nodemon
```
nodemon index.js
```
# Modify code
# Auto-restart 
