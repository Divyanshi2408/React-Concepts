# Rate Limiting & Security Middleware in Express

To keep your Express app secure and performant, it's essential to implement rate limiting and other security best practices using middleware.

---

## What is Rate Limiting?

Rate limiting helps **prevent abuse** (e.g., brute force attacks or DoS attacks) by **limiting the number of requests** a user can make to your API in a certain timeframe.

---

## Required Packages

```bash
npm install express-rate-limit helmet xss-clean express-mongo-sanitize
```

## 1. Helmet – Set Secure HTTP Headers
```
const helmet = require('helmet');
app.use(helmet());
```
Purpose: Adds security headers like Content-Security-Policy, X-Frame-Options, etc.

## 2. Data Sanitization Against NoSQL Injection
```
const mongoSanitize = require('express-mongo-sanitize');
app.use(mongoSanitize());
```
Purpose: Prevents injection attacks in MongoDB by removing $ and . from requests.

## 3. Data Sanitization Against XSS Attacks
```
const xss = require('xss-clean');
app.use(xss());
```
Purpose: Cleans user input from malicious HTML and JS code.

## 4. Rate Limiting Using express-rate-limit
```
const rateLimit = require('express-rate-limit');

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // limit each IP to 100 requests per windowMs
  message: 'Too many requests from this IP, please try again later.'
});

app.use(limiter);
```

## Combine All for a Secure Setup
```
const express = require('express');
const helmet = require('helmet');
const xss = require('xss-clean');
const mongoSanitize = require('express-mongo-sanitize');
const rateLimit = require('express-rate-limit');

const app = express();

// Apply security middleware
app.use(helmet());
app.use(xss());
app.use(mongoSanitize());

const limiter = rateLimit({
  windowMs: 10 * 60 * 1000, // 10 minutes
  max: 50,
  message: 'Too many requests from this IP, please try again after 10 minutes.'
});
app.use(limiter);
```

## Summary
| Middleware	| Purpose |
| ---------- | --------- |
| helmet() |	Adds HTTP headers for basic protection |
| express-mongo-sanitize() |	Prevents NoSQL injections |
| xss-clean() |	Prevents cross-site scripting attacks |
| express-rate-limit() |	Limits repeated requests |
