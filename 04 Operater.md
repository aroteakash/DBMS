# Assignment No 4

### **Aim :** Implementation of different types of operators(Arithmetic Operators  ,Logical Operators , Comparison Operator  ,Special Operator,  Set Operation) in SQL by using suitable examples

## Basic
```
create database CompanyDB;
 ```
Query OK, 1 row affected (1.15 sec)
```
USE CompanyDB;
```
database changed
```
create table employees (
    employeeid int primary key,
    Name varchar(100),
    Age int,
    Salary decimal(10, 2),
    Department varchar(50),
    ManagerID int null
);

```
Query OK, 0 rows affected (2.41 sec)
```
insert into employees (employeeid, Name, Age, Salary, Department, ManagerID) values
(1, 'AKash', 30, 60000, 'IT', null),
(2, 'Rohan', 45, 80000, 'Finance', null),
(3, 'Rahul', 35, 75000, 'HR', 1),
(4, 'Rohit', 25, 50000, 'IT', 1),
(5, 'Atish', 40, 65000, 'HR', 3),
(6, 'Sameer', 29, 48000, 'IT', 4),
(7, 'Parimal', 38, 72000, 'Finance', 2);

```
Query OK, 5 rows affected (0.14 sec)
```
select * from studentmarks;
```


## 1. Arithmetic Operators

1. "+" (ADD)
```
 select stid, name, science, math, english, science+math+english AS 'Total' from studentmarks;
```
```
O/P
+------+---------+---------+------+---------+-------+
| stid | name    | science | math | english | Total |
+------+---------+---------+------+---------+-------+
|    1 | Akash   |      65 |   59 |      81 |   205 |
|    2 | Akshyay |      95 |   89 |      71 |   255 |
|    3 | Dipak   |      91 |   56 |      79 |   226 |
|    4 | Dipali  |      71 |   96 |      72 |   239 |
|    5 | Tina    |      78 |   89 |      49 |   216 |
+------+---------+---------+------+---------+-------+
```

2. "-" (Subtract)
```
select 10 - 10;
```
3. " * " (Multiply)
```
select 10 * 10;
```
4. / (Divide)
```
select 10 / 10;
```
5. % (Module)
```
select 10 % 10;
```
## 2. Logical Operators
1. AND
```
select *
from employees
where Salary > 50000 AND Department = 'IT';
```
2. OR
```
select *
from employees
where Salary > 50000 OR Department = 'HR';
```
3. not
```
select *
from employees
where not Department = 'Finance';

```
## 3. Comparison Operators
1. = (Equal to)
```
select *
from employees
where Age = 30;
```
6. <> ( not Equal to)
```
select *
from employees
where Age <> 30;
```
2. ">" (Greater than)
```
select *
from employees
where Salary > 60000;
```
5. <= (Less than Equal to)
```
select *
from employees
where Salary <= 45000;
```

## 4. Special Operators
1. BETWEEN
```
select *
from employees
where Age BETWEEN 30 AND 40;
```
2. IN
```
select *
from employees
where Department IN ('HR', 'IT', 'Finance');
```
3. LIKE
```
select *
from employees
where Name LIKE 'J%';
```
4. IS null operator
```
select *
from employees
where ManagerID IS null;
```


## 5. Set Operators
1. UNION
```
select Name, Department
from employees
where Department = 'IT'
UNION
select Name, Department
from employees
where Department = 'HR';
```

2. INTERSECT
```
select Name, Department
from employees
where Department = 'IT'
INTERSECT
select Name, Department
from employees
where Salary > 60000;
```
3. MINUS
```
select Name, Department
from employees
where Department = 'IT'
EXCEPT
select Name, Department
from employees
where Salary < 60000;
```


