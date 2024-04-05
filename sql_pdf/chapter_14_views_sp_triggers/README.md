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