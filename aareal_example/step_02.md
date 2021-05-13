# Comenzar a trabajar con la tabla 
SHOW DATABASES;
USE ES1821009465;
SHOW TABLES;

# Inserciones
## Inserción de 5 usuarios
INSERT INTO Usuario VALUES(NULL, 'Francisco', 'Gonzalez', 'Antonio', 'seissixer@nube.unadmexico.mx', 'default', '1990-09-19', 'M');

INSERT INTO Usuario VALUES(NULL, 'Abelardo', 'Sanchez', 'Urrutia', 'abelardo@mail.com', 'default', '1990-09-20', 'M');

INSERT INTO Usuario VALUES(NULL, 'Pedro', 'Rivaz', 'Gómez', 'pedror@mail.com', 'default', '1990-09-21', 'M');

INSERT INTO Usuario VALUES(NULL, 'Martha', 'Malverde', 'Ruiz', 'mmruiz@mail.com', 'default', '1990-09-22', 'F');

INSERT INTO Usuario VALUES(NULL, 'Fernando', 'Vallejo', 'Mattus', 'fvallejo@mail.com', 'default', '1990-09-23', 'M');

## Inserción de 2 post por usuario
INSERT INTO Post VALUES(null, 'Francisco01', null, 1);

INSERT INTO Post VALUES(null, 'Francisco02', null, 1);

INSERT INTO Post VALUES(null, 'Abelardo01', null, 2);

INSERT INTO Post VALUES(null, 'Abelardo02', null, 2);

INSERT INTO Post VALUES(null, 'Pedro01', null, 3);

INSERT INTO Post VALUES(null, 'Pedro02', null, 3);

INSERT INTO Post VALUES(null, 'Martha01', null, 4);

INSERT INTO Post VALUES(null, 'Martha02', null, 4);

INSERT INTO Post VALUES(null, 'Fernando01', null, 5);

INSERT INTO Post VALUES(null, 'Fernando02', null, 5);

## Inserción de 5 registros en la tabla comentario
INSERT INTO Comentario VALUES(null, 'Comentario01', null, 1, 5);

INSERT INTO Comentario VALUES(null, 'Comentario02', null, 3, 4);

INSERT INTO Comentario VALUES(null, 'Comentario03', null, 5, 1);

INSERT INTO Comentario VALUES(null, 'Comentario04', null, 7, 3);

INSERT INTO Comentario VALUES(null, 'Comentario05', null, 9, 2);


## Inserción de 3 registros en la tabla amigo
INSERT INTO Amigo VALUES(null, 1, 3, null);

INSERT INTO Amigo VALUES(null, 2, 4, null);

INSERT INTO Amigo VALUES(null, 5, 1, null);

# Consultas
## Selección de lista de usuarios
SELECT Nombre, Apellido1, Apellido2, CorreoElectronico, FechaNacimiento FROM Usuario;

## Selección por grupo
SELECT * FROM Usuario GROUP BY Sexo;

## Selección con varias columnas

SELECT p.IDUsuario, u.Nombre, u.Apellido1, u.Apellido2, p.ContenidoPost, c.TextoComentario, p.FechaCreacion
FROM Post p, Usuario u, Comentario c
WHERE p.IDUsuario = u.IdUsuario;

## Subconsulta con eliminación 
DELETE FROM Comentario WHERE IdUsuario = 1;
SELECT * FROM Comentario; 


## Mostrar comentarios
SELECT IdUsuario, fechaCreacion, COUNT(IdUsuario) FROM Comentario WHERE IdUsuario = 2 GROUP BY fechaCreacion;

## Actualización 
UPDATE Amigo SET fechaAmistad = now() where idSigue = 5;

## Seleccionar último elemento registrado
SELECT * FROM Amigo ORDER BY IdSigue DESC LIMIT 1;

## Seleccionar con edad
SELECT Nombre, TIMESTAMPDIFF(YEAR, FechaNacimiento, CURDATE()) AS edad FROM usuario;

## Actualización de un item
UPDATE Usuario SET CorreoElectronico = 'mail4you@mail.sayto' where IdUsuario = 1;

