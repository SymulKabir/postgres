### To install PostgreSQL in Ubuntu (works for Ubuntu 22.04, 23.04, and 24.04)

#### Update package list
Before installing, always update your package repository:

```bash
sudo apt update
```
---
#### Install PostgreSQL
Run this command:

```bash
sudo apt install postgresql postgresql-contrib -y
```
This installs both PostgreSQL and useful extra tools (`postgresql-contrib`).
---
#### Check PostgreSQL service status
After installation, verify that the service is running:
```bash
sudo systemctl status postgresql
```
You should see output showing it is active (running).
If not, start it manually:
```bash
sudo systemctl start postgresql
```
And enable it to start on boot:
```bash
sudo systemctl enable postgresql
```

#### Switch to the postgres user and open the shell
```bash
sudo -i -u postgres
psql
```
If you see the PostgreSQL prompt:
```makrefile
postgres=#
```
#### Set (or reset) the postgres user password
```sql
ALTER USER postgres WITH PASSWORD 'YourNewPassword';
\q
```

it means PostgreSQL is working fine.
To exit the shell:
```sql
\q
```
#### Exit from postgres user and switch to the root user
```bash
exit
```
#### (Optional) Allow external access
If you need to connect remotely, edit:
```bash
sudo nano /etc/postgresql/16/main/postgresql.conf
```
Find the line:
```shell
#listen_addresses = 'localhost'
```
Change it to:
```ini
listen_addresses = '*'
```
Then edit `pg_hba.conf`:
```bash
sudo nano /etc/postgresql/16/main/pg_hba.conf
```
Add at the end:
```shell
host    all             all             0.0.0.0/0               md5
```
Restart PostgreSQL:
```bash
sudo systemctl restart postgresql
```
#### Test locally
Even from the same server, test with:
```bash
psql -h 127.0.0.1 -U postgres -d postgres
```

#### Test remote connection
From another computer (with PostgreSQL client installed), try connecting:
```bash
psql -h <your-server-ip> -U postgres -d postgres
```
If you’ve set a password for `postgres`, it will ask for it and connect successfully.
**✅ Example success message:**
```psql
psql (16.10)
Type "help" for help.

postgres=#
```
**❌ Example failure message:**
```psql
psql: error: connection to server at "<ip>" (port 5432) failed: Connection refused
```
That means:
- Firewall or security group blocked port 5432
- Or PostgreSQL not listening externally



















