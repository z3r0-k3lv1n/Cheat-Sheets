# SQL Cheat Sheet: Essential SQL Queries

## Retrieving Data

### SELECT
```sql
SELECT column1, column2
FROM table_name;
```

### SELECT with WHERE
```sql
SELECT column1, column2
FROM table_name
WHERE condition;
```

### DISTINCT
```sql
SELECT DISTINCT column1
FROM table_name;
```

### LIMIT
```sql
SELECT column1, column2
FROM table_name
LIMIT n;
```

## Sorting Data
---

### ORDER BY
```sql
SELECT column1, column2
FROM table_name
ORDER BY column1 ASC/DESC;
```

## Filtering Data
---

### WHERE
```sql
SELECT column1, column2
FROM table_name
WHERE condition;
```

### AND/OR
```sql
SELECT column1, column2
FROM table_name
WHERE condition1
AND/OR condition2;
```

### IN
```sql
SELECT column1, column2
FROM table_name
WHERE column1 IN (value1, value2);
```

## Aggregating Data
---

### COUNT
```sql
SELECT COUNT(column1)
FROM table_name;
```

### SUM
```sql
SELECT SUM(column1)
FROM table_name;
```

### AVG
```sql
SELECT AVG(column1)
FROM table_name;
```

### MAX
```sql
SELECT MAX(column1)
FROM table_name;
```

### MIN
```sql
SELECT MIN(column1)
FROM table_name;
```

## Joining Tables
---

### INNER JOIN
```sql
SELECT column1, column2
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### LEFT JOIN
```sql
SELECT column1, column2
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

### RIGHT JOIN
```sql
SELECT column1, column2
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

## Grouping Data
---

### GROUP BY
```sql
SELECT column1, COUNT(column2)
FROM table_name
GROUP BY column1;
```

## Subqueries
---

### Subquery in WHERE
```sql
SELECT column1, column2
FROM table_name
WHERE column1 = (SELECT column1 FROM another_table WHERE condition);
```

### Subquery in FROM
```sql
SELECT column1, subquery_result
FROM table_name
JOIN (SELECT column1, COUNT(*) as subquery_result FROM another_table GROUP BY column1) AS subquery_table
ON table_name.column1 = subquery_table.column1;
```

## Updating Data
---

### UPDATE
```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

## Deleting Data
---

### DELETE
```sql
DELETE FROM table_name
WHERE condition;
```

## Creating and Altering Tables
---

### CREATE TABLE
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);
```

### ALTER TABLE
```sql
ALTER TABLE table_name
ADD column_name datatype;
```

## Indexing
---

### CREATE INDEX
```sql
CREATE INDEX index_name
ON table_name (column);
```

## Removing Duplicates
---

### Removing Duplicates
```sql
SELECT DISTINCT column1, column2
FROM table_name;
```

## Conditional Logic
---

### CASE
```sql
SELECT column1,
       CASE
           WHEN condition1 THEN result1
           WHEN condition2 THEN result2
           ELSE result
       END AS new_column
FROM table_name;
```

Feel free to create a pull request and customize and format this cheat sheet according to your preferences.
