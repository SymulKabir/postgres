🧩 Flask App Database Initialization Guide

Repository: https://github.com/moa-digitalagency/JusristudeAI.git

Stack: Python (Flask) + PostgreSQL

#### Open the PostgreSQL shell as the postgres admin:
```bash
sudo -u postgres psql
```

#### Create the new user:
```sql
CREATE USER jusristude_user WITH PASSWORD 'jusristude_54321';
```

#### Create the database (if it doesn’t exist):
```sql 
CREATE DATABASE jusristude OWNER jusristude_user;
```

#### Grant full access on that database to your new user:

```sql
GRANT ALL PRIVILEGES ON DATABASE jusristude TO jusristude_user;

```

#### Connect to your database:

```sql
\c jusristude

```

#### Change the owner of the `public` schema to `jusristude_user`:

```sql
ALTER SCHEMA public OWNER TO jusristude_user;
```

#### Grant all privileges on the `public` schema to `jusristude_user`: 

```sql 
GRANT ALL PRIVILEGES ON SCHEMA public TO jusristude_user;
```

#### Verify the schema owner and privileges:

```sql 
\dn+
```
You should now see:
```sql 
Name   | Owner   | Access privileges
-------+---------+------------------
public | jusristude_user | bellari=UC/jusristude
```

####  ✅ After that, exit psql:

```sql 
\q
```
 

 
