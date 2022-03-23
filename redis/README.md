# install redis via docker

## port 6379

```sh
docker run --name my-redis -p 6379:6379 -d redis
```

source : https://medium.com/idomongodb/installing-redis-server-using-docker-container-453c3cfffbdf

this command will do the following:

1. pull the latest image from the docker hub
2. Create and run the container and name it: my-redis
3. Route port 6379 on my laptop to port 6379 inside the container. 6379 is Redis default port and can be changed


## with volume and file configuration

```
docker run -v /myredis/conf:/usr/local/etc/redis --name myredis redis redis-server /usr/local/etc/redis/redis.conf
```

# running redis

## enter docker terminal interactive

enter to docker `docker exec -it <container name> <bash>` The -i flag keeps input open to the container, and the -t flag creates a pseudo-terminal that the shell can attach to. 

the `<bash>` is shell program location in your machine. In linux it is usually `/bin/bash` and for MacOS `/bin/sh`

## running redis cli

by running `redis-cli -h localhost`

## Let's play arround

Now you can try some codes to play with redis !

- selecting database 1 `select 1`
- selecting database 2 `select 2`
- show redis information `info keyspace`
- show all keys in the database `keys *`


# data type in redis

an introduction redis data type -->  https://redis.io/topics/data-types-intro

redis data type --> https://redis.io/topics/data-types

check data type --> `TYPE keyname`

1. strings
2. lists -> simply lists of strings, SORTED by insertion order
3. sets -> an UNORDERED and UNIQUE collection of string
4. hashes -> are map between string fields and string value
5. sorted sets -> ordered sets

## 1 String

https://redis.io/commands/#string

- set data `SET name "Ananto Yusuf"`
- delete data `DEL name`
- multiple set data `MSET fname "Yameena" lname "Azzahra"`
- multiple get data `MGET fname lname`

## 2 Lists: a simple ordered string collection

https://redis.io/commands/#list

- right push `RPUSH fruits "banana"`
- right push `RPUSH fruits "berry"`
- left push `LPUSH fruits "appl"`
- set or replace value `LSET fruits -1 "apple"`
- left push `LPUSH fruits manggo orange pear`
- right pop and show the value `RPOP fruits` 
- left pop and show the value `LPOP fruits`
- show all list `LRANGE fruits 0 -1`
- show value in first index `LINDEX fruits 0`
- show value in second index `LINDEX fruits 1`
- show value in last index `LINDEX fruits -1`
- show value in before last second index `LINDEX fruits -2`

## 3 Sets: an unique and unordered collection

https://redis.io/commands#set

- set add (sadd) is to add or create value `SADD animals "tiger" "dolphin" "eagle"`
- add value again `SADD animals "lion" "tiger" "rabit"`
- see members is to view all value `SMEMBERS animals`
- is member exist `SISMEMBER animals "tiger"`
- add "class" tagging on animals member `SADD class:mammals:animals lion elephant tiger`
- show all member that has "class" tagging `SMEMBERS class:mammals:animals`

## 4 Hashes

https://redis.io/commands#hash

suppose we want to create database for 'Naruto Mugen'

- create 1st character `HSET player:001 name "Uzumaki Naruto" origin "Konoha" attack 45 speed 30 power 46`
- get all field data 1st character `HGETALL player:001`
- get specific field data `HGET player:001 speed`
- add power by 10 `HINCRBY player:001 power 10`
- delete power `HDEL player:001 power`
- does naruto still have power?  `HEXISTS player:001 power`

## 5 Sorted Sets

https://redis.io/commands#sorted-set

the example is inspired from https://redis.io/topics/data-types-intro. We would like to make list students sorted by year of birth.

- add 1st student `ZADD students 1997 "Fitriani Eka"`
- add 2nd student `ZADD students 1991 "Rizkianto"`
- add 3rd student `ZADD students 1995 "Askar Fikri"`
