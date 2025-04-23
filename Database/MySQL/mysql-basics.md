# MySQL Basics

This section covers the essential concepts and commands to get started with MySQL.

---

## Basic Terminology

| Term       | Description                                           |
|------------|-------------------------------------------------------|
| **Database** | A collection of related data organized in tables     |
| **Table**    | A structure to store data in rows and columns        |
| **Row**      | A single record in a table                           |
| **Column**   | A field in a table representing one piece of data    |
| **Schema**   | The structure that defines a database (tables, columns, types, etc.) |

---

## MySQL Data Types

| Category     | Examples                                |
|--------------|------------------------------------------|
| **Numeric**  | `INT`, `FLOAT`, `DOUBLE`, `DECIMAL`      |
| **String**   | `VARCHAR`, `CHAR`, `TEXT`                |
| **Date/Time**| `DATE`, `DATETIME`, `TIMESTAMP`          |
| **Boolean**  | `BOOLEAN`, `TINYINT(1)`                  |

---

## Basic SQL Commands

```sql
-- Create a database
CREATE DATABASE my_database;

-- Use a database
USE my_database;

-- Create a table
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100) UNIQUE,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);

-- View all databases
SHOW DATABASES;

-- View tables in the current database
SHOW TABLES;

-- Describe a table structure
DESCRIBE users;
```
## Clean Up
```
-- Delete a table
DROP TABLE users;

-- Delete a database
DROP DATABASE my_database;
```

## Tip
Always use meaningful table and column names that reflect the actual data for better readability and maintenance.

