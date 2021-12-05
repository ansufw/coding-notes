
## psql command list

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
| `SELECT version();` | retrieve the current version |
| `CREATE DATABASE db_name;` | create database |
| `CREATE TABLE colors (ColorID int, ColorName char(20));` | create table named 'colors' |
| `INSERT INTO colors VALUES (1, 'red'), (1, 'blue'), (1, 'green');` | insert data to table | 

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
