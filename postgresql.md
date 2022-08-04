[[LINUX]]
# postgreql

## create database  
- create folder
- dreate database inside folder:
    - `initdb .`

## start database
- inside folder:
    - `pg_ctl -D . -l logdatei start`

## stop database
- inside folder:
    - `pg_ctl -D . stop`

## enter database
- list databases:
    - `psql -l`
- enter:
    - `psql NAME`


