# Funciones de Agregado

## Average (Promedio)
SELECT 
    AVG(calificaciones) AS 'Promedio'
    FROM curso; 

## Min
SELECT MIN(creditos) AS 'Menor Creditaje' FROM curso; 

## Max
SELECT MAX(creditos) AS 'Mayor Creditaje' FROM curso; 

## Sum
SELECT SUM(creditos) AS 'Suma de créditos' FROM curso; 

## Count
SELECT COUNT(*) AS 'Cantidad total' FROM curso; 

# Funciones Numéricas

## Redondeo de números 
### ROUND(value, positions)
SELECT ROUND(AVG(creditos), 0) AS 'Promedio' FROM cursos; 

### CEILING(value)
SELECT CEILING(AVG(creditos)) AS 'Ceiling' FROM cursos; 

### FLOOR(value)
SELECT FLOOR(AVG(creditos)) AS 'Floor' FROM cursos; 

### ABS(value)
SELECT FLOOR(AVG(creditos)) AS 'Abs' FROM cursos; 

### Aleatorio 
SELECT RAND();

SELECT RAND()*10;

SELECT CEILING(RAND()*10);

SELECT ROUND(20 + RAND()*80) AS 'Aleatorio';

### POW(base, exponent)
SELECT POW(5, 6);

### SQRT(base)
SELECT SQRT(15);

### MOD(dividendo, divisor)
SELECT MOD(10,3);

# Funciones de cadena o texto
SELECT UPPER(ApellidoPaterno) FROM estudiantes; 

SELECT LOWER(ApellidoPaterno) FROM estudiantes; 

## Concat
SELECT CONCAT(ApellidoMaterno , ' ', ApellidoPaterno, ' ', Nombres) AS 'Nombre completo' FROM alumno; 

## Tamanio
SELECT LENGTH( CONCAT(ApellidoMaterno , ' ', ApellidoPaterno, ' ', Nombres)) AS 'Longitud_nombre_compelto' FROM alumno; 

## TRIM()
SELECT TRIM('     este e     s un ej eeem plo   ');

SELECT LTRIM('     este e     s un ej eeem plo   ');

SELECT RTRIM('     este e     s un ej eeem plo   ');

## SUBSTR(<cadena>, <start_position>, <longe_sub>)
SELECT SUBSTR(Nombre, 1, 3) AS 'Silaba' from cursos; 

## INSTR(<columna>, <substring>) (IN STRING)
SELECT Nombre, INSTR(Nombre, 'ing') AS 'Position' FROM carrera; 

## LPAD(<column>, tamanio, value)
SELECT LPAD(Nombre, 100, '$') FROM alumno; 

## RPAD(<column>, tamanio, value)
SELECT RPAD(Nombre, 100, '$') FROM alumno; 

## REPLACE(<campo>, string_match, string_replace)
SELECT REPLACE(Nombre, 'ing', 'ING ***') FROM carrera; 

## REVERSE
SELECT REVERSE('MySQL');

## REPEAT
SELECT REPEAT('MySQL', 1000);

# FECHAS
SELECT CURDATE(), CURRENT_DATE(), CURTIME(), CURRENT_TIME();

SELECT NOW(), LOCALTIME(), CURRENT_TIMESTAMP();

## Extracciones
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

# Campos Calculados
SELECT Nombre, YEAR(CURDATE()) - YEAR(FechaNacimiento) AS edad
    FROM alumno
    ORDER BY Edad ASC;

# SUBCONSULTAS
SELECT Nombre, Creditos
    FROM curso 
    WHERE Creditos = (SELECT MIN(Creditos) FROM curso);

SELECT ApellidoPaterno, ApellidoMaterno, Nombre, Calificacion
    FROM alumno
    WHERE FechaNacimiento = (SELECT MAX(FechaNacimiento) FROM alumno);