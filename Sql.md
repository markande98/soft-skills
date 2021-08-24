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
# Important concepts in SQL:

## ACID properties:

* Atomicity
* Consistency
* Isolation
* Durability

### Atomicity:
<p>A transaction is an atomic unit; hence, all the instructions within a transaction will successfully execute, or none of them will execute. The following transaction transfers 20 dollars from Alice’s bank account to Bob’s bank account. If any of the instructions fail, the entire transaction should abort and rollback.
</p>

| T1 |
| :-: |
| Read(A_bal) |
| A_bal -= 20 |
| Write(A_bal) |
| Read(B_bal) |
| B_bal += 20 |
| Write(B_bal) |

```
A transaction to transfer 20 pounds from Alice's account to Bob's account.
```

### Consistency:
<p>A database is initially in a consistent state, and it should remain consistent after every transaction. Suppose that the transaction in the previous example fails after Write(A_b) and the transaction is not rolled back; then, the database will be inconsistent as the sum of Alice and Bob’s money, after the transaction, will not be equal to the amount of money they had before the transaction.
</p>

### Isolation:
<p>If the multiple transactions are running concurrently, they should not be affected by each other; i.e., the result should be the same as the result obtained if the transactions were running sequentially. Suppose B_bal is initially 100. If a context switch occurs after B_bal *= 20, then the changes should only be visible to T2 once T1 commits. This ensures consistency in the data and prevents incorrect results.
</p>

| T1 | T2 |
| :-: | :-: |   
| Read(B_bal) | Read(B_bal) |
| B_bal *= 0.2 | B_bal += 20 |
| Write(B_bal) | Write(B_bal) |

```
T1 adds 20% interest to Bob's savings account and T2 adds 20 pounds to Bob's account.
```

### Durability:
<p>Changes that have been committed to the database should remain even in the case of software and system failure. For instance, if Bob’s account contains $120, this information should not disappear upon system or software failure.
</p>

---
## CAP Theorem:
<p>The CAP theorem (also called Brewer’s theorem) states that a distributed database system can only guarantee two out of these three characteristics: Consistency, Availability, and Partition Tolerance.
</p>

