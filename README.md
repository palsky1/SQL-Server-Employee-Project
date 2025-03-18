# SQL-Server-Employee-Project
SQL Server project with employee database, tables, sample data, and stored procedures.
-- create_database.sql
-- Create the Employee Database
CREATE DATABASE EmployeeDB;
GO

USE EmployeeDB;
GO

-- tables.sql
-- Create Employee Table
CREATE TABLE Employee (
    ID INT PRIMARY KEY IDENTITY(1,1),
    Name VARCHAR(100) NOT NULL,
    Salary DECIMAL(10,2) NOT NULL,
    Department VARCHAR(50) NOT NULL,
    JoiningDate DATE NOT NULL
);
GO

-- sample_data.sql
-- Insert Sample Data
INSERT INTO Employee (Name, Salary, Department, JoiningDate) VALUES 
('John Doe', 5000, 'HR', '2020-05-10'),
('Jane Smith', 7000, 'IT', '2019-08-15'),
('Mike Johnson', 6000, 'Finance', '2021-02-20'),
('Emma Brown', 9000, 'IT', '2018-07-30'),
('Robert White', 8000, 'Marketing', '2020-11-25');
GO

-- stored_procedures.sql
-- Stored Procedure to Get the Second-Highest Salary
CREATE PROCEDURE GetSecondHighestSalary AS
BEGIN
    SELECT MAX(Salary) AS SecondHighestSalary
    FROM Employee
    WHERE Salary < (SELECT MAX(Salary) FROM Employee);
END;
GO
