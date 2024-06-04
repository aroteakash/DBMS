# Assignment No 5

### **Aim :** Implementation of Different types of Joins(Inner Join  ,Outer Join  Natural Join ) in SQL on Employee database
### 1 Departmant database
```
create table employees (
    employeeid int primary key,
    firstname varchar(50),
    lastname varchar(50),
    departmentid int
);

```
```
insert into employees (employeeid, firstname, lastname, departmentid) values
(1, 'Akash', 'Doe', 10),
(2, 'Krushana', 'Smith', 20),
(3, 'Rohan', 'Brown', 30),
(4, 'Rahul', 'Johnson', null);

```
### 2 Employee database
```
create table departments (
    departmentid int primary key,
    departmentname varchar(50)
);

```
```
insert into departments (departmentid, departmentname) values
(10, 'HR'),
(20, 'IT'),
(30, 'Finance'),
(40, 'Marketing');

```
## 1. Inner Join

```
select 
    employees.employeeid,
    employees.firstname,
    employees.lastname,
    departments.departmentname
from 
    employees
INNER JOIN 
    departments 
ON 
    employees.departmentid = departments.departmentid;

```
o/p
```

```

## 2. Outer Join

```
select 
    employees.employeeid,
    employees.firstname,
    employees.lastname,
    departments.departmentname
from 
    employees
LEFT OUTER JOIN 
    departments 
ON 
    employees.departmentid = departments.departmentid;

```
O/P
```

```

## 3. Natural Join

```
select 
    employees.employeeid,
    employees.firstname,
    employees.lastname,
    departments.departmentname
from 
    employees
NATURAL JOIN 
    departments;

```
O/P
```

```

