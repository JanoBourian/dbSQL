# Subqueries and nested queries

## Subqueries and nested queries

```sql
SELECT column1, column2, column 3
FROM table1 as tb1
WHERE tb1.column1 in (
    SELECT column1 
    FROM table2
    WHERE column2 > 50000
);
```