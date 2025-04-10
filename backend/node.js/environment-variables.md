# Environment Variables in Node.js

Environment variables are used to store **configuration values** (like database credentials, API keys, or secret tokens) **outside your source code**. This makes your application more **secure**, **scalable**, and **portable**.

---

## Why Use Environment Variables?

- Keep **sensitive data** (like passwords) out of code.
- Easily change values for different environments (development, production).
- Avoid hard-coding configuration values.

---

## Using `process.env`

In Node.js, environment variables can be accessed using:

```js
console.log(process.env.PORT); // e.g., 3000
```
### You can set environment variables temporarily like:
```
PORT=5000 node app.js
```
### Using .env File with dotenv
For real-world projects, we commonly use a .env file to manage variables, and load them using the dotenv package.

### 1 Install dotenv
```
npm install dotenv
```
### 2 Create a .env File
env
```
PORT=4000
DB_URI=mongodb://localhost:27017/mydb
SECRET_KEY=mysecretkey
```
### 3 Load .env in Your App
```
require('dotenv').config();

const port = process.env.PORT;
console.log(`Server running on port ${port}`);
```
### Make sure to add .env to your .gitignore file so it’s not pushed to GitHub.

###n .gitignore Example
```
node_modules/
.env
```

### Best Practices
- Never push .env files to version control.
- Use process.env to access environment variables.
- Keep sensitive info like passwords, tokens, and API keys in .env.

### Common Use Cases
 | Variable |	Purpose |
 | ---------- | -------- |
| PORT | 	Define server port |
| DB_URI |	MongoDB or other database URL |
| JWT_SECRET | Secret key for authentication |
| API_KEY	 | Third-party service credentials |

### Pro Tip
You can define default values in case environment variables are missing:

```
const port = process.env.PORT || 3000;

```
