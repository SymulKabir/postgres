🧩 Flask App Database Initialization Guide

Repository: https://github.com/moa-digitalagency/BellariConcept.git

Stack: Python (Flask) + PostgreSQL

#### Open the PostgreSQL shell as the postgres admin:
```bash
sudo -u postgres psql
```

#### Create the new user:
```sql
CREATE USER bellari WITH PASSWORD 'bellari54321';
```

#### Create the database (if it doesn’t exist):
```sql
CREATE DATABASE bellari_concept;
```

#### Grant full access on that database to your new user:

```sql
GRANT ALL PRIVILEGES ON DATABASE bellari_concept TO bellari;

```

#### Connect to your database:

```sql
\c bellari_concept

```

#### Change the owner of the `public` schema to `bellari`:

```sql
ALTER SCHEMA public OWNER TO bellari;
```

#### Grant all privileges on the `public` schema to `bellari`: 

```sql 
GRANT ALL PRIVILEGES ON SCHEMA public TO bellari;
```

#### Verify the schema owner and privileges:

```sql 
\dn+
```
You should now see:
```sql 
Name   | Owner   | Access privileges
-------+---------+------------------
public | bellari | bellari=UC/bellari
```

####  ✅ After that, exit psql:

```sql 
\q
```

#### Step 1: Activate your virtual environment

```sql 
cd ~/BellariConcept
source venv/bin/activate

```

#### Step 2: Start Flask shell

```sql 
flask shell
```

#### Inside the Flask shell, create all tables:

```python 
from app import db
db.create_all()
exit()
```
✅ This will create all tables defined in your SQLAlchemy models.

#### Step 3: Verify tables in PostgreSQL
```bash
sudo -u postgres psql -d bellari_concept
\dt
```
You should see something like:
```bash
        List of relations
 Schema |  Name  | Type  | Owner
--------+--------+-------+-------
 public | user   | table | bellari
 public | page   | table | bellari
 ...

```
Use `\q` to exit PostgreSQL.

 