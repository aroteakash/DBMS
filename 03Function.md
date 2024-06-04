# Assignment No 3

### **Aim :** Implementation of different types of function (Number function, Aggregate Function, Character Function ,Conversion Function,& date Function ) on  student database.
## 1. Basic

```
create table students (
    student_id integer primary key,
    first_name text not null,
    last_name text not null,
    birthdate date not null,
    gpa REAL,
    credits integer
);
```
```
insert into students (first_name, last_name, birthdate, gpa, credits) values
('John', 'Doe', '2000-01-15', 3.5, 30),
('Jane', 'Smith', '1999-05-20', 3.8, 60),
('Alice', 'Johnson', '2001-07-22', 3.2, 45),
('Bob', 'Brown', '1998-12-30', 3.6, 90),
('Charlie', 'Davis', '2000-09-10', 3.4, 75);

```
## 1. Number Function

-- Round the GPA to the nearest whole number
```
select student_id, first_name, ROUND(gpa) AS rounded_gpa from students;
```

-- Get the absolute value of the GPA difference from a perfect 4.0
```
select student_id, first_name, ABS(gpa - 4.0) AS gpa_diff from students;
```
## 2. Aggregate Function

-- Count the number of students
```
select COUNT(*) AS student_count from students;
```
-- Calculate the average GPA
```
select AVG(gpa) AS average_gpa from students;
```
-- Calculate the total credits
```
select SUM(credits) AS total_credits from students;
```
-- Find the highest GPA
```
select MAX(gpa) AS highest_gpa from students;
```
-- Find the lowest GPA
```
select MIN(gpa) AS lowest_gpa from students;
```

## 3. Character Function

```
-- Convert first names to uppercase
select student_id, UPPER(first_name) AS uppercase_first_name from students;
```
-- Convert last names to lowercase
```
select student_id, LOWER(last_name) AS lowercase_last_name from students;
```
-- Get the length of the first names
```
select student_id, LENGTH(first_name) AS first_name_length from students;
```
-- Get the first 3 characters of the last names
```
select student_id, SUBSTR(last_name, 1, 3) AS last_name_start from students;
```

## 4. Conversion Function

-- Convert GPA to an integer
```
select student_id, CAST(gpa AS integer) AS gpa_as_int from students;
```
-- Convert credits to a text string
```
select student_id, CAST(credits AS text) AS credits_as_text from students;

```
## 5. date Function

-- Get the year of birth
select student_id, first_name, STRFTIME('%Y', birthdate) AS birth_year from students;
```
-- Get the current date
select date('now') AS current_date;
```
-- Calculate age of students
```
select student_id, first_name, 
    (CAST(STRFTIME('%Y', 'now') AS integer) - CAST(STRFTIME('%Y', birthdate) AS integer)) AS age 
from students;
```
-- Calculate days until next birthday
```
select student_id, first_name, 
    (JULIANDAY(date(STRFTIME('%Y', 'now') || '-' || STRFTIME('%m-%d', birthdate))) - JULIANDAY('now')) AS days_until_birthday
from students
where date(STRFTIME('%Y', 'now') || '-' || STRFTIME('%m-%d', birthdate)) >= date('now')
UNION
select student_id, first_name, 
    (JULIANDAY(date((CAST(STRFTIME('%Y', 'now') AS integer) + 1) || '-' || STRFTIME('%m-%d', birthdate))) - JULIANDAY('now')) AS days_until_birthday
from students
where date(STRFTIME('%Y', 'now') || '-' || STRFTIME('%m-%d', birthdate)) < date('now');
```