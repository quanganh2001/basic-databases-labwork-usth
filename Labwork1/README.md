# 1. Write SQL Statement to create a new database

```sql
CREATE DATABASE Company;
```

# 2. Write a SQL statement to create to set the default working database to “Company”

```sql
USE Company;
```

Right click schemas and click Set as Default Schemas

# 3. Write SQL statements to define tables of “Company” databases with contraints andcolumns illustrated by igures below. You should determine appropriate datatype for each column

```sql
CREATE TABLE Employee (
	Fname varchar(20),
    Minit varchar(10),
    Lname varchar(20),
    Ssn char(10),
    Bdate Date,
    Address varchar(100),
    Sex varchar(10),
    Salary decimal(10,2),
    Super_ssn char(10),
    Dno int
);

CREATE TABLE Department (
	Dname varchar(20),
    Dnumber int,
    Mgr_ssn varchar(10),
    Mgr_start_date datetime
);

CREATE TABLE Dept_locations (
	Dnumber int,
    Dlocation varchar(50)
);

CREATE TABLE Project (
	Pname varchar(100),
    Pnumber int,
    Plocation varchar(100),
    Dnum int
);

CREATE TABLE Works_on (
	Essn varchar (100),
    Pno int,
    Hours decimal(3,1)
);

CREATE TABLE Dependent (
	Essn char (10),
    Dependent_name varchar(50),
    Sex varchar(10),
    Bdate date,
    Relationship varchar(100)
);
```

You can type DESCRIBE name table to see table structure

Employee table structure

```
+-----------+---------------+------+-----+---------+-------+
| Field     | Type          | Null | Key | Default | Extra |
+-----------+---------------+------+-----+---------+-------+
| Fname     | varchar(20)   | YES  |     | NULL    |       |
| Minit     | varchar(10)   | YES  |     | NULL    |       |
| Lname     | varchar(20)   | YES  |     | NULL    |       |
| Ssn       | char(10)      | YES  |     | NULL    |       |
| Bdate     | date          | YES  |     | NULL    |       |
| Address   | varchar(100)  | YES  |     | NULL    |       |
| Sex       | varchar(10)   | YES  |     | NULL    |       |
| Salary    | decimal(10,2) | YES  |     | NULL    |       |
| Super_ssn | char(10)      | YES  |     | NULL    |       |
| Dno       | int           | YES  |     | NULL    |       |
+-----------+---------------+------+-----+---------+-------+
```

Department table structure

```
+----------------+-------------+------+-----+---------+-------+
| Field          | Type        | Null | Key | Default | Extra |
+----------------+-------------+------+-----+---------+-------+
| Dname          | varchar(20) | YES  |     | NULL    |       |
| Dnumber        | int         | YES  |     | NULL    |       |
| Mgr_ssn        | varchar(10) | YES  |     | NULL    |       |
| Mgr_start_date | datetime    | YES  |     | NULL    |       |
+----------------+-------------+------+-----+---------+-------+
```

Dept_locations table structure

```
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| Dnumber   | int         | YES  |     | NULL    |       |
| Dlocation | varchar(50) | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
```

Project table structure

```
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| Pname     | varchar(100) | YES  |     | NULL    |       |
| Pnumber   | int          | YES  |     | NULL    |       |
| Plocation | varchar(100) | YES  |     | NULL    |       |
| Dnum      | int          | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
```

Works_on table structure

```
+-------+--------------+------+-----+---------+-------+
| Field | Type         | Null | Key | Default | Extra |
+-------+--------------+------+-----+---------+-------+
| Essn  | varchar(100) | YES  |     | NULL    |       |
| Pno   | int          | YES  |     | NULL    |       |
| Hours | decimal(3,1) | YES  |     | NULL    |       |
+-------+--------------+------+-----+---------+-------+
```

Dependent table structure

```
+----------------+--------------+------+-----+---------+-------+
| Field          | Type         | Null | Key | Default | Extra |
+----------------+--------------+------+-----+---------+-------+
| Essn           | char(10)     | YES  |     | NULL    |       |
| Dependent_name | varchar(50)  | YES  |     | NULL    |       |
| Sex            | varchar(10)  | YES  |     | NULL    |       |
| Bdate          | date         | YES  |     | NULL    |       |
| Relationship   | varchar(100) | YES  |     | NULL    |       |
+----------------+--------------+------+-----+---------+-------+
```

