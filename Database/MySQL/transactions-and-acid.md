# Transactions & ACID in MySQL

Transactions in MySQL allow executing a series of operations as a single unit, ensuring data consistency and reliability.

---

## What is a Transaction?

A **transaction** is a sequence of one or more SQL statements that are executed as a single unit of work. Either all the operations succeed, or none are applied.

---

## ACID Properties

Transactions follow the **ACID** properties to ensure reliability:

| Property    | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| Atomicity   | Ensures that all operations in a transaction are completed, or none at all |
| Consistency | Ensures the database is in a valid state before and after the transaction  |
| Isolation   | Ensures transactions are executed independently                             |
| Durability  | Ensures committed changes are permanent                                     |

---

## Using Transactions in MySQL

```sql
-- Start a transaction
START TRANSACTION;

-- Execute queries
UPDATE accounts SET balance = balance - 1000 WHERE id = 1;
UPDATE accounts SET balance = balance + 1000 WHERE id = 2;

-- Commit changes
COMMIT;

-- Rollback in case of error
ROLLBACK;
```

## Transaction Control Statements


| Statement         | Description                                             |
|------------------|---------------------------------------------------------|
| `START TRANSACTION` | Begins a new transaction                            |
| `COMMIT`          | Saves all changes made during the transaction         |
| `ROLLBACK`        | Reverts all changes since the start of the transaction |
| `SAVEPOINT name`  | Sets a savepoint within a transaction                 |
| `ROLLBACK TO name`| Rolls back to the specified savepoint                 |

## Not All Storage Engines Support Transactions
MySQL storage engines:

- ✅ InnoDB – Supports transactions and ACID compliance
- ❌ MyISAM – Does not support transactions
