To achieve this task, we need to follow these steps:

1. create a database schema for employees.
2. create a table to store employee data.
3. Populate the table with some sample data.
4. Write a PL/SQL block to calculate the incentive of an employee whose ID is accepted from the user.

Here's how you can do it:

### Step 1: create database Schema
First, we'll assume you have a database already created. We'll create a new schema for the employees if it's not already present.

### Step 2: create Employee table

```sql
create table employees (
    employeeid NUMBER primary key,
    firstname VARCHAR2(50),
    lastname VARCHAR2(50),
    Salary NUMBER(10, 2),
    IncentivePercentage NUMBER(5, 2) -- This percentage will be used to calculate the incentive
);
```

### Step 3: Insert Sample Data

```sql
insert into employees (employeeid, firstname, lastname, Salary, IncentivePercentage) values (1, 'John', 'Doe', 50000, 10);
insert into employees (employeeid, firstname, lastname, Salary, IncentivePercentage) values (2, 'Jane', 'Smith', 60000, 15);
insert into employees (employeeid, firstname, lastname, Salary, IncentivePercentage) values (3, 'Alice', 'Johnson', 70000, 20);
```

### Step 4: Write PL/SQL Block to Calculate Incentive

```sql
DECLARE
    v_employee_id employees.employeeid%TYPE;
    v_salary employees.Salary%TYPE;
    v_incentive_percentage employees.IncentivePercentage%TYPE;
    v_incentive NUMBER(10, 2);
BEGIN
    -- Accept the employee ID from the user
    v_employee_id := &employeeid;

    -- Fetch the employee's salary and incentive percentage
    select Salary, IncentivePercentage
    into v_salary, v_incentive_percentage
    from employees
    where employeeid = v_employee_id;

    -- Calculate the incentive
    v_incentive := v_salary * (v_incentive_percentage / 100);

    -- Display the incentive
    DBMS_OUTPUT.PUT_LINE('The incentive for employee ID ' || v_employee_id || ' is ' || v_incentive);
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Employee ID ' || v_employee_id || ' does not exist.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An error occurred: ' || SQLERRM);
END;
/
```

### Explanation

1. **Declaration Section**:
    - `v_employee_id`: Variable to store the employee ID entered by the user.
    - `v_salary`: Variable to store the salary of the employee.
    - `v_incentive_percentage`: Variable to store the incentive percentage of the employee.
    - `v_incentive`: Variable to store the calculated incentive.

2. **Begin Section**:
    - The employee ID is accepted from the user using `&employeeid`.
    - The `select` statement fetches the salary and incentive percentage of the employee whose ID matches `v_employee_id`.
    - The incentive is calculated using the formula: `v_salary * (v_incentive_percentage / 100)`.
    - The result is displayed using `DBMS_OUTPUT.PUT_LINE`.

3. **Exception Handling**:
    - Handles `NO_DATA_FOUND` exception if the employee ID does not exist.
    - Handles all other exceptions using `WHEN OTHERS`.

To execute this PL/SQL block, make sure you have enabled `DBMS_OUTPUT` in your SQL*Plus or SQL Developer session using:

```sql
SET SERVEROUTPUT ON;
```

This will allow the `DBMS_OUTPUT.PUT_LINE` statements to display the output.