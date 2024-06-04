# Assignment No 1

### **Aim :** Implementation of DDL commands (create table , alter table , Drop table) of SQL on Student database.

## 1. create table

### 1.  create database
```
 create database Book;
```
```
O/P :
> show databases;
+--------------------+
| database           |
+--------------------+
| fymca              |
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| world              |
+--------------------+
```


### 2.  create table
```
create table student(
    rno int, 
    fname varchar(20),
    lname varchar(20),
    age int, 
    marks int
    );
```
```
O/P :

mysql> desc database_name;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| rno   | int         | YES  |     | null    |       |
| fname | varchar(20) | YES  |     | null    |       |
| lname | varchar(20) | YES  |     | null    |       |
| age   | int         | YES  |     | null    |       |
| marks | int         | YES  |     | null    |       |
+-------+-------------+------+-----+---------+-------+
```
## 2. alter table

### 1. ADD
```
alter table student ADD mname varchar(20);
```

```
mysql> desc student;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| rno   | int         | YES  |     | null    |       |
| fname | varchar(20) | YES  |     | null    |       |
| lname | varchar(20) | YES  |     | null    |       |
| age   | int         | YES  |     | null    |       |
| marks | int         | YES  |     | null    |       |
| mname | varchar(20) | YES  |     | null    |       |
+-------+-------------+------+-----+---------+-------+
```

### 2. DROP
```
alter table student DROP marks;
```

```
mysql> desc student;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| rno   | int         | YES  |     | null    |       |
| fname | varchar(20) | YES  |     | null    |       |
| lname | varchar(20) | YES  |     | null    |       |
| age   | int         | YES  |     | null    |       |
| mname | varchar(20) | YES  |     | null    |       |
+-------+-------------+------+-----+---------+-------+
```

## 3. DROP table

### 1. DROP table
```
DROP table student;
```

```
mysql> show tables;
Empty set (0.16 sec)
```

### 2. DROP databases
```
DROP database book;;
```

```
mysql> show databases;
+--------------------+
| database           |
+--------------------+
| fymca              |
| information_schema |
| mysql              |
| performance_schema |
| sakila             |
| sys                |
| world              |
+--------------------+
```