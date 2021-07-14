---
layout: post
title:  "Install & Configure PostGreSQL on macOS for development"
date:   2021-07-05 05:42:21 +0530
categories: postgresql
---

# Install & Configure PostGreSQL on macOS:

```bash

# Install brew, if you don't have brew already installed.
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

brew update
brew install postgresql

# see if postgres is running and its version
postgres --version
ps -aef | grep postgres

# Look at the services of brew and verify that postgresql is running
brew services 

# If you happened to get an error
rm /usr/local/var/postgres/postmaster.pid

# Try to launch postgresql using launchctl 
launchctl load -w /usr/local/Cellar/postgresql/13.2_1/homebrew.mxcl.postgresql.plist 

# You can start and Stop postgres manually.
pg_ctl -D /usr/local/var/postgres start
pg_ctl -D /usr/local/var/postgres stop

# Start and Stop postgres brew way, it will also restart
brew services start postgres
brew services stop postgres
brew services restart postgresql

initdb /usr/local/var/postgres

# Run psql with specified port and hostname
psql -p 5432 -h localhost

# create and drop DB
createdb <database_name>
dropdb <database_name>

# Use psql to see if you view the psql console
psql <database_name>

# Exit the psql prompt using `CTRL + d`

# You can create and drop DB inside psql
CREATE DATABASE <database_name>;
DROP DATABASE <database_name>;

# \list - List all of your actual databases.
# \c mydatabasename - Connect to another database.
# \d - List the relations of your currently connected database.
# \d mytablename - Shows information for a specific table.


# plsql authentication system
# ---------------------------
# ident authentication uses the operating system's identification server running at TCP port 113 to verify the user's credentials.

# peer authentication on the other hand, is used for local connections and verifies that the logged in username of the operating system matches the username for the Postgres database.

sudo -u postgres psql
# or
sudo -u postgres psql template1

# If you receive an authentication error when attempting to connect to the psql client, you may need to alter the Postgres authentication config file (pg_hfa.conf).

find / -name pg_hba.conf
subl /usr/local/var/postgres/pg_hba.conf
# Add a Line like this, save and exit.
local all postgres peer

psql template1

template1-# CREATE USER postgres PASSWORD 'NewTamperedPassword'
ALTER ROLE postgres PASSWORD 'NewTamperedPassword'
template1-# ALTER ROLE
template1-# \q

# Export relevant environmental variables, if needed.
export POSTGRES_HOST=localhost
export POSTGRES_PORT=5432
export POSTGRES_DB=<database_name>
export POSTGRES_USER=<database_user>
export POSTGRES_PASSWORD=<password>

# For Django App:
# Adjust the Django settings.py on your root of your App.

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'yourproject',
        'USER': 'yourprojectuser',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '5432',
      }
  }

```
