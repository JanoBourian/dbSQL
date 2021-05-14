# Creación de usuarios
CREATE USER 'usuario01'@'localhost' IDENTIFIED BY 'password1234';
CREATE USER 'usuario02'@'localhost' IDENTIFIED BY 'password1234';

GRANT ALL PRIVILEGES ON * . * TO 'usuario01'@'localhost';
FLUSH PRIVILEGES; 

GRANT INSERT ON * . * TO 'usuario02'@'localhost';
FLUSH PRIVILEGES; 

# Verificación de acceso
Aquí sólo se realiza la captura de los accesos


# Verificación de permisos
SHOW GRANTS FOR 'usuario01'@'localhost';
SHOW GRANTS FOR 'usuario02'@'localhost';


# Inserción de registros
GRANT INSERT ON * . * TO 'usuario02'@'localhost';
FLUSH PRIVILEGES; 
INSERT INTO Usuario VALUES(NULL, 'Usuario01', 'User', 'Prueba1', 'usuario01@mail.com', 'default', '1990-09-24', 'M');
INSERT INTO Usuario VALUES(NULL, 'Karla', 'Dominique', 'Arteaga', 'dakarla@mail.com', 'default', '1990-09-25', 'F');


# Creación de Rol
CREATE ROLE IF NOT EXISTS 'mi_rol';
GRANT SELECT ON es1821009465.* TO 'mi_rol';


# Relación de Rol y usuario
GRANT 'mi_rol' TO 'usuario02'@'localhost';


# Verificación de actualización de permisos
SHOW GRANTS FOR 'usuario02'@'localhost';