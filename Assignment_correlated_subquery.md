# Correlated Subquery Assignment 

---

## Step 1: Create Tables

```sql
CREATE TABLE departments (
    department_id SERIAL PRIMARY KEY,
    department_name VARCHAR(50)
);

CREATE TABLE employees (
    employee_id SERIAL PRIMARY KEY,
    employee_name VARCHAR(50),
    salary NUMERIC(10,2),
    department_id INT,
    hire_date DATE,
    FOREIGN KEY (department_id)
    REFERENCES departments(department_id)
);
```

---

## Step 2: Insert Data

```sql
INSERT INTO departments (department_name)
VALUES
('HR'),
('IT'),
('Finance');
```

```sql
INSERT INTO employees
(employee_name, salary, department_id, hire_date)
VALUES
('Amit', 50000, 1, '2022-01-10'),
('Priya', 60000, 1, '2021-05-15'),

('Rahul', 70000, 2, '2020-03-12'),
('Neha', 90000, 2, '2019-07-01'),
('Karan', 80000, 2, '2021-11-20'),

('Anjali', 65000, 3, '2022-02-14'),
('Rohit', 75000, 3, '2020-09-09');
```

---

## Verify Data

```sql
SELECT * FROM departments;

SELECT * FROM employees;
```



# Correlated Subquery 1

## Employees earning more than the average salary of their department

```sql
SELECT
    e1.employee_name,
    e1.salary,
    e1.department_id
FROM employees e1
WHERE e1.salary >
(
    SELECT AVG(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e1.department_id
);
```



# Correlated Subquery 2

## Highest-paid employee in each department

```sql
SELECT
    e1.employee_name,
    e1.salary,
    e1.department_id
FROM employees e1
WHERE e1.salary =
(
    SELECT MAX(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e1.department_id
);
```




# Correlated Subquery 3

## Employees hired before the latest hire in their department

```sql
SELECT
    e1.employee_name,
    e1.hire_date,
    e1.department_id
FROM employees e1
WHERE e1.hire_date <
(
    SELECT MAX(e2.hire_date)
    FROM employees e2
    WHERE e2.department_id = e1.department_id
);
```


# Correlated Subquery 4

## Employees whose salary is lower than the highest salary in their department

```sql
SELECT
    e1.employee_name,
    e1.salary,
    e1.department_id
FROM employees e1
WHERE e1.salary <
(
    SELECT MAX(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e1.department_id
);
```



---

# Correlated Subquery 5

## Employees who are not the lowest-paid employee in their department

```sql
SELECT
    e1.employee_name,
    e1.salary,
    e1.department_id
FROM employees e1
WHERE e1.salary >
(
    SELECT MIN(e2.salary)
    FROM employees e2
    WHERE e2.department_id = e1.department_id
);
```

