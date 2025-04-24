# Advanced Queries in MySQL

This section covers powerful SQL techniques to handle complex data operations efficiently using advanced query methods.

---

## 1. Subqueries

A query nested within another query.

```sql
SELECT name FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```

## 2. Aliases
Give temporary names to columns or tables for readability.

```
SELECT name AS 'Employee Name', salary AS 'Income'
FROM employees;
```

## 3. CASE Statements
Used to implement conditional logic in queries.

```
SELECT name,
  CASE 
    WHEN salary > 50000 THEN 'High'
    WHEN salary > 30000 THEN 'Medium'
    ELSE 'Low'
  END AS Salary_Level
FROM employees;
```

## 4. Nested SELECT
A query within FROM, useful for summarizing data.

```
SELECT dept, AVG(salary) as avg_salary
FROM (
  SELECT dept, salary FROM employees
) AS sub
GROUP BY dept;
```

## 5. EXISTS vs IN
IN: Checks values within a list.
```
SELECT name FROM employees 
WHERE dept_id IN (1, 2, 3);
```

EXISTS: Checks if subquery returns any rows.

```
SELECT name FROM departments d
WHERE EXISTS (
  SELECT * FROM employees e WHERE e.dept_id = d.id
);
```

## 6. UNION & UNION ALL
Combines results from multiple queries.

```
SELECT name FROM employees
UNION
SELECT name FROM managers;
```

- UNION removes duplicates
- UNION ALL keeps all records

## 7. LIMIT & OFFSET
Used for pagination.

```
SELECT * FROM employees
LIMIT 10 OFFSET 20;
```

## 8. Common Table Expressions (CTEs)
Temporary result sets used within queries.

```
WITH HighEarners AS (
  SELECT * FROM employees WHERE salary > 60000
)
SELECT * FROM HighEarners;
```

## Summary

| Feature   | Description                         |
|-----------|-------------------------------------|
| Subquery  | Query inside another query          |
| CASE      | Conditional logic                   |
| CTE       | Reusable temporary query block      |
| UNION     | Merge results from multiple queries |
| EXISTS    | Checks subquery for existence       |
