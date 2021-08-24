# Introduction to SQL
<p>SQL, or Structured Query Language, is a language designed to allow both technical and non-technical users query, manipulate, and transform data from a relational database. And due to its simplicity, SQL databases provide safe and scalable storage for millions of websites and mobile applications.
</p>

---
# Relational Database

<p>A relational database is a type of database that stores and provides access to data points that are related to one another.
</p>

---

# Command-line Utilities in PostegreSQL

<p>With the help of the command-line utilities, we can directly execute the query from the command prompt, inserting, updating and various stuff can be handled by command line utilities.
</p>

| Command |  Result |
| :-: | :-: |
| \l  | enlisting the available database |
| \dt | enlisting the available tables in the current databse |
| \c databse_name | switching to another database |
| \d table_name | describing a particular table |
| \g | seeing the previously executed command |
| \? | enlisting all the available commands |
| \h syntax | knowing the syntaxes of PostgreSQL statements |
|  \timing | knowing the execution times of queries |
| \e | it opens the last executed query in a text editor |

---

# SQL Queries

## SELECT:
<p>To retrieve data from the SQL database, we need to write the select statements. Let's say the name of table in my database in mytable.</p>

1. To select every column from the database.

```sql
SELECT * FROM mytable;
```

2. To select specific column from the databse.

```sql
SELECT column1, column2 FROM mytable.
```

---
## Queries with constraints:
<p>Let's say if you have lots of row in your data and you want the rows based on the condition then we can use Where clause in the query</p>

```sql
SELECT column, another_column, …
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR …;
```
<p>Below are some useful operators that you can use for numerical data and string data in your query.</p>

| Operator | Condtion |
| :-: | :-: |
| =,!=,<,<=,>,>= | Standard numerical operators as well as used in string comparison |
| BETWEEN ... AND ... | Number is within range two values (inclusive)
| NOT BETWEEN ... AND ... | Number is not within range of two values |
| IN(...) | Number or String exits in a list |
| NOT IN(...) | Number or String does not exist in a list |
| LIKE | Case insensitive exact string comparison |
| NOT LIKE | 	Case insensitive exact string inequality comparison |
| % | Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE) |
| _ | 	Used anywhere in a string to match a single character (only with LIKE or NOT LIKE) |

---

## Unique rows:
<p>To discrad rows that have a duplicate column, we can use DISTINCT keyword in our SELECT query statement.</p>

```sql
SELECT DISTINCT column, another_column, …
FROM mytable
WHERE condition(s);
```

---
## Ordering results:
<p>To sort the columns in ascending or descending order, we can use order by clause in our query.</p>

```sql
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC;
```

---

## Limit and Offset:
<p>Limit and offset clauses which are used with the order by clause, is used to find the subset of the result. Limit clause can be used to to limit the number of rows in and offset can be used to specify where to begin counting the number rows from.</p>

```sql
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

---

## Practice SQL:
<p>All the above clauses and constraints, you can go to the following link and practice there.</p>

[Practice for sql](https://sqlbolt.com/)

---
# JOINS:
<p>A SQL Join statement is used to combine data or rows from two or more tables based on a common field between them. Different types of Joins are:</p>

* INNER JOIN
* LEFT JOIN
* RIGHT JOIN
* FULL JOIN

<p>Consider the two tables.</p>

1. Student

| ROLL_NO | NAME | ADDRESS | AGE |
| :-: | :-: | :-: | :-: |
| 1 | Harsh | Delhi | 18 |
| 2 | Pratik | Bihar | 19 |
| 3 | Riyanka | Siliguri | 20 |
| 4 | Deep | Ramnagar | 18 |
| 5 | Saptarhi | Kolkata | 19 |
| 6 | Dhanraj | Barabajar | 20 |
| 7 | Rohit | Balurghat | 18 |
| 8 | Niraj | Alipur | 19 |

2. StudentCourse

| COURSE_ID | ROLL_NO |
| :-: | :-: |
| 1 | 1 |
| 2 | 2 |
| 2 | 3 |
| 3 | 4 |
| 1 | 5 |
| 4 | 9 |
| 5 | 10 |
| 4 | 11 |

---

## INNER JOIN:
<p>The INNER JOIN keyword selects all rows from both the tables as long as the condition satisfies. This keyword will create the result-set by combining all rows from both the tables where the condition satisfies i.e value of the common field will be same.</p>

<p>Writing only JOIN in place of INNER JOIN is same.</p>

### Syntax:
```sql
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1 
INNER JOIN table2
ON table1.matching_column = table2.matching_column;


