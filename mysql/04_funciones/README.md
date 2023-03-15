# Funciones de Agregado

## Average (Promedio)

```sql
SELECT 
    AVG(calificaciones) AS 'Promedio'
    FROM curso; 
```

## Min

```sql
SELECT MIN(creditos) AS 'Menor Creditaje' FROM curso; 
```

## Max

```sql
SELECT MAX(creditos) AS 'Mayor Creditaje' FROM curso; 
```

## Sum

```sql
SELECT SUM(creditos) AS 'Suma de créditos' FROM curso; 
```

## Count

```sql
SELECT COUNT(*) AS 'Cantidad total' FROM curso; 
```

# Funciones Numéricas

## Redondeo de números 

### ROUND(value, positions)

```sql
SELECT ROUND(AVG(creditos), 0) AS 'Promedio' FROM cursos; 
```

### CEILING(value)

```sql
SELECT CEILING(AVG(creditos)) AS 'Ceiling' FROM cursos; 
```

### FLOOR(value)

```sql
SELECT FLOOR(AVG(creditos)) AS 'Floor' FROM cursos; 
```

### ABS(value)

```sql
SELECT FLOOR(AVG(creditos)) AS 'Abs' FROM cursos; 
```

### Aleatorio 

```sql
SELECT RAND();

SELECT RAND()*10;

SELECT CEILING(RAND()*10);

SELECT ROUND(20 + RAND()*80) AS 'Aleatorio';
```

### POW(base, exponent)

```sql
SELECT POW(5, 6);
```

### SQRT(base)

```sql
SELECT SQRT(15);
```

### MOD(dividendo, divisor)

```sql
SELECT MOD(10,3);
```

# Funciones de cadena o texto

```sql
SELECT UPPER(ApellidoPaterno) FROM estudiantes; 

SELECT LOWER(ApellidoPaterno) FROM estudiantes; 
```

## Concat

```sql
SELECT CONCAT(ApellidoMaterno , ' ', ApellidoPaterno, ' ', Nombres) AS 'Nombre completo' FROM alumno; 
```

## Tamanio

```sql
SELECT LENGTH( CONCAT(ApellidoMaterno , ' ', ApellidoPaterno, ' ', Nombres)) AS 'Longitud_nombre_compelto' FROM alumno; 
```

## TRIM()

```sql
SELECT TRIM('     este e     s un ej eeem plo   ');

SELECT LTRIM('     este e     s un ej eeem plo   ');

SELECT RTRIM('     este e     s un ej eeem plo   ');
```

## SUBSTR(<cadena>, <start_position>, <longe_sub>)

```sql
SELECT SUBSTR(Nombre, 1, 3) AS 'Silaba' from cursos; 
```

## INSTR(<columna>, <substring>) (IN STRING)

```sql
SELECT Nombre, INSTR(Nombre, 'ing') AS 'Position' FROM carrera; 
```

## LPAD(<column>, tamanio, value)

```sql
SELECT LPAD(Nombre, 100, '$') FROM alumno; 
```

## RPAD(<column>, tamanio, value)

```sql
SELECT RPAD(Nombre, 100, '$') FROM alumno; 
```

## REPLACE(<campo>, string_match, string_replace)

```sql
SELECT REPLACE(Nombre, 'ing', 'ING ***') FROM carrera; 
```

## REVERSE

```sql
SELECT REVERSE('MySQL');
```

## REPEAT

```sql
SELECT REPEAT('MySQL', 1000);
```

# FECHAS

```sql
SELECT CURDATE(), CURRENT_DATE(), CURTIME(), CURRENT_TIME();

SELECT NOW(), LOCALTIME(), CURRENT_TIMESTAMP();
```

## Extracciones

```sql
SELECT NOW() AS Fecha_Hora, DATE(NOW()) AS Solo_Fecha;

SELECT CURRENT_TIMESTAMP() AS Fecha_Hora, YEAR(CURRENT_TIMESTAMP()) AS Solo_Anio;

SELECT ABS( DATEDIFF('1990-09-19', DATE(NOW()))) AS Diferencia_Dias;

SELECT ABS( DATEDIFF('2011-05-18', DATE(NOW()))) AS Diferencia_Dias;

SELECT DATE_ADD(DATE(NOW()), INTERVAL 15 DAY) AS En_15;

/* FOR INTERVAL
SECOND
MINUTE
HOUR
DAY
WEEK
MONTH
YEAR
*/

SELECT TIME(NOW()) AS Hora_ACTUAL, ADDTIME(TIME(NOW()), '01:17:22') AS Hora_Futura;

SELECT DATE_SUB('2017-07-21', INTERVAL 37 MONTH) AS Fecha_anterior;

SELECT SUBTIME(TIME(NOW()),'04:23:19') AS Fecha_antes;
```

# Campos Calculados

```sql
SELECT Nombre, YEAR(CURDATE()) - YEAR(FechaNacimiento) AS edad
    FROM alumno
    ORDER BY Edad ASC;
```

# SUBCONSULTAS

```sql
SELECT Nombre, Creditos
    FROM curso 
    WHERE Creditos = (SELECT MIN(Creditos) FROM curso);

SELECT ApellidoPaterno, ApellidoMaterno, Nombre, Calificacion
    FROM alumno
    WHERE FechaNacimiento = (SELECT MAX(FechaNacimiento) FROM alumno);
```