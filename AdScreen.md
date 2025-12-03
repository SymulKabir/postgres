🧩 Flask App Database Initialization Guide

Repository: https://github.com/moa-digitalagency/AdScreen.git

Stack: Python (Flask) + PostgreSQL

#### Open the PostgreSQL shell as the postgres admin:
```bash
sudo -u postgres psql
```

#### Create the new user:
```sql
CREATE USER adscreenuser WITH PASSWORD 'StrongPassword123';
```

#### Create the database (if it doesn’t exist):
```sql 
CREATE DATABASE adscreen OWNER adscreenuser;
```

#### Grant full access on that database to your new user:

```sql
GRANT ALL PRIVILEGES ON DATABASE adscreen TO adscreenuser;

```

#### Connect to your database:

```sql
\c adscreen

```

#### Change the owner of the `public` schema to `adscreenuser`:

```sql
ALTER SCHEMA public OWNER TO adscreenuser;
```

#### Grant all privileges on the `public` schema to `adscreenuser`: 

```sql 
GRANT ALL PRIVILEGES ON SCHEMA public TO adscreenuser;
```

#### Verify the schema owner and privileges:

```sql 
\dn+
```
You should now see:
```sql 
Name   | Owner   | Access privileges
-------+---------+------------------
public | adscreenuser | bellari=UC/adscreenuser
```

####  ✅ After that, exit psql:

```sql 
\q
```
