# Control flow tools

## Case statement

```sql
CASE value
WHEN value_1 THEN result_1
WHEN value_2 THEN result_2
ELSE else_result
END;
```

```sql
SELECT table_alias.column1, table_alias.column2,
    CASE table_alias.column3
    WHEN value_1 THEN result_1
    WHEN value_2 THEN result_2
    ELSE else_result
    END AS new_column_name
FROM table.tablename AS table_alias;
```

## IF Function