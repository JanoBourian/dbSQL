## SELECT

```sql
SELECT * 
    FROM <table_name>;

SELECT <column_name>, <column_name> 
    FROM <table_name>;
```

## INSERT

```sql
INSERT INTO <table_name> VALUES(NULL, 'value', 'value');

INSERT INTO <table_name> (<column_name>, <column_name>, <column_name>) VALUES(NULL, 'value', 'value');
```

## UPDATE

```sql
UPDATE <table_name> 
    SET <column_name> = <new_value>, 
        <column_name> = <new_value>, 
        <column_name> = <new_value> 
    WHERE id = 0;

UPDATE alumno 
    SET apellido_paterno = "jaimez" 
    WHERE codigo <> 8;
```

## DELETE

```sql
DELETE FROM matricula;

DELETE FROM <table_name> 
    WHERE <column> <> 'baja'; 
```

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

```sql
SELECT *
    FROM alumno
    WHERE fecha_nacimiento > "1992-07-01"
    AND apellido_paterno = "Quispe";
```

## Estructuras de control 

### IF

```sql
SELECT * 
    IF(calificacion >= 6, 'Aprobado', 'Reprobado') 
    AS Resultado 
    FROM alumno; 
```

### WHEN - CASE (many cases)

```sql
SELECT *
    CASE WHEN calificacion < 6 THEN 'Bajo'
         WHEN calificacion BETWEEN 6 AND 8 THEN 'Medio'
         WHEN calificacion >= 8 THEN 'Alto'
    END AS Categoria
    FROM curso; 
```

## BETWEEN

```sql
SELECT * 
    FROM alumno 
    WHERE FechaNacimiento BETWEEN '1990-01-01' AND '2000-12-31';
```

## LIKE

```sql
SELECT * 
    FROM curso 
    WHERE nombre LIKE '%ing%';

SELECT * 
    FROM curso 
    WHERE nombre LIKE '%ing';

SELECT * 
    FROM curso 
    WHERE nombre LIKE 'ing%';
```

## IN

```sql
SELECT * 
    FROM alumno
    WHERE apellido IN ('Sosa', 'Vega', 'Diaz');
```

## ALTER

```sql

ALTER TABLE <table_name> 
    ADD <column_name> <description> 
    AFTER <column_name>; 

ALTER TABLE alumno 
    ADD direccion VARCHAR(200) NULL 
    AFTER fecha_nacimiento;

ALTER TABLE Usuario 
    ADD sexo CHAR(10) NOT NULL;

ALTER TABLE Usuario 
    ADD COLUMN Sexo CHAR(10) NOT NULL;

ALTER TABLE matricula 
    ADD FOREIGN KEY (codigo_alumno) REFERENCES alumno(codigo);
``` 

## IS NOT NULL

```sql
SELECT * 
    FROM alumno 
    WHERE direccion IS NOT NULL; 
```

## IS NULL

```sql
SELECT * 
    FROM alumno 
    WHERE direccion IS NULL; 
```

## ORDER BY

```sql
SELECT * 
    FROM alumnos 
    ORDER BY creditos ASC 
    WHERE edad < 30 or edad > 40;

SELECT * 
    FROM alumnos 
    ORDER BY creditos DESC, promedio ASC
    WHERE edad < 30 or edad > 40;
```