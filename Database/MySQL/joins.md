# Joins in MySQL

**Joins** are used to combine rows from two or more tables based on a related column between them.

---

## Types of Joins

| Join Type     | Description |
|---------------|-------------|
| **INNER JOIN**     | Returns records that have matching values in both tables |
| **LEFT JOIN**      | Returns all records from the left table, and matched records from the right |
| **RIGHT JOIN**     | Returns all records from the right table, and matched records from the left |
| **FULL OUTER JOIN**| Not directly supported in MySQL; simulated using `UNION` |
| **CROSS JOIN**     | Returns Cartesian product of both tables (all possible combinations) |

---

## INNER JOIN

```sql
SELECT orders.id, customers.name
FROM orders
INNER JOIN customers ON orders.customer_id = customers.id;
```

## LEFT JOIN
```
SELECT customers.name, orders.id AS order_id
FROM customers
LEFT JOIN orders ON customers.id = orders.customer_id;
```

## RIGHT JOIN
```
SELECT orders.id, customers.name
FROM orders
RIGHT JOIN customers ON orders.customer_id = customers.id;
```

## FULL OUTER JOIN (via UNION)
```
SELECT customers.name, orders.id
FROM customers
LEFT JOIN orders ON customers.id = orders.customer_id

UNION

SELECT customers.name, orders.id
FROM customers
RIGHT JOIN orders ON customers.id = orders.customer_id;
```

## CROSS JOIN
```
SELECT customers.name, products.name
FROM customers
CROSS JOIN products;
```

## Tip
- Always define relationships clearly using ON table1.column = table2.column.
- Use table aliases for cleaner queries.
