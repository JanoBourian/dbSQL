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

```sql
CREATE TABLE carrera (
    codigo TINYINT AUTO_INCREMENT NOT NULL, 
    nombre VARCHAR(50) UNIQUE NOT NULL, 
    PRIMARY KEY(codigo)
    );

CREATE TABLE alumno(
    codigo INT AUTO_INCREMENT NOT NULL,
    primer_nombre VARCHAR(35) NOT NULL,
    segundo_nombre VARCHAR(35) ,
    apellido_paterno VARCHAR(35) NOT NULL,
    apellido_materno VARCHAR(35) NOT NULL,
    sexo CHAR(1) DEFAULT "F",
    fecha_nacimiento DATE DEFAULT "1990-01-01",
    codigo_carrera TINYINT,
    PRIMARY KEY (codigo),
    CONSTRAINT FK_codigo_carrera FOREIGN KEY (codigo_carrera) REFERENCES carrera (codigo) ON DELETE CASCADE ON UPDATE CASCADE 
    -- SET NULL
    -- NO ACTION / RESTRICT
);

CREATE TABLE curso(
    codigo SMALLINT(4) AUTO_INCREMENT NOT NULL,
    nombre VARCHAR(50) UNIQUE NOT NULL,
    creditos TINYINT(2) NOT NULL,
    codigo_carrera TINYINT NOT NULL,
    estado TINYINT(1) DEFAULT 1,
    PRIMARY KEY (codigo), 
    CONSTRAINT FKcodigo_carrera FOREIGN KEY (codigo_carrera) REFERENCES carrera (codigo)
);

CREATE TABLE matricula(
    codigo INT AUTO_INCREMENT NOT NULL,
    codigo_alumno INT NOT NULL,
    codigo_curso SMALLINT(4) NOT NULL, 
    fecha DATE DEFAULT "1990-01-01",
    PRIMARY KEY (codigo),
    CONSTRAINT FK_codigo_alumno FOREIGN KEY (codigo) REFERENCES alumno (codigo),
    CONSTRAINT FK_codigo_curso FOREIGN KEY (codigo_curso) REFERENCES curso (codigo)
);
```

Management privileges:

```sql
CREATE USER 'janobourian'@'172.17.0.1' IDENTIFIED BY '123456';

GRANT ALL PRIVILEGES ON * . * TO 'janobourian'@'172.17.0.1';

FLUSH PRIVILEGES; 

SHOW GRANTS FOR 'janobourian'@'172.17.0.1';
```

Alter information, only examples:

```sql
ALTER TABLE carrera ADD PRIMARY KEY (codigo);

ALTER TABLE carrera CHANGE COLUMN codigo codigo TINYINT(2) AUTO_INCREMENT NOT NULL;

ALTER TABLE alumno CHANGE COLUMN codigo_carrera codigo_carrera TINYINT(2) NOT NULL;

ALTER TABLE carrera CHANGE codigo codigo TINYINT(2) NOT NULL AUTO_INCREMENT;

RENAME TABLE carrera TO ingenieria;

ALTER TABLE Usuario CHANGE COLUMN Edad FechaNacimiento DATE;

ALTER TABLE Usuario ADD COLUMN Sexo CHAR(10) NOT NULL; 

ALTER TABLE matricula ADD FOREIGN KEY (codigo_alumno) REFERENCES alumno(codigo);

ALTER TABLE alumno DROP FOREIGN KEY FK_codigo_carrera;

ALTER TABLE alumno ADD CONSTRAINT FK_codigo_carrera FOREIGN KEY (codigo_carrera) REFERENCES carrera (codigo) ON DELETE CASCADE ON UPDATE CASCADE;
```

Insert information by console:

```sql
INSERT INTO carrera (codigo, nombre) VALUES (NULL, "ingenieria de software");

INSERT INTO carrera VALUES (NULL, "informatica");

INSERT INTO alumno VALUES (NULL, "fernando", NULL, "vallejo", "caminos", "M", "1992-05-15", 1);

INSERT INTO alumno VALUES (NULL, "dario", "damian", "carlos", "andre", "M", "1999-05-15", 2);

INSERT INTO curso VALUES (NULL, "python", 8, 1, 1);

INSERT INTO curso VALUES (NULL, "cpp", 8, 1, 1);

INSERT INTO matricula VALUES (NULL, 1, 1, "2023-01-01");

INSERT INTO matricula VALUES (NULL, 1, 3, "2022-06-16");

INSERT INTO matricula VALUES (NULL, 3, 2, "2021-01-07");

```

<hr>

## Manipulation using SQL queries

For more information you can check **03_manipulacion**

```sql
SELECT

INSERT

UPDATE

DELETE

WHERE

IF

CASE - WHEN

BETWEEN

LIKE

IN

ALTER

IS NOT NULL

IS NULL

ORDER BY
```

<hr>

## Aditional Functions

<hr>

## Group Tables

<hr>

## Store Procedures, Funtioncs, Triggers, Index

<hr>

## Access and Backup

<hr>

## All sentences

```cmd
docker exec -it mysqlcontainer mysql -p
```

```sql
SHOW DATABASES;
CREATE DATABASE database_name;
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

