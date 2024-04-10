# Setting Primary Keys and Foreign Keys

## PRIMARY KEY 

```sql
CREATE SCHEMA temporal;

CREATE TABLE IF NOT EXISTS temporal.clients(
    uuid_client UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    first_name VARCHAR,
    last_name VARCHAR,
    username VARCHAR,
    password_value VARCHAR,
    created_at TIMESTAMP DEFAULT now(),
    UNIQUE (username)
);

ALTER TABLE temporal.clients
ALTER COLUMN created_at SET DEFAULT now();

CREATE TABLE IF NOT EXISTS temporal.temporal_information(
	current_id SERIAL PRIMARY KEY,
	uuid_value UUID,
	score SMALLINT,
	created_at TIMESTAMP
);

SELECT *
FROM temporal.temporal_information;

INSERT INTO temporal.temporal_information(uuid_value, score, created_at)
VALUES (gen_random_uuid(), floor(random() * 5 + 1)::int, now());

ALTER TABLE temporal.temporal_information
DROP PRIMARY KEY;

ALTER TABLE temporal.temporal_information
ADD PRIMARY KEY (uuid_value);
```

## FOREIGN KEY

```sql
CREATE TABLE IF NOT EXISTS temporal.temporal_survey(
	current_id SERIAL PRIMARY KEY,
	uuid_client UUID,
	score SMALLINT,
	created_at TIMESTAMP DEFAULT now(),
    FOREIGN KEY (uuid_client) REFERENCES temporal.clients(uuid_client)
);

INSERT INTO temporal.temporal_survey(uuid_client, score)
VALUES ('ef00686a-67f9-498a-954e-69039a57a906', floor(random() * 5 + 1)::int);

SELECT cl.username, AVG(surv.score) AS total_score
FROM temporal.temporal_survey AS surv
INNER JOIN temporal.clients AS cl ON cl.uuid_client = surv.uuid_client
GROUP BY cl.username;
```

## Temporary tables

```sql
CREATE TEMPORARY TABLE;
DROP TEMPORARY TABLE;
```