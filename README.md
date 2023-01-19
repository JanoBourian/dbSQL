# Fast query examples

## Creating a Docker container

For this application we going to work with **MySQL**. The official image is in: https://hub.docker.com/_/mysql
But the steps about the configuration are in: https://platzi.com/tutoriales/1432-docker/3268-como-crear-un-contenedor-con-docker-mysql-y-persistir-la-informacion/

### Steps:

- Review docker state

```cmd
docker --version
docker image
docker ps
docker ps -a
```

- Download the official image.

```cmd
docker pull mysql
```

- Started a MySQL instance:
    - **some-mysql**: is the container name- it : interactive mode and terminal
    - **my-secret-pw**: password
    - **tag**: the specific version of mysql
    - **d**: Deatached mode (Running in background)
    - **p**: Port 
    - **name**: indicate that the next command will be the container name
    - **e**: environment for the password

By documentation
```cmd
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag
docker run --name mysqlcourse -e MYSQL_ROOT_PASSWORD=simplepassword -d mysql:latest
```

By Platzi
```cmd
docker run -d -p 33060:3306 --name mysqlcontainer -e MYSQL_ROOT_PASSWORD=simplepassword mysql:latest
```

### To into the container

- **exec**: we will pass a command
- **-it**: Interactive mode
- **mysql -p**: To into with root user

```cmd
docker exec -it mysqlcontainer mysql -p
```

## Conecting and store the information with the DataBase Manager

For more information you can check this: https://earthly.dev/blog/docker-mysql/

- Delete the last process
```cmd
docker rm -f mysqlcontainer
```

- Delete all volumes:
```cmd
docker volume prune
```

- Create a volume
```cmd
docker volume create mysqlcourse
docker volume ls
```

- Start again docker 
```cmd
docker run -d -p 33060:3306 --name mysqlcontainer -e MYSQL_ROOT_PASSWORD=simplepassword -v mysqlcourse=/var/lib/mysql mysql:latest
```

```cmd
docker exec -it mysqlcontainer mysql -p
```

<hr>

## Introduction

Database is a set of information relationed.
SGBD: MySQL, MariaDB, Oracel, Microsoft SQL Server.

Relations:

    - Many-to-Many: (N:N) Product-Sale
    - One-to-Many: (1:M) Debt-Client
    - One-to-One: (1:1) Person-Family
    
SQL (Structure Query Language): SQL is the standard, but each DBGS decide the implementation

    - Types:
        - String
        - Integer
        - Decimal
        - Date
    - Data Types:
        - varchar(x)
        - char(x)
        - tinyint
        - smallint
        - int
        - bigint
        - float
        - double
        - datetime
        - blob: Binary information as file o text
        
    - Transaction:
        - Has only two results: done and fail, doesn't exist middle state.
        - Should abide ACID properties:
            - Atomicity: A transaction should be executed all
            - Concistency: No affect the data structure
            - Isolation: Only one, altough exist another
            - Durability: The future changes will be permanents.

    - Categories:

        - DDL: Data Definition Languages 
            - CREATE: Create a new table, database or schema
            - ALTER: Modify already exists table o column properties
            - DROP: Delete some object already exists in database

        - DML: Data Manipulation Languages (CRUD)
            - SELECT: Select item 
            - INSERT: Insert item inside a table
            - UPDATE: Update item
            - DELETE: Delete item

        - DCL: Data Control Language (about users)
            - GRANT: Allow users
            - REVOKE: Revoke permissions
            
        - TCL: Transaction Control Language
            - COMMIT: Save information
            - ROLLBACK: Back to last state.

## Environment

At this point we are using a docker container. But also we are using DBeaver and Console. 

```cmd
docker exec -it mysqlcontainer mysql -p
```

<hr>

## Normalization

We are looking for a database optimization

This topic is in: **01_normalizacion**

<hr>

## Design and Creation

For this topics please check: **02_consola**

<hr>

## Manipulation using SQL queries


## Aditional Functions


## Group Tables


## Store Procedures, Funtioncs, Triggers, Index


## Access and Backup


## All sentences

```cmd
docker exec -it mysqlcontainer mysql -p
```

```sql
SHOW DATABASES;
USE database_name;
SHOW TABLES;
DESCRIBE table_name;
EXIT;
``` 

```sql
```

```sql
```

```sql
```

```sql
```

