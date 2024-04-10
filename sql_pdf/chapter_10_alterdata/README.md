# Data Altering Commands

## UPDATE
```sql
UPDATE tablename1
SET column1
WHERE column1 IN (1, 2);

UPDATE temporal.clients
SET username = 'razek'
WHERE uuid_client = 'da300ec4-805b-44cd-80f6-7559474b9879';
```

## DELETE
```sql
DELETE FROM tablename1
WHERE uuid_client = 'da300ec4-805b-44cd-80f6-7559474b9879';
```

## CAST
```sql
SELECT CAST('2020-02-28 08:14:57' AS TIMESTAMP);
```
