🧩 Flask App Database Initialization Guide

Repository: https://github.com/moa-digitalagency/KansotexWeb.git

Stack: Python (Flask) + PostgreSQL

#### Open the PostgreSQL shell as the postgres admin:
```bash
sudo -u postgres psql
```

#### Create the new user:
```sql
CREATE USER kansotex WITH PASSWORD 'kansotex54321';
```

#### Create the database (if it doesn’t exist):
```sql 
CREATE DATABASE kansotex OWNER kansotex;
```

#### Grant full access on that database to your new user:

```sql
GRANT ALL PRIVILEGES ON DATABASE kansotex TO kansotex;

```

#### Connect to your database:

```sql
\c kansotex

```

#### Change the owner of the `public` schema to `kansotex`:

```sql
ALTER SCHEMA public OWNER TO kansotex;
```

#### Grant all privileges on the `public` schema to `kansotex`: 

```sql 
GRANT ALL PRIVILEGES ON SCHEMA public TO kansotex;
```

#### Verify the schema owner and privileges:

```sql 
\dn+
```
You should now see:
```sql 
Name   | Owner   | Access privileges
-------+---------+------------------
public | kansotex | bellari=UC/kansotex
```

####  ✅ After that, exit psql:

```sql 
\q
```
 

 