# 4. Add column Partner_ssn to the table EMPLOYEE. This column indicates the SSN of spouse of each employee. For those who are now single, the value should be NULL.

```sql
ALTER TABLE Employee ADD Partner_ssn char(10);
DESCRIBE Employee;
```

Output:

```
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| Fname       | varchar(20)   | YES  |     | NULL    |       |
| Minit       | varchar(10)   | YES  |     | NULL    |       |
| Lname       | varchar(20)   | YES  |     | NULL    |       |
| Ssn         | char(10)      | YES  |     | NULL    |       |
| Bdate       | date          | YES  |     | NULL    |       |
| Address     | varchar(100)  | YES  |     | NULL    |       |
| Sex         | varchar(10)   | YES  |     | NULL    |       |
| Salary      | decimal(10,2) | YES  |     | NULL    |       |
| Super_ssn   | char(10)      | YES  |     | NULL    |       |
| Dno         | int           | YES  |     | NULL    |       |
| Partner_ssn | char(10)      | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
```

# 5. Write SQL statements to insert sample rows to these tables.

```sql
INSERT INTO Employee
	VALUES ('Linh', 'C', 'Nguyen', '0123456789', '2001-10-27', 'Cau Giay - Hanoi', 'F', '10000000', '123456789', 1, '13456789');
SELECT * FROM Employee;
```

Output:

```sql
+-------+-------+--------+------------+------------+------------------+------+-------------+-----------+------+-------------+
| Fname | Minit | Lname  | Ssn        | Bdate      | Address          | Sex  | Salary      | Super_ssn | Dno  | Partner_ssn |
+-------+-------+--------+------------+------------+------------------+------+-------------+-----------+------+-------------+
| Linh  | C     | Nguyen | 0123456789 | 2001-10-27 | Cau Giay - Hanoi | F    | 10000000.00 | 123456789 |    1 | 13456789    |
+-------+-------+--------+------------+------------+------------------+------+-------------+-----------+------+-------------+
```

# 6. Write SQL statements to delete the tables you created.

```sql
DROP TABLE Company;
```

Full source code:

```sql
-- 1. Write SQL Statement to create a new database
CREATE TABLE Company;
-- 2. Write a SQL statement to create to set the default working database to “Company”
USE Company;
-- Right click schemas and click Set as Default Schemas
-- 3. Write SQL statements to define tables of “Company” databases with contraints andcolumns illustrated by igures below. You should determine appropriate datatype for each column
CREATE TABLE Employee (
	Fname varchar(20),
    Minit varchar(10),
    Lname varchar(20),
    Ssn char(10),
    Bdate Date,
    Address varchar(100),
    Sex varchar(10),
    Salary decimal(10,2),
    Super_ssn char(10),
    Dno int
);

CREATE TABLE Department (
	Dname varchar(20),
    Dnumber int,
    Mgr_ssn varchar(10),
    Mgr_start_date datetime
);

CREATE TABLE Dept_locations (
	Dnumber int,
    Dlocation varchar(50)
);

CREATE TABLE Project (
	Pname varchar(100),
    Pnumber int,
    Plocation varchar(100),
    Dnum int
);

CREATE TABLE Works_on (
	Essn varchar (100),
    Pno int,
    Hours decimal(3,1)
);

CREATE TABLE Dependent (
	Essn char (10),
    Dependent_name varchar(50),
    Sex varchar(10),
    Bdate date,
    Relationship varchar(100)
);

-- 4. Add column Partner_ssn to the table EMPLOYEE. This column indicates the SSN of spouse of each employee. For those who are now single, the value should be NULL.
ALTER TABLE Employee ADD Partner_ssn char(10);
DESCRIBE Employee;

-- 5. Write SQL statements to insert sample rows to these tables.
INSERT INTO Employee
	VALUES ('Linh', 'C', 'Nguyen', '0123456789', '2001-10-27', 'Cau Giay - Hanoi', 'F', '10000000', '123456789', 1, '13456789');
SELECT * FROM Employee;

-- 6. Write SQL statements to delete the tables you created.
 DROP TABLE Company
```