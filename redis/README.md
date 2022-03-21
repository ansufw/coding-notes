# install redis via docker


```sh
docker run --name my-redis -p 6379:6379 -d redis
```
source : https://medium.com/idomongodb/installing-redis-server-using-docker-container-453c3cfffbdf

this command will do the following:

1. pull the latest image from the docker hub
2. Create and run the container and name it: my-redis
3. Route port 6379 on my laptop to port 6379 inside the container. 6379 is Redis default port and can be changed


# running redis

## enter docker terminal interactive

enter to docker `docker exec -it <container name> <bash>` The -i flag keeps input open to the container, and the -t flag creates a pseudo-terminal that the shell can attach to. 

the `<bash>` is shell program location in your machine. In linux it is usually `/bin/bash` and for MacOS `/bin/sh`

## running redis cli

by running `redis-cli -h localhost`

## Let's play arround

Now you can try some codes to play with redis !

### Selecting database

selecting database 1

`select 1`

selecting database 2

`select 2`

### Show redis information

`info keyspace`

### Show all keys in the database

`keys *`



# data type in redis

1. strings
2. lists -> simply lists of strings, sorted by insertion order
3. sets -> an unordered collection of string
4. hashes -> are map between string fields and string value
5. sorted sets -> ordered sets

## 1 String