table1: First table.
table2: Second table
matching_column: Column common to both the tables.
```

### Example:
```sql
SELECT StudentCourse.COURSE_ID, Student.NAME, Student.AGE FROM Student
INNER JOIN StudentCourse
ON Student.ROLL_NO = StudentCourse.ROLL_NO;
```

### Result:

| COURSE_ID | NAME | AGE |
| :-: | :-: | :-: |
| 1 | Harsh | 18 |
| 2 | Pratik | 19 |
| 2 | Riyanka | 20 |
| 3 | Deep | 18 |
| 1 | Saptarhi | 19 |

---

## LEFT JOIN:
<p>This join returns all the rows of the table on the left side of the join and matching rows for the table on the right side of join. The rows for which there is no matching row on right side, the result-set will contain null. LEFT JOIN is also known as LEFT OUTER JOIN.
</p>

<p>Writing LEFT OUTER JOIN in place of LEFT JOIN is same.</p>

### Syntax:
```sql
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1 
LEFT JOIN table2
ON table1.matching_column = table2.matching_column;


table1: First table.
table2: Second table
matching_column: Column common to both the tables.
```

### Example:
```sql
SELECT Student.NAME,StudentCourse.COURSE_ID 
FROM Student
LEFT JOIN StudentCourse 
ON StudentCourse.ROLL_NO = Student.ROLL_NO;
```

### Result:

| NAME | COURSE_ID |
| :-: | :-: |
| Harsh | 1 |
| Pratik | 2 |
| Riyanka | 2 |
| Deep | 3 |
| Saptarhi | 1 |
| Dhanraj | NULL |
| Rohit | NULL |
| Niraj | NULL |

---

## RIGHT JOIN:
<p>RIGHT JOIN is similar to LEFT JOIN. This join returns all the rows of the table on the right side of the join and matching rows for the table on the left side of join. The rows for which there is no matching row on left side, the result-set will contain null. RIGHT JOIN is also known as RIGHT OUTER JOIN.
</p>

<p>Writing RIGHT OUTER JOIN is same as RIGHT JOIN.</p>

### Syntax:
```sql
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1 
RIGHT JOIN table2
ON table1.matching_column = table2.matching_column;


table1: First table.
table2: Second table
matching_column: Column common to both the tables.
```

### Example:
```sql
SELECT Student.NAME,StudentCourse.COURSE_ID 
FROM Student
RIGHT JOIN StudentCourse 
ON StudentCourse.ROLL_NO = Student.ROLL_NO;
```

### Result:

| NAME | COURSE_ID |
| :-: | :-: |
| Harsh | 1 |
| Pratik | 2 |
| Riyanka | 2 |
| Deep | 3 |
| Saptarhi | 1 |
| NULL | 4 |
| NULL | 5 |
| NULL | 4 |

---

## FULL JOIN:
<p>FULL JOIN creates the result-set by combining result of both LEFT JOIN and RIGHT JOIN. The result-set will contain all the rows from both the tables. The rows for which there is no matching, the result-set will contain NULL values.
</p>

<p>Wriring FULL OUTER JOIN is same as FULL JOIN.</p>

### Syntax:
```sql
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1 
FULL JOIN table2
ON table1.matching_column = table2.matching_column;


