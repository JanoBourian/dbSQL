# The SELECT statement


```sql
SELECT *
FROM tablename1;
```

```sql
SELECT *
FROM tablename1
ORDER BY column1
LIMIT 3;
```

```sql
SELECT column1, column2
FROM tablename1
ORDER BY column1
LIMIT 3;
```

## SELECT DISTINCT

```sql
SELECT DISTINCT(column1), COUNT(column1)
FROM tablename1
GROUP BY DISCOUNT(column1);

SELECT DISTINCT(column1) AS current_value, COUNT(column1)
FROM tablename1
GROUP BY current_value
ORDER BY current_value ASC;
```

## WHERE CONDITION

```sql
SELECT DISTINCT(column1) AS current_value, COUNT(column1), column2
FROM tablename1
WHERE column1 >= 3 
AND column2 > '2023-01-01 00:00:00'
GROUP BY current_value, column2
ORDER BY column1 ASC;
```

## HAVING

```sql
SELECT DISTINCT(column1) AS current_value, COUNT(column1), column2
FROM tablename1
GROUP BY current_value, column2
HAVING column1 >= 3 
AND column2 > '2023-01-01 00:00:00'
ORDER BY column1 ASC;
```

## BETWEEN AND NOT BETWEEN

```sql
SELECT *
FROM tablename1
WHERE column1 BETWEEN '2023-02-11' AND '2024-04-10';
```

## LIKE

```sql
SELECT *
FROM tablename1
WHERE column1 LIKE '%ad%';
```

## IN

```sql
SELECT column1, COUNT(column1)
FROM tablename1
WHERE user_id IN (1773)
GROUP BY column1;
```

## NOT

```sql
SELECT column1, COUNT(column1)
FROM tablename1
WHERE user_id NOT IN (1773)
GROUP BY column1;
```

## IS NULL

```sql
SELECT *
FROM tablename1
WHERE column1 IS NULL;

SELECT *
FROM tablename1
WHERE column1 IS NOT NULL;
```