# Crear la base de datos
CREATE DATABASE ES1821009465;
USE ES1821009465;
SHOW TABLES;

# Crear todas las tablas
## Tabla Usuario
CREATE TABLE Usuario(
    IdUsuario INT AUTO_INCREMENT NOT NULL,
    Nombre VARCHAR(50) NOT NULL, 
    Apellido1 VARCHAR(50) NOT NULL, 
    Apellido2 VARCHAR(50) NOT NULL, 
    CorreoElectronico VARCHAR(20) NOT NULL, 
    Contrasena VARCHAR(50) NOT NULL,
    Edad TINYINT(2) NOT NULL,
    PRIMARY KEY (IdUsuario) 
);

## Tabla Post
CREATE TABLE Post(
    IdPost INT AUTO_INCREMENT NOT NULL, 
    ContenidoPost VARCHAR(21844) NOT NULL, 
    FechaCreacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    IDUsuario INT NOT NULL, 
    PRIMARY KEY (IdPost), 
    CONSTRAINT FK_IDUsuario FOREIGN KEY (IDUsuario) REFERENCES Usuario(IdUsuario)
);

## Tabla Comentario
CREATE TABLE Comentario(
    IdComentario INT AUTO_INCREMENT NOT NULL, 
    textoComentario VARCHAR(21844) NOT NULL, 
    fechaCreacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    IdPost INT NOT NULL, 
    IdUsuario INT NOT NULL, 
    PRIMARY KEY (IdComentario),
    CONSTRAINT FK_IdPost FOREIGN KEY (IdPost) REFERENCES Post(IdPost),
    CONSTRAINT FKIDUsuario FOREIGN KEY(IdUsuario) REFERENCES Usuario(IdUsuario)
);

## Tabla Sigue
CREATE TABLE Sigue(
    IdSigue INT AUTO_INCREMENT NOT NULL, 
    IdUsuario INT NOT NULL, 
    IdUsuarioAmigo INT NOT NULL, 
    fechaAmistad TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    PRIMARY KEY (IdSigue), 
    CONSTRAINT FoK_IdUsuario FOREIGN KEY (IdUsuario) REFERENCES Usuario(IdUsuario),
    CONSTRAINT FK_IdUsuarioAmigo FOREIGN KEY (IdUsuarioAmigo) REFERENCES Usuario(IdUsuario)
);

# Renombrar tablas
RENAME TABLE Sigue TO Amigo;

# Modificar Campo
ALTER TABLE Usuario CHANGE COLUMN Edad FechaNacimiento DATE;

# Agregar Campo
ALTER TABLE Usuario ADD COLUMN Sexo CHAR(10) NOT NULL; 


# Verificar Estado
CHECK TABLE Usuario; 

# Reparar Tablas
REPAIR TABLE Usuario; 

# Descripción de tablas
DESCRIBE Usuario;
DESCRIBE Post;
DESCRIBE Comentario; 
DESCRIBE Amigo;


