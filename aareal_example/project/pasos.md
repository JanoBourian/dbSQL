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
#### TipoUsuario
INSERT INTO TipoUsuario VALUES(NULL, 'Delegada');

INSERT INTO TipoUsuario VALUES(NULL, 'Ayudante');

INSERT INTO TipoUsuario VALUES(NULL, 'Presidente');

SELECT * FROM TipoUsuario; 

#### Seccion 
INSERT INTO Seccion VALUES(NULL, 'Delegacion');

INSERT INTO Seccion VALUES(NULL, 'COPACI');

INSERT INTO Seccion VALUES(NULL, 'Ayuda Externa');

SELECT * FROM Seccion;

#### Area
INSERT INTO Area VALUES(NULL, 'Salon de fiestas', 'Salon de fiestas para diversos eventos');

INSERT INTO Area VALUES(NULL, 'Parque', 'Area de canchas');

INSERT INTO Area VALUES(NULL, 'Gastos Plataforma', 'Tecnologia e IT');

SELECT * FROM Area;

#### TipoMovimiento
INSERT INTO TipoMovimiento VALUES(NULL, 'Ingreso' );

INSERT INTO TipoMovimiento VALUES(NULL, 'Egreso' );

SELECT * FROM TipoMovimiento; 

#### Usuario
INSERT INTO Usuario VALUES(NULL, 1, 1, 'Alejandra Villanueva', 'password', 'alejandrav@delegacion.com', NULL);

INSERT INTO Usuario VALUES(NULL, 3, 2, 'Salvador Vallejo', 'password', 'salvadorv@copaci.com', NULL);

INSERT INTO Usuario VALUES(NULL, 2, 3, 'Francisco Gonzalez', 'password', 'fgonzaleza@master.com', NULL);

SELECT * FROM Usuario; 

#### Movimiento
INSERT INTO Movimiento VALUES(NULL, 1, 1, 1, 'Pago de fiesta infantil', 1500.00, NULL);

INSERT INTO Movimiento VALUES(NULL, 1, 2, 1, 'Limpieza salon', 150.00, NULL);

INSERT INTO Movimiento VALUES(NULL, 3, 2, 3, 'Diseno de base de datos', 1000.00, NULL);

SELECT * FROM Movimiento; 

### Creación de ROL
CREATE ROLE IF NOT EXISTS 'capturista';

GRANT SELECT, INSERT ON gestor.* TO 'capturista';

### Creación de Usuario
CREATE USER 'capturista01'@'localhost' IDENTIFIED BY 'password1234';

GRANT 'capturista' TO 'capturista01'@'localhost';

### Ingreso Con Usuario
Aquí sólo se realiza la captura de datos

### Ejecución de DELETE
DELETE FROM Usuario where IDUsuario = 1;

### ROL Gestor
CREATE ROLE IF NOT EXISTS 'gestion';

GRANT ALL PRIVILEGES ON gestor.* TO 'gestion';

### Usuario con nuevo ROL
CREATE USER 'gestor01'@'localhost' IDENTIFIED BY 'password1234';

GRANT 'gestion' TO 'gestor01'@'localhost';
