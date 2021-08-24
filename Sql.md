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

<p></p>