table1: First table.
table2: Second table
matching_column: Column common to both the tables.
```
### Example:
```sql
SELECT Student.NAME,StudentCourse.COURSE_ID 
FROM Student
FULL JOIN StudentCourse 
ON StudentCourse.ROLL_NO = Student.ROLL_NO;
```

### Result:

| NAME | COURSE_ID |
| :-: | :-: |
| Harsh | 1 |
| Pratik | 2 |
| Riyanka | 2 |
| Deep | 3 |
| Saptarhi | 1 |
| Dhanraj | NULL |
| Rohit | NULL |
| Niraj | NULL |
| NULL | 9 |
| NULL | 10 |
| NULL | 11 |

---

# AGGREGATIONS:
<p>SQL also supports the use of aggregate expressions (or functions) that allow you to summarize information about a group of rows of data. We can give an alias to our aggregate functions to easy read and process.</p>

### Syntax:
```sql
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, …
FROM mytable
WHERE constraint_expression;
```

## Common aggregate functions:

| Function | Description |
| :-: | :-: |
| COUNT(*), COUNT(column) | A common function used to counts the number of rows in the group if no column name is specified. Otherwise, count the number of rows in the group with non-NULL values in the specified column. |
| MIN(column) | Finds the smallest numerical value in the specified column for all rows in the group. |
| MAX(column) | Finds the largest numerical value in the specified column for all rows in the group. |
| AVG(column) | Finds the average numerical value in the specified column for all rows in the group. |
| SUM(column) | Finds the sum of all numerical values in the specified column for the rows in the group. |

---

<p>With the help of group by clause, we can instead apply the aggregate functions to individual groups of data within that group. The GROUP BY clause works by grouping rows that have the same value in the column specified.</p>

### Syntax:
```sql
SELECT AGG_FUNC(column_or_expression) AS aggregate_description, …
FROM mytable
WHERE constraint_expression
GROUP BY column;
```

<p>We have another clause which is HAVING clause, which is used specifically with the GROUP BY clause to allow us to filter grouped rows from the result set and aggregate function can't be 
used with the WHERE clause.</p>

### Example:

```sql
SELECT group_by_column, AGG_FUNC(column_expression) AS aggregate_result_alias, …
FROM mytable
WHERE condition
GROUP BY column
HAVING group_condition;
```

---
# Order of execution of query:

<p>Below is the complete SQL query.</p>

```sql
SELECT DISTINCT column, AGG_FUNC(column_or_expression), …
FROM mytable
    JOIN another_table
      ON mytable.column = another_table.column
    WHERE constraint_expression
    GROUP BY column
    HAVING constraint_expression
    ORDER BY column ASC/DESC
    LIMIT count OFFSET COUNT;
```

---
## Query order of execution.

1. FROM and JOIN's:
<p>The FROM clause, and subsequent JOINs are first executed to determine the total working set of data that is being queried. This includes subqueries in this clause, and can cause temporary tables to be created under the hood containing all the columns and rows of the tables being joined.
</p>

2. WHERE:
<p>Once we have the total working set of data, the first-pass WHERE constraints are applied to the individual rows, and rows that do not satisfy the constraint are discarded. Each of the constraints can only access columns directly from the tables requested in the FROM clause. Aliases in the SELECT part of the query are not accessible in most databases since they may include expressions dependent on parts of the query that have not yet executed.
</p>

3. GROUP BY:
<p>
The remaining rows after the WHERE constraints are applied are then grouped based on common values in the column specified in the GROUP BY clause. As a result of the grouping, there will only be as many rows as there are unique values in that column. Implicitly, this means that you should only need to use this when you have aggregate functions in your query.
</p>

4. HAVING:
<p>If the query has a GROUP BY clause, then the constraints in the HAVING clause are then applied to the grouped rows, discard the grouped rows that don't satisfy the constraint. Like the WHERE clause, aliases are also not accessible from this step in most databases.
</p>

5. SELECT:
<p>Any expressions in the SELECT part of the query are finally computed.
</p>

6. DISTINCT:
<p>Of the remaining rows, rows with duplicate values in the column marked as DISTINCT will be discarded.
</p>

7. ORDER BY:
<p>If an order is specified by the ORDER BY clause, the rows are then sorted by the specified data in either ascending or descending order. Since all the expressions in the SELECT part of the query have been computed, you can reference aliases in this clause.
</p>

8. LIMIT / OFFSET:
<p>Finally, the rows that fall outside the range specified by the LIMIT and OFFSET are discarded, leaving the final set of rows to be returned from the query.
</p>

---

# INSERTING NEW DATA:

<p>With the help of INSERT statement, we can insert one or more rows in our table.</p>

<p>Inserting in all columns, there is no need to specify the columns but the values should be in order according to columns.</p>

```sql
INSERT INTO mytable
VALUES (value_or_expr, another_value_or_expr, …),
       (value_or_expr_2, another_value_or_expr_2, …),
       …;
