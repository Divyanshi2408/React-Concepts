# Indexing in MySQL

Indexing is a performance optimization technique that speeds up the retrieval of rows from a table by creating data structures (indexes) that make lookups faster.

---

## What is an Index?

An **index** is a data structure (typically a B-Tree) associated with a table column to optimize query performance.

Without an index, MySQL performs a full table scan. With indexes, it can locate data faster.

---

## Why Use Indexes?

- Improve **SELECT** query performance
- Speed up **WHERE**, **JOIN**, and **ORDER BY** clauses
- Enforce **UNIQUE** constraints
- Optimize searches on large datasets

---

## Types of Indexes

| Index Type     | Description                                 |
|----------------|---------------------------------------------|
| Primary Index  | Automatically created on the primary key    |
| Unique Index   | Ensures all values in the column are unique |
| Composite Index| Index on multiple columns                   |
| Full-text Index| For text searching using `MATCH AGAINST`    |
| Spatial Index  | For spatial data types                      |
| Normal Index   | Basic non-unique index                      |

---

## Creating Indexes

```sql
-- Single column index
CREATE INDEX idx_name ON employees(name);

-- Composite index
CREATE INDEX idx_dept_salary ON employees(dept, salary);
```
## Viewing Indexes
```
SHOW INDEX FROM employees;
```

## Dropping Indexes
```
DROP INDEX idx_name ON employees;
```

## When Not to Use Indexes
- On small tables (no major performance gain)
- On columns with low selectivity (e.g., many duplicate values)
- Too many indexes can slow down INSERT, UPDATE, and DELETE
