# Backup & Restore in MySQL

Backing up and restoring databases is essential for disaster recovery, migration, and general maintenance.

## Backup Methods

| Method | Description |
|--------|-------------|
| `mysqldump` | Command-line tool to create logical backups (SQL scripts) |
| `mysqlpump` | Faster, parallelized version of mysqldump |
| File Copy | Physical copy of database files (for large datasets, needs downtime) |

---

## Common Backup Commands

### Using `mysqldump`
```bash
# Backup a single database
mysqldump -u username -p database_name > backup.sql

# Backup multiple databases
mysqldump -u username -p --databases db1 db2 > backup.sql

# Backup all databases
mysqldump -u username -p --all-databases > all_backup.sql
```

## Using mysqlpump
```
# Faster backup with multiple threads
mysqlpump -u username -p database_name > backup.sql
```

## Restore Methods

| Method |	Description |
| ------ | ------------- |
| mysql command |	Restore from a SQL backup file |
| File Copy |	Restore physical files (requires server downtime) |

## Common Restore Commands
```
# Restore a database
mysql -u username -p database_name < backup.sql
```

## Restore multiple databases
```
mysql -u username -p < all_backup.sql
```

## Best Practices for Backup & Restore

- Automate Backups: Set up cron jobs or scheduled tasks.
- Secure Backup Files: Protect backups with encryption and secure storage.
- Test Restores Regularly: Verify that backups can be restored properly.
- Use Incremental Backups: For large databases, save time and space.

