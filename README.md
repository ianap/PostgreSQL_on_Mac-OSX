# PostgreSQL on Mac OSX

1. Install Homebrew:
```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Installing Postgres 

```shell
brew install postgresql
```

Start Postgres running:
```shell
pg_ctl -D /usr/local/var/postgres start && brew services start postgresql
```

3. Make sure Postgres is installed and running
```shell
postgres -V
```

4.  Configuring Postgres
```shell
psql postgres
```
We can now enter a command to see what users are installed:
```shell
postgres=# \du
```

# Creating Users
1. Set the password for the default postgres account:
```shell
postgres=# \password postgres
```

2. Create  new role:
```shell
postgres=# CREATE ROLE new_user WITH LOGIN PASSWORD 'test_password';
postgres=# \du
```
3. Add the CREATEDB permission to  new user to allow them to create database:
```shell
postgres=# ALTER ROLE new_user CREATEDB; 
postgres=# \du
postgres=# \q 
```

# Creating DB
```shell
psql postgres -U new_user
postgres=> CREATE DATABASE test_DB;
```
add at least one user who has permission to access the database:
```shell
postgres=> GRANT ALL PRIVILEGES ON DATABASE super_awesome_application TO patrick;
postgres=> \list
postgres=> \connect super_awesome_application
postgres=> \dt
postgres=> \q
```


