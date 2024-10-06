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
    Firstname VARCHAR(255),
    Lastname VARCHAR(255),
    Position TEXT,
    Salary INT(8) NOT NULL,
    Sex TEXT,
    Dob DATE,
    CONSTRAINT PK_Staff PRIMARY KEY (Staffno)
);
-- Inserting a new record into the Staff table
INSERT INTO Staff (Staffno, Firstname, Lastname, Position, Salary, Sex, Dob) 
VALUES ('KE324', 'Keli', 'Mark', 'Data Scientist', 40000, 'Male', '2000-01-01');
-- Inserting multiple records into the Staff table
INSERT INTO Staff (Staffno, Firstname, Lastname, Position, Salary, Sex, Dob) 
VALUES 
    ('KE325', 'Alice', 'Johnson', 'Software Engineer', 60000, 'Female', '1995-03-15'),
    ('KE326', 'David', 'Smith', 'Project Manager', 75000, 'Male', '1988-07-22'),
    ('KE327', 'Emma', 'Williams', 'UX Designer', 55000, 'Female', '1992-12-05'),
    ('KE328', 'James', 'Brown', 'Data Analyst', 50000, 'Male', '1990-11-30'),
    ('KE329', 'Sophia', 'Davis', 'HR Specialist', 45000, 'Female', '1994-02-20'),
    ('KE330', 'Michael', 'Wilson', 'DevOps Engineer', 70000, 'Male', '1986-05-10');
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
WHERE Position IN ('Manager','Engineer');
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

