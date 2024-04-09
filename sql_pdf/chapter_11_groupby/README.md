# GROUP BY and Aggregate Functions

## GROUP BY

The columns in GROUP BY must appear in SELECT statement. 

```sql
SELECT column1, column2, column3 
FROM tablename
WHERE condition1
GROUP BY column1, column2, column3
```

## AGGREGATE FUNCTIONS

- COUNT(*): include null, not null and duplicated
- COUNT(expression): not null values
- COUNT(DISTINCT expression): not null values

```sql
SELECT username, COUNT(contract_number)
FROM table1
GROUP BY username;
```