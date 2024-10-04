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

