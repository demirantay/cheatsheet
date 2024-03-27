
## Mysql Notes

```bash
# To enter the Mysql Shell with RDBMS password
mysql -u root -p
```

- I put qwerty... for my local computer if it asks for password
- Normally you should change your password and remember it.
- But you can always rechange the password.


```bash
# new database
mysql> CREATE DATABASE test_db;

# To make created_db the current database, use this statement:
mysql> USE test_db
Database changed
```

Errors
- You might get an error of mysql db server not starting in XAMPP, it is either because you havea a process running elswehere or your password in xampp configuration file is not matching with your computers mysql server downloaded from mysql clinet.
  ```bash
  # if you want to kill the process in bg
  ps aux | grep mysql
  sudo kill {process_id}
  ```