![CAP](https://www.educative.io/cdn-cgi/image/f=auto,fit=contain,w=3000/api/edpresso/shot/6661082609352704/image/5676830073815040.png)

### Consistency:
<p>A system is said to be consistent if all nodes see the same data at the same time.

Simply, if we perform a read operation on a consistent system, it should return the value of the most recent write operation. This means that, the read should cause all nodes to return the same data, i.e., the value of the most recent write.
</p>

### Availability:
<p>Availability in a distributed system ensures that the system remains operational 100% of the time. Every request gets a (non-error) response regardless of the individual state of a node.
</p>

### Partial Tolerance:
<p>
This condition states that the system does not fail, regardless of if messages are dropped or delayed between nodes in a system.

Partition tolerance has become more of a necessity than an option in distributed systems. It is made possible by sufficiently replicating records across combinations of nodes and networks.
</p>

---

## Normalization:
<p>It is the process of reducing the redundancy of data in the data table and improving data integrity.</p>

<p>There are various normal forms which helps us to normalizes the table</p>

* 1st Normal Form (1NF)
* 2nd Normal Form (2NF)
* 3rd Normal Form (3NF)
* Boyce-Codd Normal Form (BCNF)

### 1NF:
<p>In this Normal Form, we tackle the problem of atomicity. Here atomicity means values in the table should not be further divided. In simple terms, a single cell cannot hold multiple values. If a table contains a composite or multi-valued attribute, it violates the First Normal Form.</p>

### 2NF:
<p>First it has to be in 1NF and should not contain any partial dependency. Here partial dependency means the proper subset of candidate key determines a non-prime attribute. 
</p>

### 3NF:
<p>Same here, first it has to be in the 2NF. The other condition is there should be no transitive dependency for non-prime attributes. That means non-prime attributes (which doesn’t form a candidate key) should not be dependent on other non-prime attributes in a given table. So a transitive dependency is a functional dependency in which X → Z (X determines Z) indirectly, by virtue of X → Y and Y → Z (where it is not the case that Y → X).</p>

### BCNF:
<p>It is also known as 3.5NF. Its the higher version 3NF and was developed by Raymond F. Boyce and Edgar F. Codd to address certain types of anomalies which were not dealt with 3NF.</p>

<p>In BCNF if every functional dependency A → B, then A has to be the Super Key of that particular table.</p>

---
# Indexes:
<p>An index is a schema object. It is used by the server to speed up the retrieval of rows by using a pointer. It can reduce disk I/O(input/output) by using a rapid path access method to locate data quickly. An index helps to speed up select queries and where clauses, but it slows down data input, with the update and the insert statements. Indexes can be created or dropped with no effect on the data.</p>

<p>Let's see some syntax oh how to create, remove and alter an index.</p>

### Creating an index:

```sql
CREATE INDEX index
 ON TABLE column;
```
<p>where the index is the name given to that index and TABLE is the name of the table on which that index is created and column is the name of that column for which it is applied.</p>

---
### Unique index:

```sql
CREATE UNIQUE INDEX index
 ON TABLE column;
```
---
<p>Unique indexes are used for the maintenance of the integrity of the data present in the table as well as for the fast performance, it does not allow multiple values to enter into the table. </p>

---
### Removing an index:

```sql
DROP INDEX index;
```
<p>To drop an index, we must be the owner of the index.</p>

---
### When should index be created:
* If column has wide range of values.
* If column does not contain large number of null values.
* One or more columns are frequently used together in where clause and join condition.

---
### When should indexes be avoided:
* If table is small or column updated frequently.
* Columns are not often used as a condition in the query.

---
# Transactions:
<p>A transaction is a sequence of steps or tasks performed on a database as a single unit. If any of these tasks are not performed, the whole unit is rolled back to its previous state. Otherwise, the changes are updated in the database. In simpler terms, it is “ALL or NONE”.</p>

<p>A database transaction has four main properties that should be maintained while writing a transaction. These are called ACID properties as we discussed earlier.</p>

## Transaction control commands:
* BEGIN
* COMMIT
* ROLLBACK
* SAVE

### BEGIN:
<p> We assign a starting point to a transaction using the BEGIN TRANSACTION statement. After beginning, the transaction will either be committed or rolled back.

Consider the sample table (students_table) that has the two entries shown below:</p>

| student_id | student_name |
| :-: | :-: |
| 1 | abc |
| 2 | def |

### COMMIT:
<p>The ending point of a transaction is marked using the COMMIT command. It is used to update changes made by the transaction in the database and saves all modifications made until the last COMMIT or ROLLBACK command. This can be seen below:</p>

```sql
BEGIN TRANSACTION
UPDATE students_table
SET student_name = 'xyz' 
WHERE student_id = 1
COMMIT
```

<p>Result:</p>

| student_id | student_name |
| :-: | :-: |
| 1 | xyz |
| 2 | def |

### ROLLBACK:
<p>In case of any failure or error during the transaction, we use the ROLLBACK command to undo all modifications made till the last COMMIT or ROLLBACK command. It would look like this:</p>

```sql
DELETE FROM students_table
WHERE student_id = 1
ROLLBACK
```

<p>Result:</p>

| student_id | student_name |
| :-: | :-: |
| 1 | xyz |
| 2 | def |

### SAVE:
<p>To save the current state of the database in a transaction, use the SAVE TRANSACTION. In case of any failure in the transaction, it is used to roll back to the previous save point without rolling back the complete transaction. This process is shown below:</p>

```sql
SAVE TRANSACTION point1
DELETE FROM students_table WHERE student_id = 1

SAVE TRANSACTION point2
DELETE FROM students_table WHERE student_id = 2

ROLLBACK TRANSACTION point1
        --OR
ROLLBACK TRANSACTION point2
```

<p>Result:</p>

| student_id | student_name |
| :-: | :-: |
| 1 | xyz |
| 2 | def |

```
Rollback to savepoint "point1"
```

| student_id | student_name |
| :-: | :-: |
| 2 | def |

```
Rollback to savepoint "point2"
```

* All changes are made in the temporary database. To make them permanent, we need to COMMIT them.
* The BEGIN TRANSACTION can also be written as BEGIN TRANS.
* By default, all DML commands (INSERT, UPDATE, DELETE) are auto-committed unless we define a transaction.

---
# Locking mechanism:
<p>Locking is essential to successful SQL Server transactions processing and it is designed to allow SQL Server to work seamlessly in a multi-user environment. Locking is the way that SQL Server manages transaction concurrency. Essentially, locks are in-memory structures which have owners, types, and the hash of the resource that it should protect. A lock as an in-memory structure is 96 bytes in size.</p>

## Lock modes:
* Exclusive(X)
* Shared(S)
* Update(U)
* Intent(I)

### Exclusive lock (X):
<p>This lock type, when imposed, will ensure that a page or row will be reserved exclusively for the transaction that imposed the exclusive lock, as long as the transaction holds the lock.

The exclusive lock will be imposed by the transaction when it wants to modify the page or row data, which is in the case of DML statements DELETE, INSERT and UPDATE. An exclusive lock can be imposed to a page or row only if there is no other shared or exclusive lock imposed already on the target. This practically means that only one exclusive lock can be imposed to a page or row, and once imposed no other lock can be imposed on locked resources.</p>

### Shared lock (S):
<p>this lock type, when imposed, will reserve a page or row to be available only for reading, which means that any other transaction will be prevented to modify the locked record as long as the lock is active. However, a shared lock can be imposed by several transactions at the same time over the same page or row and in that way several transactions can share the ability for data reading since the reading process itself will not affect anyhow the actual page or row data. In addition, a shared lock will allow write operations, but no DDL changes will be allowed.</p>

### Update lock (U):
<p>this lock is similar to an exclusive lock but is designed to be more flexible in a way. An update lock can be imposed on a record that already has a shared lock. In such a case, the update lock will impose another shared lock on the target row. Once the transaction that holds the update lock is ready to change the data, the update lock (U) will be transformed to an exclusive lock (X). It is important to understand that update lock is asymmetrical in regards of shared locks. While the update lock can be imposed on a record that has the shared lock, the shared lock cannot be imposed on the record that already has the update lock.</p>

### Intent lock (I):
<p>this lock is a means used by a transaction to inform another transaction about its intention to acquire a lock. The purpose of such lock is to ensure data modification to be executed properly by preventing another transaction to acquire a lock on the next in hierarchy object. In practice, when a transaction wants to acquire a lock on the row, it will acquire an intent lock on a table, which is a higher hierarchy object. By acquiring the intent lock, the transaction will not allow other transactions to acquire the exclusive lock on that table (otherwise, exclusive lock imposed by some other transaction would cancel the row lock).</p>

---
# Database Isolation Levels:
<p>Isolation determines how transaction integrity is visible to other users and systems. It means that a transaction should take place in a system in such a way that it is the only transaction that is accessing the resources in a database system.</p>

<p>The SQL standard defines four isolation levels.</p>

## Read Uncommitted:
<p>Read Uncommitted is the lowest isolation level. In this level, one transaction may read not yet committed changes made by other transaction, thereby allowing dirty reads. In this level, transactions are not isolated from each other.</p>

## Read Committed:
<p>This isolation level guarantees that any data read is committed at the moment it is read. Thus it does not allows dirty read. The transaction holds a read or write lock on the current row, and thus prevent other transactions from reading, updating or deleting it.</p>

## Repeatable Read:
<p>This is the most restrictive isolation level. The transaction holds read locks on all rows it references and writes locks on all rows it inserts, updates, or deletes. Since other transaction cannot read, update or delete these rows, consequently it avoids non-repeatable read.</p>

## Serializable:
<p>This is the Highest isolation level. A serializable execution is guaranteed to be serializable. Serializable execution is defined to be an execution of operations in which concurrently executing transactions appears to be serially executing.</p>

---
# Triggers:
<p>A trigger is a stored procedure - which is a set of SQL statements saved under a name, just like a function, so that it can be reused - that is executed automatically when a certain event occurs in a database.</p>

## Types of Triggers:

1. Event
* DML Trigger: It fires when a DML (Database Manipulation Language) event is specified (INSERT/UPDATE/DELETE)
* DDL Trigger: It fires when a DDL (Database Definition Language) event is specified (CREATE/ALTER)
* DATABASE Trigger: It fires when a database event is specified (LOGON/LOGOFF/STARTUP/SHUTDOWN)

2. Timing
* BEFORE Trigger: It fires before the specified event has occurred.
* AFTER Trigger: It fires after a specified event has occurred.
* INSTEAD OF Trigger: It lets you skip a statement and execute a different statement present in the trigger body instead.

3. Level
* STATEMENT level Trigger: It fires one time for a specified event statement.
* ROW level Trigger: It fires for each record that was affected in a specified event. (only for DML)

### SQL Implementation:
<p>A trigger is implemented in the given code which will be fired before anything is inserted in the people table. This trigger makes sure that a person does not have a negative age and sets the age to zero.</p>

```sql
CREATE TABLE people (
  age INT, 
  name varchar(150)
);

delimiter //
CREATE TRIGGER agecheck BEFORE INSERT ON people FOR EACH ROW IF NEW.age < 0 THEN SET NEW.age = 0; END 
IF; //

INSERT INTO people VALUES (-20, 'Sid'), (30, 'Josh');
select * from people;
```

---
# REFERENCES:
* https://sqlbolt.com/
* https://www.datacamp.com/community/tutorials/10-command-line-utilities-postgresql
* https://www.geeksforgeeks.org/sql-join-set-1-inner-left-right-and-full-joins/
* https://sqlbolt.com/lesson/select_queries_with_aggregates
* https://sqlbolt.com/lesson/select_queries_order_of_execution
* https://www.edureka.co/blog/normalization-in-sql/#1stNF
* https://www.geeksforgeeks.org/sql-indexes/
* https://www.sqlshack.com/locking-sql-server/
* https://www.geeksforgeeks.org/transaction-isolation-levels-dbms/

