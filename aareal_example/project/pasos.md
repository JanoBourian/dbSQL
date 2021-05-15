# Pasos completos para construcción Básica

## Creación completa de la base de datos

### Creación de la base de datos
CREATE DATABASE gestor;

### Creación de las tablas
USE gestor;
SHOW TABLES gestor;

#### TipoUsuario

CREATE TABLE TipoUsuario(
    ID INT AUTO_INCREMENT NOT NULL, 
    DescripcionUsuario VARCHAR(50) NOT NULL, 
    IndicadorEspecifico INT UNIQUE NOT_NULL,
    PRIMARY KEY (ID)
);



#### Movimientos


### Inserción de registros


### Creación de ROL


### Creación de Usuario


### Ingreso Con Usuario


### Ejecución de DELETE


### ROL Gestor


### Usuario con nuevo ROL

