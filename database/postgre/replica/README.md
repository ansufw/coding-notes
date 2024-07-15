# postgres

1. create project folder contains 3 folder (pg-0, pg-1, pg-2) for storing pg instance configs, 1 for master (pg-0) and the rest for replica/backup.
2. create network `docker network create postgres`
3. get configuration files ready (`pg_hba.conf`, `pg_ident.conf`, `postgresql.conf`), put under `config` folder
    - in the file `pg_hba.conf` of primary pg, add this line:
        ```
        host    replication     replicationUser     0.0.0.0/0   md5
        ```
    - in the file `pg_indent.conf` of primary pg, add following
        ```
        wal_level = replica
        max_wal_senders = 5

        archive_mode = on
        archive_command = 'test ! -f /mnt/server/archive/%f && cp %p /mnt/server/archive/%f'
        ```
4. run docker primary pg from project folder:
    ```
    docker run -it --rm --name pg-0 \
        --net postgres \
        -e POSTGRES_USER=postgresadmin \
        -e POSTGRES_PASSWORD=admin123 \
        -e POSTGRES_DB=postgresdb \
        -e PGDATA="/data" \
        -v ${PWD}/pg-0/pgdata:/data \
        -v ${PWD}/pg-0/config:/config \
        -v ${PWD}/pg-0/archive:/mnt/server/archive \
        -p 5100:5432 \
        postgres:15.0 -c 'config_file=/config/postgresql.conf'
    ```
5. create user for replica postgres connecting to master
    - run `docker exec -it pg-0 bash`
    - run `createuser -U postgresadmin -P -c 5 --replication replicationUser`
6. run pg backup utility
    - run container of replica pg-1 from project dir
        ```
        docker run -it --rm \
            --net postgres \
            -v ${PWD}/pg-1/pgdata:/data \
            --entrypoint /bin/bash postgres:15.0
        ```
    - take the backup by logging into `pg-0` with our `replicationUser` and writing the backup to `/data`
        ```
        pg_basebackup -h pg-0 -p 5432 -U replicationUser -D /data/ -Fp -Xs -R
        ```
7. run standby instance,
    - run this from project dir:
        ```
        docker run -it --rm --name pg-1 \
        --net postgres \
        -e POSTGRES_USER=postgresadmin \
        -e POSTGRES_PASSWORD=admin123 \
        -e POSTGRES_DB=postgresdb \
        -e PGDATA="/data" \
        -v ${PWD}/pg-1/pgdata:/data \
        -v ${PWD}/pg-1/config:/config \
        -v ${PWD}/pg-1/archive:/mnt/server/archive \
        -p 5101:5432 \
        postgres:15.0 -c 'config_file=/config/postgresql.conf'
        ```
8. test the replication
    - on our primary db:
        - login to postgres: `docker exec -it pg-0 bash` -> `psql -U postgresadmin -d postgresdb`
        - create a table: `CREATE TABLE customers (firstname text, customer_id serial, date_created timestamp);`
        - show the table: `\dt`
    - now login to secondary db, pg-1, and view the table:
        - login: `psql --username=postgresadmin postgresdb`
        - show the table: `\dt`
9. Failover
    Now let's say primary pg `pg-0` fails. Postgres does not have built-in automated failover and recovery and requires tooling to perform this.
    When `pg-0` fails, we would use a utility called `pg_ctl` to promote our stand-by server to a new primary db.
    - stop primary server to simulate failure: `docker rm -f pg-0`
    - login to secondary pg: `docker exec -it pg-1 bash` -> `psql --username=postgresadmin postgresdb`
    - create a table to test:  `CREATE TABLE customers (firstname text, customer_id serial, date_created timestamp);`
    - promote secondary pg to primary: `runuser -u postgres -- pg_ctl promote`
