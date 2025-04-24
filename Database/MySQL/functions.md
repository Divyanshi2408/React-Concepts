# Functions in MySQL

**MySQL functions** are built-in operations that let you perform calculations, manipulate data, or retrieve information. They can be used in `SELECT`, `WHERE`, `ORDER BY`, and other clauses.

---

## 1. Numeric Functions

| Function         | Description |
|------------------|-------------|
| `ABS(x)`         | Returns the absolute value of x |
| `CEIL(x)`        | Rounds x up to the nearest integer |
| `FLOOR(x)`       | Rounds x down to the nearest integer |
| `ROUND(x, d)`    | Rounds x to d decimal places |
| `MOD(x, y)`      | Returns remainder of x/y |

```sql
SELECT ABS(-10), ROUND(3.14159, 2);
```

## 2. Date & Time Functions

| Function | Description |
|----------|-------------|
| `NOW()` | Returns current date and time |
| `CURDATE()` | Returns current date |
| `CURTIME()` | Returns current time |
| `DATEDIFF(d1, d2)` | Returns difference in days between dates |
| `DATE_ADD(date, INTERVAL n unit)` | Adds interval to date |

```
SELECT NOW(), DATEDIFF('2025-01-01', '2024-01-01');
```

## 3. String Functions

| Function | Description |
|----------|-------------|
| `LENGTH(str)` | Returns length in bytes |
| `CHAR_LENGTH(str)` | Returns number of characters |
| `CONCAT(s1, s2, ...)` | Joins strings |
| `LOWER(str)` / `UPPER(str)` | Changes case |
| `SUBSTRING(str, pos, len)` | Extracts part of a string |
| `TRIM(str)` | Removes whitespace |

```
SELECT CONCAT('My', 'SQL'), UPPER('hello');
```

## 4. Aggregate Functions

| Function | Description |
|----------|-------------|
| `COUNT(*)` | Returns number of rows |
| `SUM(col)` | Returns total of a column |
| `AVG(col)` | Returns average value |
| `MIN(col)` | Returns smallest value |
| `MAX(col)` | Returns largest value |

```
SELECT COUNT(*) FROM users;
SELECT AVG(price) FROM products;
```

## 5. Control Flow Functions

Function	Description
IF(condition, t, f)	Returns t if condition is true, else f
CASE	Multiple condition checks

```
SELECT IF(10 > 5, 'Yes', 'No');

SELECT 
  CASE 
    WHEN score >= 90 THEN 'A'
    WHEN score >= 80 THEN 'B'
    ELSE 'C'
  END AS grade
FROM marks;
```

## Notes
- Functions can be nested and combined for powerful queries.
- String, date, and math functions are useful for data transformation.