```

<p>Inserting in specific columns.</p>

```sql
INSERT INTO mytable
(column, another_column, …)
VALUES (value_or_expr, another_value_or_expr, …),
      (value_or_expr_2, another_value_or_expr_2, …),
      …;
```

---
# UPDATING DATA:
<p>With the help of UPDATE clause, we can update the value of columns based on the condition in WHERE clause.</p>

```sql
UPDATE mytable
SET column = value_or_expr, 
    other_column = another_value_or_expr, 
    …
WHERE condition;
```

---
# DELETING DATA:
<p>With the help of DELETE clause, we can delete data from the table based on condition. If we do not specify any condition then it will delete all the rows from the table.</p>

```sql
DELETE FROM mytable
WHERE condition;
```
---
# CREATING TABLES:
<p>With the help of CREATE TABLE statement, you can create a table in your database.</p>

```sql
CREATE TABLE IF NOT EXISTS mytable (
    column DataType TableConstraint DEFAULT default_value,
    another_column DataType TableConstraint DEFAULT default_value,
    …
);
```

<p>If there already exists a table with the same name, the SQL implementation will usually throw an error, so to suppress the error and skip creating a table if one exists, you can use the IF NOT EXISTS clause.</p>

## DATA TYPES:
* CHARACTER [(length)] or CHAR [(length)]
* VARCHAR (length)
* BOOLEAN
* SMALLINT
* INTEGER or INT
* DECIMAL [(p[,s])] or DEC [(p[,s])]
* NUMERIC [(p[,s])]
* REAL
* FLOAT(p)
* DOUBLE PRECISION
* DATE
* TIME
* TIMESTAMP
* CLOB [(length)] or CHARACTER LARGE OBJECT [(length)] or CHAR LARGE OBJECT [(length)]
* BLOB [(length)] or BINARY LARGE OBJECT [(length)]

### Example:
<p>Example schema movies table.</p>

```sql
CREATE TABLE movies (
    id INTEGER PRIMARY KEY,
    title TEXT,
    director TEXT,
    year INTEGER, 
    length_minutes INTEGER
);
```
---

# ALTERING TABLES:
<p>With the help of ALTER TABLE, we can add, remove, or modify columns and table constraints.</p>

## Adding columns:
```sql
ALTER TABLE mytable
ADD column DataType OptionalTableConstraint 
    DEFAULT default_value;
```

## Removing columns:
```sql
ALTER TABLE mytable
DROP column_to_be_deleted;
```

## Renaming the table:
```sql
Altering table name
ALTER TABLE mytable
RENAME TO new_table_name;
```

---
# DROPING TABLE:
<p>With the help of DROP TABLE statement, we can delete the whole table as well as its schema from database.
</p>

```sql
DROP TABLE IF EXISTS mytable;
```

---
# REFERENCES:
* https://sqlbolt.com/
* https://www.datacamp.com/community/tutorials/10-command-line-utilities-postgresql
* https://www.geeksforgeeks.org/sql-join-set-1-inner-left-right-and-full-joins/
* https://sqlbolt.com/lesson/select_queries_with_aggregates
* https://sqlbolt.com/lesson/select_queries_order_of_execution




