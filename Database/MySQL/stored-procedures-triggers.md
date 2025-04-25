# Stored Procedures & Triggers in MySQL

MySQL provides powerful tools like **Stored Procedures** and **Triggers** to automate and encapsulate logic directly in the database.

---

## Stored Procedures

A **Stored Procedure** is a group of SQL statements that can be saved and reused.

### Benefits:
- Improves code reusability
- Enhances performance
- Helps with security by controlling data access

### Creating a Stored Procedure

```sql
DELIMITER //

CREATE PROCEDURE GetEmployeeCount()
BEGIN
    SELECT COUNT(*) FROM employees;
END //

DELIMITER ;
```

## Calling a Stored Procedure
```
CALL GetEmployeeCount();
```

## Procedure with Parameters
```
DELIMITER //

CREATE PROCEDURE GetEmployeesByDept(IN deptName VARCHAR(50))
BEGIN
    SELECT * FROM employees WHERE department = deptName;
END //

DELIMITER ;
```

## Triggers
A Trigger is a set of instructions that automatically executes in response to certain events on a table.

## When to Use:
- Audit trails
- Enforcing business rules
- Validating data

## Creating a Trigger
```
CREATE TRIGGER before_insert_employee
BEFORE INSERT ON employees
FOR EACH ROW
SET NEW.created_at = NOW();
```

## Trigger Events

| Event            | Description                            |
|------------------|----------------------------------------|
| `BEFORE INSERT`  | Trigger before inserting a row         |
| `AFTER INSERT`   | Trigger after inserting a row          |
| `BEFORE UPDATE`  | Trigger before updating a row          |
| `AFTER UPDATE`   | Trigger after updating a row           |
| `BEFORE DELETE`  | Trigger before deleting a row          |
| `AFTER DELETE`   | Trigger after deleting a row           |

## Viewing Triggers
```
SHOW TRIGGERS;
```

## Dropping a Trigger
```
DROP TRIGGER IF EXISTS before_insert_employee;
```
