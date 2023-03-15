# Agrupamiento de tablas

```sql
SHOW DATABASES; 
```

## UNION (Convert two tables in one, without repetition)

```sql
SELECT * FROM alumno
UNION 
SELECT * FROM alumno2; 
```

## UNION-ALL (Convert two tables in one, with repetition)

```sql
SELECT * FROM alumno
UNION ALL
SELECT * FROM alumno2; 
```

# Consultas multitablas internar

# JOIN (Y operator)

```sql
SELECT *
    FROM TableA a
    INNER JOIN Tableb b
    ON a.Key = b.Key;

SELECT * 
    FROM  alumno alu
    JOIN carrera car 
    ON alu.codigo_carrera = car.codigo;

SELECT * 
    FROM  alumno alu
    INNER JOIN carrera carr 
    ON alu.CodigoCarrera = carr.Codigo;

SELECT alu.ApellidoPaterno as 'Paterno', alu.Nombres as 'Nombres', carr.Carrera as 'Carrera' 
    FROM alumno alu
    INNER JOIN carrera carr 
    ON alu.CodigoCarrera = carr.Codigo
    where alu.Matricula = '209983' and carr.Creditos = 8;
```

# LEFT-JOIN
#### Coincidencias y toda la tabla de la izquierda

```sql
--- All inside left table
SELECT alu.ApellidoPaterno as 'Paterno', alu.Nombres as 'Nombres', mat.Fecha as 'Fecha de Matricula'
    FROM alumno alu --Left table
    LEFT JOIN matricula mat --Right table
    ON alu.Codigo = mat.Matricula;

--- All table left but withoun union
SELECT alu.ApellidoPaterno as 'Paterno', alu.Nombres as 'Nombres', mat.Fecha as 'Fecha de Matricula'
    FROM alumno alu -- left table
    LEFT JOIN matricula mat -- right table
    ON alu.Codigo = mat.Matricula
    WHERE mat.CodigoAlumno IS NULL;
```

# RIGHT-JOIN
#### Coincidencias y toda la tabla de la derecha

```sql
SELECT *
    FROM matricula mat
    RIGHT JOIN curso cu
    ON mat.codigo_curso = cu.codigo
    WHERE mat.codigo_curso IS NULL
    AND cu.nombre LIKE "%gia";

SELECT alu.ApellidoPaterno as 'Paterno', alu.Nombres as 'Nombres', mat.Fecha as 'Fecha de Matricula'
    FROM alumno alu
    RIGHT JOIN matricula mat
    ON alu.Codigo = mat.Matricula;
```

# GROUP BY

```sql
SELECT COUNT(*) 
    FROM alumno
    WHERE CodigoCarrera = 1; 

SELECT car.Nombre, COUNT(alu.Codigo) AS 'Cantidad de Alumnos'
    FROM Carrera car 
    JOIN Alumno alu 
    ON car.Codigo = alu.CodigoCarrera
    GROUP BY car.Nombre; 
```

# HAVING (only with GROUP BY)

```sql
SELECT car.Nombre, COUNT(alu.Codigo) AS Cantidad
    FROM Carrera car 
    JOIN Alumno alu 
    ON car.Codigo = alu.CodigoCarrera
    GROUP BY car.Nombre
    HAVING Cantidad > 3; 
```

# DISTINCT (take without repetitions o distinct)

```sql
SELECT COUNT(DISTINCT(CodigoAlumno)) FROM matricula; 
```
