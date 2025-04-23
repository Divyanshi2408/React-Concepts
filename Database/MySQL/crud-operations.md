# CRUD Operations in MySQL

CRUD stands for **Create, Read, Update, Delete** — the four basic operations for managing data in a database.

---

## 1. CREATE (INSERT)

```sql
-- Insert a new record into a table
INSERT INTO users (name, email) 
VALUES ('Alice', 'alice@example.com');
```

## 2. READ (SELECT)
```
-- Select all records
SELECT * FROM users;

-- Select specific columns
SELECT name, email FROM users;

-- Select with conditions
SELECT * FROM users WHERE name = 'Alice';

-- Using LIKE for pattern matching
SELECT * FROM users WHERE name LIKE 'A%';

-- Sorting results
SELECT * FROM users ORDER BY name ASC;

-- Limiting results
SELECT * FROM users LIMIT 5;
```

## 3. UPDATE
```
-- Update a record
UPDATE users 
SET email = 'alice.new@example.com' 
WHERE name = 'Alice';
```

## 4. DELETE
```
-- Delete a record
DELETE FROM users 
WHERE name = 'Alice';
```

## Important Notes
- Always use WHERE clause with UPDATE and DELETE to avoid affecting all records.
- Use LIMIT with caution in production updates/deletes.
- Backup your data before performing critical operations.

## Filtering with Conditions
```
-- WHERE clause with multiple conditions
SELECT * FROM users 
WHERE name = 'Alice' AND email LIKE '%@example.com';
```
