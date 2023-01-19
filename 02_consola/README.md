# Acceso desde consola
C:\xampp\mysql\bin 

C:\xampp\mysql\bin>mysql -u root -p

Enter password: 

# Docker container

docker exec -it mysqlcontainer mysql -p

Enter password: 

## Comandos 

### Miscelanea
SHOW DATABASES;

CREATE DATABASE database_name;

USE <db_name>; 

SHOW TABLES; 

DESCRIBE <table_name>;

### Básicas
CREATE DATABASE consola; 

CREATE TABLE usuarios (id_usuario INT AUTO_INCREMENT NOT NULL, nombre VARCHAR(100) UNIQUE NOT NULL, correo VARCHAR(50) UNIQUE NOT NULL, PRIMARY KEY (id_usuario) );


CREATE TABLE carrera (codigo TINYINT AUTO_INCREMENT NOT NULL, nombre VARCHAR(50) UNIQUE NOT NULL, PRIMARY KEY(codigo));

### Insertar
INSERT INTO <table_name> VALUES(null, 'master_user', 'mu@system.com');

INSERT INTO <table_name> (id_usuario, nombre) VALUES (null, 'rockstar'); 


### Modificar
UPDATE usuarios SET nombre = 'master' WHERE id_usuario = 1; 


### Seleccionar
SELECT * FROM usuarios; 

SELECT id_usuario, nombre FROM usuarios where id_usuario = 1; 

SELECT * FROM usuarios WHERE nombre LIKE '%m%';

SELECT * FROM usuarios ORDER BY correo ASC;

SELECT * FROM usuarios ORDER BY correo DESC;

SELECT * FROM usuarios LIMIT 100;

SELECT * FROM usuarios LIMIT 0, 2; --- desde el registro cero traeme dos valores

### Eliminar
DELET FROM usuarios WHERE id_usuario = 2; 

### Borrar tabla
DROP TABLE <table_name>