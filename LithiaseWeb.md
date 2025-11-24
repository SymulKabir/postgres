🧩 Flask App Database Initialization Guide

Repository: https://github.com/moa-digitalagency/LithiaseWeb.git

Stack: Python (Flask) + PostgreSQL

#### Open the PostgreSQL shell as the postgres admin:
```bash
sudo -u postgres psql
```

#### Create the new user:
```sql
CREATE USER lithiase_user WITH PASSWORD 'lithiase54321';
```

#### Create the database (if it doesn’t exist):
```sql 
CREATE DATABASE lithiase OWNER lithiase_user;
```

#### Grant full access on that database to your new user:

```sql
GRANT ALL PRIVILEGES ON DATABASE lithiase TO lithiase_user;

```

#### Connect to your database:

```sql
\c lithiase

```

#### Change the owner of the `public` schema to `lithiase`:

```sql
ALTER SCHEMA public OWNER TO lithiase_user;
```

#### Grant all privileges on the `public` schema to `lithiase`: 

```sql 
GRANT ALL PRIVILEGES ON SCHEMA public TO lithiase_user;
```

#### Verify the schema owner and privileges:

```sql 
\dn+
```
You should now see:
```sql 
Name   | Owner   | Access privileges
-------+---------+------------------
public | lithiase_user | bellari=UC/lithiase_user
```

####  ✅ After that, exit psql:

```sql 
\q
```
