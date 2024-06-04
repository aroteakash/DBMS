# Assignment No 2

### **Aim :** Implementation of DML commands (insert table, update table , delete table) of SQL on Employee database .

## 0. Basics

```
create database employee;


mysql> use employee;


mysql> create table emp_details(
    emp_id int, 
    emp_name varchar(20),
    emp_address varchar(50),
    emp_salary int
    );


mysql> desc emp_details;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| emp_id      | int         | YES  |     | null    |       |
| emp_name    | varchar(20) | YES  |     | null    |       |
| emp_address | varchar(50) | YES  |     | null    |       |
| emp_salary  | int         | YES  |     | null    |       |
+-------------+-------------+------+-----+---------+-------+
```
## 1. insert table


### 1.  Single Entry
```
insert into emp_details(emp_id, emp_name, emp_address, emp_salary) values (101, 'Akash', 'Nashik', 40000);

OR

insert into emp_details values (102, 'Dipak', 'NAshik', 49000);
```

```
mysql> select * from emp_details ;
+--------+----------+-------------+------------+
| emp_id | emp_name | emp_address | emp_salary |
+--------+----------+-------------+------------+
|    101 | Akash    | Nashik      |      40000 |
|    102 | Dipak    | NAshik      |      49000 |
+--------+----------+-------------+------------+
```

### 2.  Multiple Entry
```
insert into emp_details values
    (103, 'Krushana', 'Dhule', 75980),
    (104, 'Rohan', 'Pune', 65465),
    (105, 'Rahul', 'Mumbai', 64865);
```

```
select * from emp_details ;
+--------+----------+-------------+------------+
| emp_id | emp_name | emp_address | emp_salary |
+--------+----------+-------------+------------+
|    101 | Akash    | Nashik      |      40000 |
|    102 | Dipak    | NAshik      |      49000 |
|    103 | Krushana | Dhule       |      75980 |
|    104 | Rohan    | Pune        |      65465 |
|    105 | Rahul    | Mumbai      |      64865 |
+--------+----------+-------------+------------+
```
## 2. select table
### 1. select ALL table
```
select * from emp_details ;
```
```
+--------+----------+-------------+------------+
| emp_id | emp_name | emp_address | emp_salary |
+--------+----------+-------------+------------+
|    101 | Akash    | Nashik      |      40000 |
|    102 | Dipak    | NAshik      |      49000 |
|    103 | Krushana | Dhule       |      75980 |
|    104 | Rohan    | Pune        |      65465 |
|    105 | Rahul    | Mumbai      |      64865 |
+--------+----------+-------------+------------+
```
### 2. select SPECIAL COLUME OF table
```
select emp_id, emp_name from emp_details;
```
```
+--------+----------+
| emp_id | emp_name |
+--------+----------+
|    101 | Akash    |
|    102 | Dipak    |
|    103 | Krushana |
|    104 | Rohan    |
|    105 | Rahul    |
+--------+----------+
```
### 3. select SPECIAL ENTRY OF table
```
select * from emp_details where emp_salary >=50000;
```
```
+--------+----------+-------------+------------+
| emp_id | emp_name | emp_address | emp_salary |
+--------+----------+-------------+------------+
|    103 | Krushana | Dhule       |      75980 |
|    104 | Rohan    | Pune        |      65465 |
|    105 | Rahul    | Mumbai      |      64865 |
+--------+----------+-------------+------------+
```
## 3. Update table

### 1. Single Update
```
update emp_details set emp_name = 'Rushi'where emp_id = 103;
```
```
select * from emp_details;
+--------+----------+-------------+------------+
| emp_id | emp_name | emp_address | emp_salary |
+--------+----------+-------------+------------+
|    101 | Akash    | Nashik      |      40000 |
|    102 | Dipak    | NAshik      |      49000 |
|    103 | Rushi    | Dhule       |      75980 |
|    104 | Rohan    | Pune        |      65465 |
|    105 | Rahul    | Mumbai      |      64865 |
+--------+----------+-------------+------------+
```
### 2. Multiple Update
```
update emp_details 
    set 
    emp_address ="Nagpur", 
    emp_salary = 99991 
    where 
    emp_id =105;
```
```
select * from emp_details;
+--------+----------+-------------+------------+
| emp_id | emp_name | emp_address | emp_salary |
+--------+----------+-------------+------------+
|    101 | Akash    | Nashik      |      40000 |
|    102 | Dipak    | NAshik      |      49000 |
|    103 | Rushi    | Dhule       |      75980 |
|    104 | Rohan    | Pune        |      65465 |
|    105 | Rahul    | Nagpur      |      99991 |
+--------+----------+-------------+------------+
```

## 4. Delete table

### 3.
```
Delete from emp_details where emp_id=104;
```
```
select * from emp_details;
+--------+----------+-------------+------------+
| emp_id | emp_name | emp_address | emp_salary |
+--------+----------+-------------+------------+
|    101 | Akash    | Nashik      |      40000 |
|    102 | Dipak    | NAshik      |      49000 |
|    103 | Rushi    | Dhule       |      75980 |
|    105 | Rahul    | Nagpur      |      99991 |
+--------+----------+-------------+------------+
```
### 3.
```
Delete from emp_details where emp_salary <= 45000;
```
```
select * from emp_details;
+--------+----------+-------------+------------+
| emp_id | emp_name | emp_address | emp_salary |
+--------+----------+-------------+------------+
|    102 | Dipak    | NAshik      |      49000 |
|    103 | Rushi    | Dhule       |      75980 |
|    105 | Rahul    | Nagpur      |      99991 |
+--------+----------+-------------+------------+
```