# Connecting MySQL with Node.js

In Node.js, you can connect to a MySQL database using libraries like **mysql** or **mysql2**.

## Install MySQL Package

```bash
# Install mysql package
npm install mysql

# or install mysql2 package (recommended)
npm install mysql2
```

## Setting Up a Connection
```
// Import the mysql module
const mysql = require('mysql');

// Create a connection
const connection = mysql.createConnection({
  host: 'localhost',
  user: 'your_username',
  password: 'your_password',
  database: 'your_database'
});

// Connect to the database
connection.connect((err) => {
  if (err) {
    console.error('Connection failed: ' + err.stack);
    return;
  }
  console.log('Connected to MySQL as id ' + connection.threadId);
});

// Close the connection
connection.end();
```

## Using mysql2 with Promises
```
// Import mysql2
const mysql = require('mysql2/promise');

async function connectDB() {
  try {
    const connection = await mysql.createConnection({
      host: 'localhost',
      user: 'your_username',
      password: 'your_password',
      database: 'your_database'
    });
    console.log('Connected to MySQL Database!');
    await connection.end();
  } catch (err) {
    console.error('Error connecting to database:', err);
  }
}

connectDB();
```

## Best Practices
- Use connection pooling for better performance in production.
- Always handle connection errors properly.
- Store database credentials securely (e.g., using Environment Variables).
