# Pasos completos para construcción Básica

## Creación completa de la base de datos

### Creación de la base de datos
CREATE DATABASE gestor;

### Creación de las tablas
USE gestor;

SHOW TABLES gestor;

#### TipoUsuario
CREATE TABLE TipoUsuario(

    IDTipoUsuario INT AUTO_INCREMENT NOT NULL, 

    DescripcionUsuario VARCHAR(50) NOT NULL, 

    PRIMARY KEY (IDTipoUsuario)

);

#### Seccion 
CREATE TABLE Seccion(

    IDSeccion INT AUTO_INCREMENT NOT NULL, 

    DescripcionSeccion VARCHAR(200) NOT NULL,

    PRIMARY KEY (IDSeccion)

);

#### Area
CREATE TABLE Area(

    IDArea INT AUTO_INCREMENT NOT NULL, 

    NombreArea VARCHAR(50) UNIQUE NOT NULL, 

    DescripcionArea VARCHAR(21844) NOT NULL,

    PRIMARY KEY (IDArea)

);

#### TipoMovimiento
CREATE TABLE TipoMovimiento(

    IDTipoMovimiento INT AUTO_INCREMENT NOT NULL, 

    DescripcionMovimiento VARCHAR(50) NOT NULL,

    PRIMARY KEY (IDTipoMovimiento)

);

#### Usuario

CREATE TABLE Usuario(
    IDUsuario INT AUTO_INCREMENT NOT NULL, 
    IDTipoUsuario INT NOT NULL,
    IDSeccion INT NOT NULL, 
    NombreUsuario VARCHAR(50) UNIQUE NOT NULL, 
    Contrasena VARCHAR(50) NOT NULL,
    Correo VARCHAR(50) UNIQUE NOT NULL,  
    FechaCreacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    PRIMARY KEY (IDUsuario),
    CONSTRAINT FK_IDTipoUsuario FOREIGN KEY (IDTipoUsuario) REFERENCES TipoUsuario (IDTipoUsuario)
);

#### Movimiento

CREATE TABLE Movimiento(
    IDMovimiento INT AUTO_INCREMENT NOT NULL, 
    ID_Area INT NOT NULL, 
    ID_TipoMovimiento INT NOT NULL, 
    ID_Usuario INT NOT NULL,
    Descripcion VARCHAR(50) NOT NULL, 
    Monto DOUBLE NOT NULL, 
    FechaMovimiento TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    PRIMARY KEY (IDMovimiento),
    CONSTRAINT FK_IDArea FOREIGN KEY (ID_Area) REFERENCES Area (IDArea),
    CONSTRAINT FKIDTipoMovimiento FOREIGN KEY (ID_TipoMovimiento) REFERENCES TipoMovimiento (IDTipoMovimiento),
    CONSTRAINT FKIDUsuario FOREIGN KEY (ID_Usuario) REFERENCES Usuario (IDUsuario)
);

### Inserción de registros


### Creación de ROL


### Creación de Usuario


### Ingreso Con Usuario


### Ejecución de DELETE


### ROL Gestor


### Usuario con nuevo ROL

