# Assignment 4 – Collaborative Schema Design + ER Diagram

## Problem Statement:
As a team, pick any company or domain you find interesting and build its database together. Each intern owns one table.
Each intern delivers: their table design with correct data types and constraints, justification for every constraint, foreign key linking to at least one teammate's table, realistic dummy data, and an ER diagram with their name as table owner. 
As a group: all tables should connect, run clean on a fresh PostgreSQL database, and end with one meaningful business query joiningall tables together.

## Solution:
In this assignment, our team created a database for an Employee Management System.
The database stores information about employees, departments, projects, salaries, attendance, tasks, and clients.

Each team member was given one table to design.
My responsibility was to create the Salary Table.

## My Approach:
I created the salary table to store employee salary details in a proper way. I used suitable data types for salary values and added constraints to avoid wrong or empty data.
I connected my table with the employee table using a foreign key because every salary belongs to an employee. I tried to make the table simple, clean, and similar to a real company payroll system.

## Group Work:
Our entire team worked together to build a connected database system. Each member designed a different table, but all tables were linked together.
One teammate created the employee table which stores employee information like name, email, department, and designation.
Another teammate created the department table to manage departments inside the company.
One member created the project table to store project details and client information.
Another teammate worked on the attendance table to track employee attendance.
The tasks table was used to assign work to employees.
I worked on the salary table which stores employee salary, bonus, tax deduction, payment date, and payment status.

At the end, all tables were connected properly and the complete database ran successfully in PostgreSQL.

## My Table – Salary Table
The salary table stores:
employee salary, bonus, tax deduction, payment date. payment status

This table helps the company manage payroll records easily.

## Salary Table SQL Code
'''
CREATE TABLE salary (

    salary_id SERIAL PRIMARY KEY,

    employee_id INT NOT NULL,

    base_salary NUMERIC(10,2) NOT NULL,

    bonus NUMERIC(10,2),

    tax_deduction NUMERIC(10,2),

    payment_date DATE NOT NULL,

    payment_status VARCHAR(20),

    CONSTRAINT fk_salary_employee
    FOREIGN KEY (employee_id)
    REFERENCES employee(employee_id)

);

'''

![Alt](https://i.ibb.co/27VmmQxD/Screenshot-2026-05-18-132245.png)

I used PRIMARY KEY on salary_id so every salary record has a unique ID.
I used NOT NULL on important fields because these values should not be empty.
I used FOREIGN KEY to connect the salary table with the employee table.
I used NUMERIC(10,2) because salary values can contain decimal numbers.


## ER Diagram

The ER diagram shows how all tables are connected in the database.
![Alt](https://i.ibb.co/FqyWbMrb/Screenshot-2026-05-18-130006.png)