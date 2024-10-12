# SQL-Create-table
--Create table named Persons with columns, PersonID, FirstName, LastName, Adress and City.
CREATE TABLE Persons (
    PersonID int,
    FirstName varchar(255),
    LastName varchar(255),
    Address varchar(255),
    City varchar(255)
);
--DML COMMANDS
--DROP TABLE -Deletes the entire table i.e DROP TABLE table_name;
DROP TABLE customers;
--TRUNCATE TABLE - Deletes the data within the table , does not alter the tables structure .ie TRUNCATE table
ALTER TABLE - Changes contents within the table i.e
ALTER TABLE table_name;
ADD COLUMN column_name;
--Inserting values
--INSERT INTO table_name
VALUES(value1,value2..)
INSERT INTO Persons
VALUES ("40404000","Marcos", "Allan", "3050-20", "Machakos");
--Insert values to specific columns
INSERT INTO table_name(column1,column2..)
VALUES(value1, value2,..);
INSERT INTO Persons(PersonID, FirstName,LastName, Address,City)
VALUES("30232020","Manse","Musa","32023_23","Latgiss");
INSERT INTO Persons(PersonID, LastName, Address,City)
VALUES("30232020","Musa","32023_23","Latgiss");
--UPDATE Statement - Modifies the table data
--UPDATE table_name
--SET column _name = new name
--WHERE column_name = existing_name
UPDATE Persons
SET FirstName = "Alex"
WHERE LastName = "Musa"
-- DELETE Command
-- DELETE FROM table_name
-- WHERE column_name = some_value
DELETE FROM Persons WHERE City = 'Nairobi';

-- SQL Constraints
-- NOT NULL Constraints - Enforces value into a column--
--ALTER TABLE Persons
--MODIFY PersonID int NOT NULL;

--UNIQUE Constraints - To ensure columns are different(Avoid duplicates)
--Primary keys are usually unique
    
CREATE TABLE Youth (
    Age int NOT NULL UNIQUE,
    LastName varchar(255),
    FirstName varchar(255)
);
-- For Multiple columns
--CONSTRAINT UC_ tablename UNIQUE (columns names)
CREATE TABLE YoungG (
    Age int 
    LastName varchar (255),
    FirstName varchar (255),
CONSTRAINT UC_Youth UNIQUE (Age,FirstName)
);
-- Primary key Constraints
ALTER TABLE Persons
ADD PRIMARY KEY (PersonID);
--For Multiple colmuns
CONSTRAINT PK_Persons(PersonID,Lastname)
-- A PRIMARY KEY does not accept null values while a UNIQUE KEY accepts one null value
--A table can have only one PRIMARY KEY and can have many UNIQUE KEYS
--AUTO INCREAMENT --assume multiple of adding 1
CREATE TABLE Employees (
    EmployeeID int AUTO_INCREMENT 
    FirstName varchar(255) UNIQUE,
    LastName varchar(255),
    Department varchar(255) NOT NULL,
    CONSTRAINT PK_Employees PRIMARY KEY (EmployeeID)
);
--DATA QUERYING
--SELECT Statement - To select data from a table the result is in tabular form.
--SELECT coulmn-name FROM table_name
SELECT FirstName, LastName
FROM Persons;
--Selecting all columns use: SELECT * FROM table_name
SELECT * FROM persons;
--SELECT DISTINCT STATEMENT
-- To select distnct data where listing may include same values :use keyword DISTINCT
--SELECT DISTINCT column_name
--FROM table_name;
SELECT DISTINCT FirstName
FROM Persons;
-- WHERE CLAUSE
-- To write some conditions
--SELECT * FROM table_name
--WHERE column_name ='some value'
SELECT * FROM Persons
WHERE  City = 'Machakos';
--Using LIKE operator
-- 'A%'(starting with A)--'%A'(Ending with  A)--'%Al%'( With pattern Al)
SELECT * FROM Persons
WHERE FirstName LIKE '%Al%';
--BETWEEN / NOT BETWEEN Statement
-- BETWEEN checks if a value is within a range--NOT BETWEEN checks if a value is outside a range
--E.G

