🧩 Flask App Database Initialization Guide

Repository: https://github.com/moa-digitalagency/CyberConfiance.git

Stack: Python (Flask) + PostgreSQL

#### Open the PostgreSQL shell as the postgres admin:
```bash
sudo -u postgres psql
```

#### Create the new user:
```sql
CREATE USER cyber_confiance_user WITH PASSWORD 'cyber_confiance54321';
```

#### Create the database (if it doesn’t exist):
```sql 
CREATE DATABASE cyber_confiance OWNER cyber_confiance_user;
```

#### Grant full access on that database to your new user:

```sql
GRANT ALL PRIVILEGES ON DATABASE cyber_confiance TO cyber_confiance_user;

```

#### Connect to your database:

```sql
\c cyber_confiance

```

#### Change the owner of the `public` schema to `kansotex`:

```sql
ALTER SCHEMA public OWNER TO cyber_confiance_user;
```

#### Grant all privileges on the `public` schema to `cyber_confiance_user`: 

```sql 
GRANT ALL PRIVILEGES ON SCHEMA public TO cyber_confiance_user;
```

#### Verify the schema owner and privileges:

```sql 
\dn+
```
You should now see:
```sql 
Name   | Owner   | Access privileges
-------+---------+------------------
public | cyber_confiance_user | bellari=UC/cyber_confiance
```

####  ✅ After that, exit psql:

```sql 
\q
```
 

 
