# Views, Stored procedures and Triggers

## Views

```sql
CREATE OR REPLACE VIEW dbname.view_name AS
SELECT column1, column2, column3 
FROM dbname.table_name
WHERE column1 > any_value;
```

```sql
ALTER VIEW dbname.view_name AS
SELECT column1, column2, column3 
FROM dbname.table_name
WHERE column1 > any_value;
```

```sql
DROP VIEW dbname.view_name;
```

## Stored procedures

In MySQL
```sql
DELIMITER //

CREATE PROCEDURE sp_name(parameter_1 TYPE)

BEGIN
-- Code
END; 

DELIMITER;
```

In PostgreSQL
```sql
CREATE OR REPLACE PROCEDURE sp_name(parameter_1 TYPE)
AS
BEGIN
-- Code
END; 

```

Implementación
```sql
CREATE TABLE IF NOT EXISTS fake.income_by_city(
	id_value SERIAL PRIMARY KEY,
	latitude DOUBLE PRECISION,
	longitude DOUBLE PRECISION,
	income DOUBLE PRECISION,
	created_at TIMESTAMP
);

CREATE OR REPLACE PROCEDURE fake.sp_insert_data_income_by_city()
LANGUAGE plpgsql
AS $$
DECLARE
BEGIN
	INSERT INTO fake.income_by_city(
		latitude, longitude, income, created_at
	) VALUES (
		(21 + random() * 12)::DOUBLE PRECISION,
		(-117 + random() * 30)::DOUBLE PRECISION,
		(random() * 10 + 1)::DOUBLE PRECISION,
		'2023-08-01 00:00:00'
	);
END;
$$;

CALL fake.sp_insert_data_income_by_city();

SELECT *
FROM fake.income_by_city;

DROP TABLE fake.income_by_city;
```

## Loops

```sql
DO $$
	DECLARE
		val INTEGER = 0;
	BEGIN
		FOR counter in 1..6 LOOP
			val = val + counter;
			RAISE notice 'val: %', val;
	END LOOP;
END; $$
```

## Triggers

```sql
ALTER TABLE fake.income_by_city
ADD country VARCHAR(255);

CREATE OR REPLACE PROCEDURE fake.sp_income_by_city_updated()
LANGUAGE plpgsql
AS $$
DECLARE
BEGIN
	UPDATE fake.income_by_city
    SET updated_at = NOW();
END;
$$;

CREATE TRIGGER income_by_city_updated
BEFORE UPDATE
ON fake.income_by_city FOR EACH ROW
EXECUTE PROCEDURE fake.sp_income_by_city_updated();
```