CREATE TABLE Staff (
    Staffno VARCHAR (255),
    Branchno VARCHAR(255),
    Firstname VARCHAR(255),
    Lastname VARCHAR(255),
    Position TEXT,
    Salary INT(8) NOT NULL,
    Sex TEXT,
    Dob DATE,
    CONSTRAINT PK_Staff PRIMARY KEY (Staffno)
);
-- Inserting a new record into the Staff table
INSERT INTO Staff (Staffno,Branchno, Firstname, Lastname, Position, Salary, Sex, Dob) 
VALUES ('KE324', '20RA','Keli', 'Mark', 'Data Scientist', 40000, 'Male', '2000-01-01');
-- Inserting multiple records into the Staff table
INSERT INTO Staff (Staffno, Branchno, Firstname, Lastname, Position, Salary, Sex, Dob) 
VALUES 
    ('KE325', '20RA', 'Anna', 'Smith', 'Data Analyst', 45000, 'Female', '1995-05-15'),
    ('KE326', '20RB', 'John', 'Doe', 'Data Analyst', 46000, 'Male', '1992-03-22'),
    ('KE327', '20RC', 'Emily', 'Johnson', 'Data Analyst', 47000, 'Female', '1994-07-10'),
    ('KE328', '20RD', 'Michael', 'Brown', 'Manager', 80000, 'Male', '1988-09-15'),
    ('KE329', '20RE', 'Sarah', 'Davis', 'Manager', 82000, 'Female', '1991-12-01'),
    ('KE330', '20RF', 'Laura', 'Wilson', 'UX Designer', 55000, 'Female', '1993-02-20'),
    ('KE331', '20RG', 'David', 'Miller', 'Software Engineer', 60000, 'Male', '1986-11-30'),
    ('KE332', '20RH', 'Chris', 'Taylor', 'Project Manager', 75000, 'Male', '1989-06-25'),
    ('KE333', '20RI', 'Sophia', 'Anderson', 'Product Owner', 70000, 'Female', '1990-04-14'),
    ('KE334', '20RJ', 'James', 'Thomas', 'Database Administrator', 62000, 'Male', '1987-10-08');
--Checking for BETWEEN and NOT BETWEEN
SELECT FirstName, Lastname, Position,Sex
FROM Staff
WHERE Salary BETWEEN 50000 AND 100000;
--You can also use
SELECT FirstName, Lastname, Position,Sex
FROM Staff
WHERE Salary >=70000 AND Salary <= 75000;
--IN and NOT IN
--IN tests whether a data value match one of a list of values
--NOT IN Checks for a data values that do not lie in a specific list of values 
SELECT FirstName,LastName,Position
FROM Staff
WHERE Position IN ('Manager');
--Could also be expressed as 
SELECT FirstName,LastName,Position
FROM Staff
WHERE Position = 'Manager' OR Position = 'Engineer';
--ORDER BY Clause  to select result in ascending or descending
SELECT Staffno,FirstName,LastName,Salary
FROM Staff
   ORDER BY Salary DESC;
--Order multiple items
SELECT Staffno, FirstName,LastName,Dob
FROM Staff
   ORDER BY Dob, Position ASC;
--AGGREGATION
--COUNT -Returns the number of rows in a specified column
--SUM -Adds the number of values in a specified column
--AVG -Returns average of values in a specied column
--MIN -Returns the smallest value in a specified column
--MAX - Returns the largest value in a specified column
--Count no. of staff paid more than 50000
SELECT COUNT (*) AS count
FROM Staff
WHERE  Salary >= 50000;
--Find total number of managers and their salaries
SELECT COUNT(Staffno) AS count, SUM(Salary) AS sum
FROM Staff
WHERE Position = 'Software Engineer';
-- Minimum, Maximum,Average staff salary
SELECT MIN(Salary) AS min, MAX(Salary)AS max, AVG(Salary) as avg
FROM Staff;
--GROUP BY CLAUSE
--Groups data from the SELECT tables  and produces a single summary row in each group
--Group Staff by Gender, count them and their average salaries
SELECT Sex, COUNT(Staffno) AS count, AVG(Salary) AS average
FROM Staff
GROUP BY Sex;
--HAVING CLAUSE - Designed with Group By clause to restrict what appears in final result
--WHERE clause filters individual rows 
--HAVING clause filters  groups going into final result table
SELECT Branchno, COUNT(Staffno) AS count, AVG(Salary) AS average
FROM Staff
GROUP BY Branchno
HAVING Staffno >2 ;
--
--UNION OPERATIONS
-- Statements must have same number of columns
--Columns  must have similar data types
--Columns must be in the same order
--syntax
--SELECT column_name(s) FROM table1
--UNION
--SELECT column_name(s) FROM table2
--To get all values including duplicates use #UNION ALL syntax
--Since UNION select distinct values
--SELECT City FROM Customers
--UNION
--SELECT City FROM Suppliers
--ORDER BY City;
--
--INTERSECT OPERATOR
--SELECT Column_1[,Column_2,..Column_n]
--FROM table_1[tabl_2,...table_n]
--INTERSECT
--SELECT Column_1[,Column_2,..Column_n]
--FROM table_1[tabl_2,...table_n]
--SELECT City FROM Customers
--INTERSECT
--SELECT City FROM Suppliers
--ORDER BY City;
--
--VIEWS(Virtual tables craeted by users to restrict data access and also summarize data)
--CREATE VIEW View_name AS SELECT
--column1,column2..
--FROM table_name
--WHERE[condition]
--e.g syntax 
--CREATE VIEW CUSTOMER_VIEW AS SELECT Name, Age FROM Costomers;
--UPDATING A VIEW
--UPDATE CUSTOMER_VIEW
--SET Age = 50
--WHERE Name = 'Alex';
--DELETING ROWS in a VIEW
--DELETE FROM CUSTOMERS_VIEW
--WHERE Age = 22;
--DROPPING A VIEW
--DROP VIEW VIEW NAME;
--DROP VIEW CUSTOMER_VIEW;
--
--Working with Subqueries


