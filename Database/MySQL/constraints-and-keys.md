# Constraints & Keys in MySQL

**Constraints** are rules applied to table columns to enforce data integrity.  
**Keys** help uniquely identify rows and establish relationships between tables.

---

## Common Constraints

| Constraint       | Description |
|------------------|-------------|
| **NOT NULL**     | Ensures the column cannot have a NULL value |
| **UNIQUE**       | Ensures all values in a column are unique |
| **PRIMARY KEY**  | Combines NOT NULL and UNIQUE. Uniquely identifies each row |
| **FOREIGN KEY**  | Ensures referential integrity between tables |
| **CHECK**        | Validates values based on a condition |
| **DEFAULT**      | Sets a default value if none is provided |

---

##  Keys Explained

| Key Type        | Description |
|-----------------|-------------|
| **Primary Key** | Unique + NOT NULL, used to identify records |
| **Foreign Key** | Links to a primary key in another table |
| **Composite Key** | A primary key made of more than one column |

---

## Examples

### PRIMARY KEY

```sql
CREATE TABLE users (
  id INT PRIMARY KEY,
  name VARCHAR(100)
);
```

## FOREIGN KEY
```
CREATE TABLE orders (
  id INT PRIMARY KEY,
  user_id INT,
  FOREIGN KEY (user_id) REFERENCES users(id)
);
```

## UNIQUE + NOT NULL
```
CREATE TABLE employees (
  id INT PRIMARY KEY,
  email VARCHAR(100) UNIQUE NOT NULL
);
```

## DEFAULT + CHECK
```
CREATE TABLE products (
  id INT,
  price DECIMAL(10, 2) DEFAULT 0.00,
  stock INT CHECK (stock >= 0)
);
```

## Notes
- A table can only have one primary key, but it can be made up of multiple columns.
- FOREIGN KEY relationships must match data types.
- CHECK constraints are supported from MySQL 8.0+

