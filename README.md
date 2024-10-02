# SQL-Create-table
#Create table named Persons with columns, PersonID, FirstName, LastName, Adress and City.
CREATE TABLE Persons (
    PersonID int,
    FirstName varchar(255),
    LastName varchar(255),
    Address varchar(255),
    City varchar(255)
);
#DML COMMANDS
#DROP TABLE -Deletes the entire table i.e DROP TABLE table_name;
DROP TABLE customers;
#TRUNCATE TABLE - Deletes the data within the table , does not alter the tables structure .ie TRUNCATE table
ALTER TABLE - Changes contents within the table i.e
ALTER TABLE table_name;
ADD COLUMN column_name;

