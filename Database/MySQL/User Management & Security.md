# User Management & Security in MySQL

Managing users and ensuring database security is crucial for maintaining the integrity and confidentiality of data.

## User Management

| Command | Description |
|---------|-------------|
| `CREATE USER 'username'@'host' IDENTIFIED BY 'password';` | Creates a new user |
| `GRANT ALL PRIVILEGES ON dbname.* TO 'username'@'host';` | Grants privileges to the user |
| `REVOKE privilege ON dbname.* FROM 'username'@'host';` | Revokes privileges from the user |
| `DROP USER 'username'@'host';` | Deletes a user |

---

## Security Best Practices

- **Use Strong Passwords:** Ensure all database users have strong and unique passwords.
- **Grant Minimum Privileges:** Follow the principle of least privilege. Only provide necessary access.
- **Use SSL/TLS:** Encrypt connections between your application and the database server.
- **Regularly Update MySQL:** Keep your MySQL server up to date with the latest security patches.
- **Monitor User Activity:** Log and monitor user access and operations.
- **Backup Regularly:** Always maintain regular backups to recover data in case of a security incident.

---

## Example: Creating a Secure User

```sql
CREATE USER 'secure_user'@'%' IDENTIFIED WITH mysql_native_password BY 'StrongPassword123!';
GRANT SELECT, INSERT, UPDATE ON mydatabase.* TO 'secure_user'@'%';
FLUSH PRIVILEGES;
