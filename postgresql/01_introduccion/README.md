# Introduction to Postgresql

For this course we are going to use a Docker container instead of use a database filed in our computer, ok, technically the database is inside our computer, but through docker. 

## Commands

* show config_file;

## Data types

* smallint -32768 
* integer
* bigint
* numeric
* decimal
* real
* double
* character varying(n)
* varchar(n)
* char(n)
* text(n)
* boolean
* date
* timestamp

## Create database

```sql
CREATE DATABASE store;
```

## Create tables

Create table directly:

```sql
CREATE TABLE persona3 (id serial primary key, name varchar(100), description text);
```

Create a table without primary key:

```sql
CREATE TABLE IF NOT EXISTS persona(id serial, name varchar(100), description text);

ALTER TABLE persona ADD PRIMARY KEY (id);
```

## Add columns

```sql
CREATE TABLE persona2(name varchar(100));

ALTER TABLE persona2 ADD id serial;

ALTER TABLE persona2 ADD PRIMARY KEY (id);
```

```sql
ALTER TABLE <table_name> ADD COLUMN <description>;

ALTER TABLE persona ADD COLUMN age integer;
```

## Rename and change column name

```sql
ALTER TABLE persona RENAME COLUMN age TO current_age; 

ALTER TABLE persona ALTER COLUMN current_age type varchar(100);

ALTER TABLE persona ALTER COLUMN current_age SET NOT NULL;

ALTER TABLE persona ALTER COLUMN name SET NOT NULL;

ALTER TABLE persona ALTER COLUMN description SET NOT NULL;

ALTER TABLE persona ALTER COLUMN description DROP NOT NULL;

ALTER TABLE persona DROP COLUMN current_age;
```

## Relationship

### One - Many

```sql
CREATE TABLE tarea (id serial primary key, nombre varchar(50) not null, idpersona integer references persona(id));
```

## Rename, change and delete table

```sql
CREATE TABLE IF NOT EXISTS persona(id serial primary key, name varchar(100), description text);

ALTER TABLE persona2 RENAME to tablapersona;

DROP TABLE persona2;

DROP TABLE persona3;
```

## Insert Information

```sql
CREATE TABLE prueba(id serial primary key, name varchar(100) not null, idtarea integer references tarea(id));

INSERT INTO persona(name, description, current_age) VALUES ('janobourian', 'optional description', 32);

INSERT INTO tarea(nombre, idpersona) VALUES ('Monterrey', 1);

SELECT * FROM persona;

SELECT * FROM tarea;

SELECT * FROM prueba;
```

## List objects inside a table

```sql
\l # List databases
\c <database_name>
\d <table_name>
\dt
\h
\h ALTER
\q 
\du 
```

```sql
ALTER USER myusername WITH PASSWORD 'mysecretpassword';
```