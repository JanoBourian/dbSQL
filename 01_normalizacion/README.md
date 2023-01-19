# Normalización

## 1FN
- No debe ser necesario un orden alfabético
- Sin filas duplicadas
- Datos atómicos
- Siempre se debe tener una clave primaria
- Sin valores Nulos
- Un campo no debe tener más de un dato en su dominio de columna

## 2FN
- La tabla debe estar en 1FN
- Romper dependencias funcionales
- Identificar la dependencia entre los campos y la clave primaria 
- Todo atributo debe depender de toda la clave primaria
- Tabla fuerte y tabla débil

## 3FN
- La tabla debe estar en 2FN
- Ningún atributo no primario de la tabla debe tener una dependencia transitiva con una clave primaria.
- Eliminar dependencia multivaluada (Conjunto de registros independientes que están en un mismo registro)