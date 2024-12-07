### Posgres Todo

- `sudo -u postgres psql`
- `CREATE DATABASE app2_db;`
- `CREATE USER app2_user WITH PASSWORD 'your_secure_password';`
- `GRANT ALL PRIVILEGES ON DATABASE app2_db TO app2_user;`
- `\q`


<br>
Additional Priviliges if no access
```
GRANT CONNECT ON DATABASE app2_db TO app2_user;
GRANT USAGE ON SCHEMA public TO app2_user;
GRANT CREATE ON SCHEMA public TO app2_user;
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO app2_user;
GRANT ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA public TO app2_user;
```
