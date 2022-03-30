## Build postgre + pgadmin using Docker


put this recipe to `docker-compose.yml` and run it with `docker-compose up`

```yaml
version: '3.8'

services:  

  db:
    container_name: pg_container
    image: postgres
    restart: always
    environment:
      POSTGRES_USER: root
      POSTGRES_PASSWORD: root
      POSTGRES_DB: test_db
    ports:
      - "5432:5432"
  pgadmin:
    container_name: pgadmin4_container
    image: dpage/pgadmin4
    restart: always
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@admin.com
      PGADMIN_DEFAULT_PASSWORD: root
    ports:
      - "5050:80"
```

if you set `POSTGRES_HOST_AUTH_METHOD` in postgres environment to `trust`, then `POSTGRES_PASSWORD` is not required.

## psql command list

some most used commands

| command | description |
|---------|------------:|
|`psql -d database -U user -W` | connects to database under a specific user |
|`\l` | list available databases |
| `\dt` | list available tables |
| `\d table_name` | describe a table |
| `\dn` | list all schemes of the currently connected db |
| `\df` | list available functions in the current db |
| `\dv` | list available view |
| `\du` | list all users and their assign role |
| `\g` | execute the last command again |
| `\?` | know all available psql commands |
| `\h` | get help |
| `\H` | switch the output to the HTML format | 
| `\q` | exit psql shell | 
| `\c db_name` | switch database |
| `SELECT current_database()` | retrieve the current database version  |
| `SELECT version();` | retrieve the current version |
| `CREATE DATABASE db_name;` | create database |
| `CREATE TABLE colors (ColorID int, ColorName char(20));` | create table named 'colors' |
| `INSERT INTO colors VALUES (1, 'red'), (1, 'blue'), (1, 'green');` | insert data to table | 

## Show all database from terminal

```
psql -U root -c "SELECT * FROM pg_database";
```
- `-U` is user 
- `-c` is command querry

## Create role with option

`CREATE ROLE <role_name> [option]`

list of option: https://www.postgresql.org/docs/current/sql-createrole.html

sample options:

- `SUPERUSER`
- `LOGIN`

## Restore dump file

`psql dbname < dumpfile`

source: https://www.postgresql.org/docs/current/backup-dump.html

## Drop role

`DROP ROLE <role_name>`

## PostgreSQL Native Data Types

from the most common:
1. Number 
    - *integer* with range -/+2 bilion, 
    - *smallint*
    - *bigint*
    - *numeric* or *decimal* (eg. 123.45 would require a `numeric(5,2)`)
    - *real* and *double precision* is for floating values or data science application
2. Character
    - *char(n)* the characters should fit _n_ number
    - *varchar(n)* with length max _n_
    - *text* is for blog post or article
3. Date/Time
    - *date* stores dates between 4713 BC and 5874897 AD
    - *time* will store time of day accurate to 1 microsecond
    - *timestamp* to record both time and date in one column
    - *timestamp with time zone* 
4. Monetary
5. Binary
6. Boolean
7. Geometric
etc...
