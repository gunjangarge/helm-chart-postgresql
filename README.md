# Helm Chart Postgresql

## Screen recording

[![asciicast](https://asciinema.org/a/oP16eOkGophkwSYqmlyfKHbhQ.svg)](https://asciinema.org/a/oP16eOkGophkwSYqmlyfKHbhQ)

## Commands 
```
helm lint postgresql-psl
helm package postgresql-psl
helm install postgresql-psl postgresql-psl-0.1.0.tgz
```
## Connect to database
```
psql -h 10.0.0.6 -p 32000 --username abc --dbname abcdb
```
## Create table and some data
```
root@pop-os:/opt/helm-content# psql -h 10.0.0.6 -p 32000 --username abc --dbname abcdb
Password for user abc: 
psql (12.2 (Ubuntu 12.2-4))
Type "help" for help.

abcdb=# create table users (id int primary key not null, name text not null);
CREATE TABLE
abcdb=# \d users
               Table "public.users"
 Column |  Type   | Collation | Nullable | Default 
--------+---------+-----------+----------+---------
 id     | integer |           | not null | 
 name   | text    |           | not null | 
Indexes:
    "users_pkey" PRIMARY KEY, btree (id)

abcdb=# insert into users (id,name) values (1,'john');
INSERT 0 1
abcdb=# select * from users;
 id | name 
----+------
  1 | john
(1 row)

abcdb=# 
abcdb=# \q
```

## Cleanup
```
helm uninstall postgresql-psl
```
