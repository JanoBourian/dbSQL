# Agrupamiento de tablas

SHOW DATABASES; 

## UNION
SELECT * FROM alumno
UNION 
SELECT * FROM alumno2; 

## UNION-ALL
SELECT * FROM alumno
UNION ALL
SELECT * FROM alumno2; 

# Consultas multitablas internar

# JOIN

SELECT * FROM 
alumno alu
INNER JOIN carrera carr 
ON alu.CodigoCarrera = carr.Codigo;

SELECT alu.ApellidoPaterno as 'Paterno', alu.Nombres as 'Nombres', carr.Carrera as 'Carrera' FROM 
alumno alu
INNER JOIN carrera carr 
ON alu.CodigoCarrera = carr.Codigo
where alu.Matricula = '209983' and carr.Creditos = 8;

# LEFT-JOIN
#### Coincidencias y toda la tabla de la izquierda

SELECT alu.ApellidoPaterno as 'Paterno', alu.Nombres as 'Nombres', mat.Fecha as 'Fecha de Matricula'
alumno alu
LEFT JOIN matricula mat
ON alu.Codigo = mat.Matricula;

SELECT alu.ApellidoPaterno as 'Paterno', alu.Nombres as 'Nombres', mat.Fecha as 'Fecha de Matricula'
alumno alu
LEFT JOIN matricula mat
ON alu.Codigo = mat.Matricula
WHERE mat.CodigoAlumno IS NULL;

# RIGHT-JOIN
#### Coincidencias y toda la tabla de la derecha

SELECT alu.ApellidoPaterno as 'Paterno', alu.Nombres as 'Nombres', mat.Fecha as 'Fecha de Matricula'
alumno alu
RIGHT JOIN matricula mat
ON alu.Codigo = mat.Matricula;

# GROUP BY
SELECT COUNT(*) FROM alumno
WHERE CodigoCarrera = 1; 

SELECT car.Nombre, COUNT(alu.Codigo) AS 'Cantidad de Alumnos'
FROM Carrera car 
JOIN Alumno alu ON car.Codigo = alu.CodigoCarrera
GROUP BY car.Nombre; 

# HAVING
SELECT car.Nombre, COUNT(alu.Codigo) AS Cantidad
FROM Carrera car 
JOIN Alumno alu ON car.Codigo = alu.CodigoCarrera
GROUP BY car.Nombre
HAVING Cantidad > 3; 

# DISTINCT

SELECT COUNT(DISTINCT(CodigoAlumno)) FROM matricula; 

