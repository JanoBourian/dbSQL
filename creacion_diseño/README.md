# Crear la base de datos
CREATE DATABASE universidad; 

USE universidad; 


# Crear las tablas
## Tabla 1 carrera
CREATE TABLE carrera (

IDCarrera INT AUTO_INCREMENT NOT NULL,

CodigoCarrera INT UNIQUE NOT NULL, 

NombreCarrera VARCHAR(50) UNIQUE NOT NULL, 

PRIMARY KEY (IDCarrera)

);

## Tabla 2 alumnos
CREATE TABLE alumnos (

IDAlumno INT AUTO_INCREMENT NOT NULL, 

Nombre VARCHAR(50) NOT NULL, 

Paterno VARCHAR(50) NOT NULL, 

Materno VARCHAR(50) NOT NULL, 

SEXO CHAR(1) NOT NULL, 

CodigoCarrera INT NOT NULL, 

PRIMARY KEY (IDAlumno), 

CONSTRAINT FK_CodigoCarrera FOREIGN KEY (CodigoCarrera) REFERENCES carrera(CodigoCarrera)

);

## Tabla 3 curso
CREATE TABLE cursos (

IDCurso INT AUTO_INCREMENT NOT NULL, 

CodigoCurso INT UNIQUE NOT NULL, 

NombreCurso VARCHAR(50) UNIQUE NOT NULL, 

Creditos TINYINT(2) NOT NULL, 

CodigoCarrera INT NOT NULL, 

Estado TINYINT(1) NOT NULL, 

PRIMARY KEY (IDCurso),

CONSTRAINT FKCodigoCarrera FOREIGN KEY (CodigoCarrera) REFERENCES carrera(CodigoCarrera)

);

## Tabla 4 matriculas
CREATE TABLE matriculas (

IDMatricula INT AUTO_INCREMENT NOT NULL, 

Matricula VARCHAR(10) UNIQUE NOT NULL, 

Alumno INT NOT NULL, 

CodigoCurso INT NOT NULL, 

Fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,

PRIMARY KEY (IDMatricula), 

CONSTRAINT FK_Alumno FOREIGN KEY (Alumno) REFERENCES alumnos(IDAlumno),

CONSTRAINT FK_CodigoCurso FOREIGN KEY(CodigoCurso) REFERENCES carrera(CodigoCarrera)

);