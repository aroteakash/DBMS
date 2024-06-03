# Assignment No 1

### **Aim :** Implementation of DDL commands (Create table , Alter table , Drop Table) of SQL on Student Database.

## 1. Create Table

### 1.  Create Database
```
 CREATE DATABASE Book;
```
```
O/P :
> show databases;
+--------------------+
| Database           |
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


### 2.  Create Table
```
CREATE TABLE student(
    rno INT, 
    fname VARCHAR(20),
    lname VARCHAR(20),
    age INT, 
    marks INT
    );
```
```code
O/P :

mysql> DESC database_name;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| rno   | int         | YES  |     | NULL    |       |
| fname | varchar(20) | YES  |     | NULL    |       |
| lname | varchar(20) | YES  |     | NULL    |       |
| age   | int         | YES  |     | NULL    |       |
| marks | int         | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
```
## 2. ALTER Table

### 1. ADD
```
ALTER table student ADD mname VARCHAR(20);
```

```
mysql> desc student;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| rno   | int         | YES  |     | NULL    |       |
| fname | varchar(20) | YES  |     | NULL    |       |
| lname | varchar(20) | YES  |     | NULL    |       |
| age   | int         | YES  |     | NULL    |       |
| marks | int         | YES  |     | NULL    |       |
| mname | varchar(20) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
```

### 2. DROP
```
ALTER table student DROP marks;
```

```
mysql> desc student;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| rno   | int         | YES  |     | NULL    |       |
| fname | varchar(20) | YES  |     | NULL    |       |
| lname | varchar(20) | YES  |     | NULL    |       |
| age   | int         | YES  |     | NULL    |       |
| mname | varchar(20) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
```

## 3. DROP Table

### 1. DROP Table
```
DROP table student;
```

```
mysql> show tables;
Empty set (0.16 sec)
```

### 2. DROP Databases
```
DROP database book;;
```

```
mysql> show databases;
+--------------------+
| Database           |
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