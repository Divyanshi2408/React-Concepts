# Express Middleware

**Middleware** in Express are functions that execute during the lifecycle of a request to the server. They have access to the `req`, `res`, and `next()` objects.

---

## What is Middleware?

Middleware functions can:

- Modify `req` and `res` objects
- End the request-response cycle
- Call `next()` to pass control to the next middleware

Basic syntax:

```js
app.use((req, res, next) => {
  console.log('Middleware running...');
  next();
});
```
## Types of Middleware
| Type |	Description |
| ------ | ------------ |
| Application-level	| Bound to app using app.use() or specific HTTP verbs |
| Router-level |	Bound to an instance of express.Router() |
| Built-in |	Included with Express like express.json() |
| Error-handling |	Defined with 4 arguments: (err, req, res, next) |
| Third-party	 | Installed via npm, e.g. morgan, cors, helmet |

## Application-Level Middleware
```
app.use((req, res, next) => {
  console.log(`${req.method} request for ${req.url}`);
  next();
});
```

Applied to every request regardless of the route.

### Router-Level Middleware
```
const router = require('express').Router();

router.use((req, res, next) => {
  console.log('Router middleware');
  next();
});

router.get('/about', (req, res) => {
  res.send('About page');
});

app.use('/api', router);
```

### Built-in Middleware
- express.json() – parses incoming JSON requests
- express.urlencoded() – parses URL-encoded bodies

```
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
```

### Third-Party Middleware
Install and use popular packages like:

```
npm install morgan cors helmet
```
```
const morgan = require('morgan');
const cors = require('cors');
const helmet = require('helmet');

app.use(morgan('dev'));
app.use(cors());
app.use(helmet());
```

### Error-Handling Middleware
```
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```
Must have four parameters – Express identifies it as an error handler this way.

### Tips

- Always call next() unless you end the response.
- Order of middleware matters!
- Use middleware for logging, auth, validation, error handling, etc.
