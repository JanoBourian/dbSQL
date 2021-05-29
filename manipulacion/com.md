## SELECT
SELECT * FROM <table_name>;

SELECT <column_name>, <column_name> FROM <table_name>;


## INSERT
INSERT INTO <table_name> VALUES(NULL, 'value', 'value');

INSERT INTO <table_name> (<column_name>, <column_name>, <column_name>) VALUES(NULL, 'value', 'value');

## UPDATE
UPDATE <table_name> SET <column_name> = <new_value>, <column_name> = <new_value>, <column_name> = <new_value> WHERE id = 0;

## DELETE
DELETE FROM <table_name> WHERE <column> <> 'baja'; 

## Operators

### Compairson
/*
= igual a
<> diferente a
< inferior o menor a 
> superior o mayor a
<= menor o igual a
>= mayor o igual a
*/

### Logic
/*
AND y 
OR o 

*/

## Estructuras de control 

### IF
SELECT * IF(calificacion >= 6, 'Aprobado', 'Reprobado') AS Resultado FROM alumno; 

### WHEN
SELECT *
    CASE WHEN calificacion < 6 THEN 'Bajo'
         WHEN calificacion BETWEEN 6 AND 8 THEN 'Medio'
         WHEN calificacion >= 8 THEN 'Alto'
    END AS Categoria
    FROM curso; 

## BETWEEN
SELECT * FROM alumno WHERE FechaNacimiento BETWEEN '1990-01-01' AND '2000-12-31';

# LIKE
SELECT * FROM curso WHERE nombre LIKE '%ing%';

SELECT * FROM curso WHERE nombre LIKE '%ing';

SELECT * FROM curso WHERE nombre LIKE 'ing%';

## IN
SELECT * FROM WHERE apellido IN ('Sosa', 'Vega', 'Diaz');

## ALTER
ALTER TABLE <table_name> ADD <column_name> <description> AFTER <column_name>; 

## IS NOT NULL
SELECT * FROM alumno WHERE direccion IS NOT NULL; 

## IS NULL
SELECT * FROM alumno WHERE direccion IS NULL; 

## ORDER BY
SELECT * 
    FROM alumnos 
    ORDER BY creditos ASC 
    WHERE edad < 30 or edad > 40;

SELECT * 
    FROM alumnos 
    ORDER BY creditos DESC, promedio ASC
    WHERE edad < 30 or edad > 40;