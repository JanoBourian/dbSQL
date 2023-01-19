# PROCEDIMIENTOS ALMACENADOS

## Declaración del procedimiento

```sql
DELIMITER //
CREATE PROCEDURE prInsertar_Carrera()
BEGIN
    INSERT INTO  carrera(nombre) VALUES('Contabilidad')
END // 
DELIMITER; 
```

## Ejecución del procedimiento

```sql
CALL prInsertar_carrera(); 
```

## Eliminar procedimiento

```sql
DROP PROCEDURE prInsertar_Carrera; 

/*
IN: Variable de entrada para el procedimiento, que se utiliza dentro de este
OUT: Variable de salida del procedimiento que se actualiza al final de este
INOUT: Variable de entrada-salida del procedimiento almacenado
*/
```

## Con parámetro IN

```sql
DELIMITER //
CREATE PROCEDURE prInsertar_Carrera(IN NombreCarrera VARCHAR(50))
BEGIN
    INSERT INTO carrera(Nombre) VALUES(NombreCarrera); 
END //
DELIMITER; 
```

## Ejecutar procedimiento con parámetro

```sql
CALL prInsertar_Carrera('Logística');
CALL prInsertar_Carrera('Administración Pública');
CALL prInsertar_Carrera('Ciencias Comerciales');
```

# FUNCIONES

```sql
CREATE FUNCTION fnCubo(valor INT) RETURNS BIGINT 
    RETURN valor*valor*valor;
```

## Llamar la función 

```sql
SELECT fnCubo(7);
```

## Creación de función 

```sql
CREATE FUNCTION areaCirculo(Radio FLOAT) RETURNS FLOAT
    RETURN Radio*Radio*3.14159265359;
``` 

## Llamar la función 

```sql
SELECT areaCirculo(35.78) AS 'Area del círculo';
```

# TRIGGERS
## Se activa antes o después de ciertos eventos: inserción, actualización o eliminación

En este ejemplo no se permite que la cantidad de créditos insertados sea mayor a 15

```sql
DELIMITER //
CREATE TRIGGER trComprueba_Creditos BEFORE INSERT ON curso
    FOR EACH ROW BEGIN
        IF NEW.Creditos > 15 THEN
            SET NEW.Creditos = 15;
        END IF; 
    END; //
DELIMITER; 

INSERT INTO curso(Nombre, Creditos, CodigoCarrera) 
    VALUES ('Base del diseño web', 19, 1);

DROP TRIGGER teComprueba_Creditos; 
```

# RESTRICCIÓN UNIQUE

```sql
TRUNCATE alumno; 

--- Like UNIQUE whe you create the table
ALTER TABLE alumno
    ADD UNIQUE UQ_Alumno_DNI (DNI);


```

# VISTAS (for check only certain information, like a virtual table)

```sql
SELECT * FROM cursos; 

CREATE VIEW vwCurso_Nombre_Creditos AS
    SELECT Nombre, Creditos
    FROM curso
    ORDER BY Nombre ASC; 

SELECT * FROM vwCurso_Nombre_Creditos; 

DROP VIEW vwCurso_Nombre_Creditos; 
```

# ÍNDICES

```sql
CREATE INDEX ixAlumno_ApellidoPaterno ON alumno (ApellidoPaterno); 

ALTER TABLE alumno DROP INDEX ixAlumno_ApellidoPaterno;
```