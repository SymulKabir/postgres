#### Use `pg_dump` and `psql` (recommended)
This is the standard and safest method.

On your source server (where data exists)
Run:
```bash
pg_dump -U meetspot_user -h localhost -Fc meetspot > meetspot_backup.dump
```
**Explanation:**
- -U meetspot_user → PostgreSQL user
- -h localhost → Host (your current server)
- -Fc → Custom format (can also use -F p for plain SQL)
- meetspot → Database name
- Output file → meetspot_backup.dump
You may be prompted for the password (`your_secure_password`).

#### Then, copy the dump file to your new server

Use rsync:
```bash
rsync -avz /path/meetspot_backup.dump root@<New_Server_IP>:/path/path
```
#### Login in your new server
```bash
ssh root@<New_Server_IP>
```

#### Login Postgresql as root or any user
```bash
psql -U postgres -h localhost -W
```
Enter the password you just set — it should connect successfully 🎯

#### Create role and database
```sql
CREATE USER <DB_USER> WITH PASSWORD <DB_PASSWORD>;
CREATE DATABASE <DATABASE_NAME> OWNER <DB_USER>;
-- If you need to reset password
-- ALTER USER <DB_USER> WITH PASSWORD <DB_PASSWORD>;
```
#### Restore the data
```bash
pg_restore -U <DB_USER> -d <DATABASE_NAME> -h localhost /path/meetspot_backup.dump
```
#### Login your new database and check is data store or not
Login:
```bash
psql -U postgres -h localhost -W
```
Check the data:
```sql
\dt
```


