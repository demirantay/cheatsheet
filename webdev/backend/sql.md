# SQL

SQL is a standard language for storing, manipulating and retrieving data in databases.

## Basics (CRUD)

```sql

SELECT column1, column2 FROM table_name;    -- selects col1, 2 from a table
SELECT * FROM table_name;                   -- selects all columns from a  table
SELECT DISTINCT column1, column2 FROM table_name; -- does not select duplicate values in rows

-- where clause is used for filter 
SELECT * FROM Customers
WHERE Country='Mexico';  

-- wehere clause can be combined with
-- and, or, not operators
SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';

SELECT * FROM Customers
WHERE NOT Country='Germany';

-- The ORDER BY keyword is used to sort the 
-- result-set in ascending or descending order.
SELECT * FROM Customers
ORDER BY Country;

SELECT * FROM Customers
ORDER BY Country DESC;

SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;

-- The INSERT INTO statement is used to 
-- insert new records in a table.
INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');

INSERT INTO Customers (CustomerName, City, Country)
VALUES ('Cardinal', 'Stavanger', 'Norway');

-- The UPDATE statement is used to modify the existing records in a table.
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
WHERE CustomerID = 1;

UPDATE Customers
SET ContactName='Juan'
WHERE Country='Mexico';

-- The DELETE statement is used to delete existing records in a table.
DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';

DELETE FROM table_name; -- deletes all records

-- IMPORTANT: Note: Be careful when updating  and deleting records in a table! Notice the 
-- WHERE clause in the UPDATE statement. The WHERE clause specifies which 
-- record(s) that should be updated. If you omit the WHERE clause, 
-- all records in the table will be updated or deleted!

```

## Databases

```sql
-- createa a db
CREATE DATABASE databasename;


-- delete a db
DROP DATABASE databasename;


-- To backup a db
BACKUP DATABASE databasename
TO DISK = 'filepath';

-- realworld ex:
BACKUP DATABASE testDB
TO DISK = 'D:\backups\testDB.bak';


-- Create a table
CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);


-- Deleteing a table
DROP TABLE table_name;


-- Delete data inside table but not table
TRUNCATE TABLE table_name;

-- The ALTER TABLE statement is used to add, 
-- delete, or modify columns in an existing table.
ALTER TABLE Customers
ADD Email varchar(255);

ALTER TABLE Customers
DROP COLUMN Email;

ALTER TABLE table_name
MODIFY COLUMN column_name datatype;


-- constraints can be used to add rules to columns
CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    column3 datatype constraint,
    ....
);

-- SQL CONSTRAINT LIST
-- NOT NULL - Ensures that a column cannot have a NULL value
-- UNIQUE - Ensures that all values in a column are different
-- PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
-- FOREIGN KEY - Prevents actions that would destroy links between tables
-- CHECK - Ensures that the values in a column satisfies a specific condition
-- DEFAULT - Sets a default value for a column if no value is specified
-- CREATE INDEX - Used to create and retrieve data from the database very quickly

-- The NOT NULL constraint enforces a column to NOT accept NULL values.
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);


-- The UNIQUE constraint ensures that all values in a column are different.
CREATE TABLE Persons (
  ID int NOT NULL UNIQUE,
);


-- The PRIMARY KEY constraint uniquely identifies each record in a table.
CREATE TABLE Persons (
  ID int NOT NULL,
  ...
  PRIMARY KEY (ID)
)

-- dropping primary key
ALTER TABLE Persons
DROP PRIMARY KEY;

-- Foreign Key constaint
-- A FOREIGN KEY is a field (or collection of fields) in one table,
-- that refers to the PRIMARY KEY in another table.
CREATE TABLE Orders (
    OrderID int NOT NULL,
    OrderNumber int NOT NULL,
    PersonID int,
    PRIMARY KEY (OrderID),
    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
);

-- dropping foreign key
ALTER TABLE Orders
DROP FOREIGN KEY FK_PersonOrder;


-- The CHECK constraint is used to limit the value range that can be placed in a column.
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CHECK (Age>=18)
);


-- The DEFAULT constraint is used to set a default value for a column.
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255) DEFAULT 'Sandnes'
);


-- Auto-increment allows a unique number to be generated automatically 
-- when a new record is inserted into a table.
CREATE TABLE Persons (
    Personid int NOT NULL AUTO_INCREMENT,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (Personid)
);
```

## Null, Top, Min, Max, Count, Avg, Max

```sql

-- A field with a NULL value is a field with no value.
-- It is not possible to test for NULL values with 
-- comparison operators, such as =, <, or <>

SELECT column_names
FROM table_name
WHERE column_name IS NULL;

SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;

-- The SELECT TOP clause is used to specify the number of records to return.
SELECT TOP 3 * FROM Customers; -- gets top three
SELECT TOP 50 PERCENT * FROM Customers; -- gets 50 percent of records

-- min / max

-- returns smallest val of selected col
SELECT MIN(column_name)
FROM table_name
WHERE condition;

-- returns biggest val of selected col
SELECT MAX(column_name)
FROM table_name
WHERE condition;

-- returns you the number of rows of that col
SELECT COUNT(column_name)
FROM table_name
WHERE condition;

-- the AVG() function returns the average value of a numeric column. 
SELECT AVG(column_name)
FROM table_name
WHERE condition;


-- The SUM() function returns the total sum of a numeric column. 
SELECT SUM(column_name)
FROM table_name
WHERE condition;

```

## Like, Wildcards, In, Between, Aliases

```sql
-- The LIKE operator is used in a WHERE clause 
-- to search for a specified pattern in a column.
SELECT * FROM Customers
WHERE CustomerName LIKE '%or%';

-- The IN operator allows you to specify multiple values in a WHERE clause.
SELECT * FROM Customers
WHERE Country IN ('Germany', 'France', 'UK');

-- The BETWEEN operator selects values within a given range. 
-- The values can be numbers, text, or dates.
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20;

-- SQL aliases are used to give a table, or a column in a table, a temporary name.
SELECT column_name AS alias_name
FROM table_name;
```


## Joins, Inner Join, Left Join, Right Join, Full Join, Self Join, Union, Group By

```sql
-- A JOIN clause is used to combine 
-- rows from two or more tables
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;

-- The INNER JOIN keyword selects records 
-- that have matching values in both tables.
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;

-- he LEFT JOIN keyword returns all records from 
-- the left table (table1), and the matching records 
-- from the right table (table2).
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;

-- he RIGHT JOIN keyword returns all records from the right table 
-- (table2), and the matching records from the left table (table1)
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;

-- The FULL OUTER JOIN keyword returns all records when 
-- there is a match in left (table1) or right (table2) table records.
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name
WHERE condition;


-- A self join is a regular join, but the table is joined with itself.
SELECT column_name(s)
FROM table1 T1, table1 T2
WHERE condition;

-- The UNION operator is used to combine the result-set of two or more SELECT statements.
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;


-- The GROUP BY statement groups rows that have the same values into summary rows
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```

## Having, Exists, Any All, Select Into, Insert Into Select, Case, Null Functions, Stored Procedures, Comments, Operators

```sql
-- The HAVING clause was added to SQL because the WHERE keyword 
-- cannot be used with aggregate functions.
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);

-- The EXISTS operator is used to test for the 
-- existence of any record in a subquery.
SELECT column_name(s)
FROM table_name
WHERE EXISTS
(SELECT column_name FROM table_name WHERE condition);
```









