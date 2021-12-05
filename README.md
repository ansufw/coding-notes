# CODING SNIPET

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
| `SELECT version();` | retrieve the current version |
| `\g` | execute the last command again |
| `\?` | know all available psql commands |
| `\h` | get help |
| `\H` | switch the output to the HTML format | 
| `\q` | exit psql shell | 