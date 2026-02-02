# DBMS Lab Experiment – 1

**Subject:** Database Management Systems (DBMS)
**Experiment Title:** Study and Implementation of Basic SQL Commands
**Database Used:** MySQL (XAMPP)

---

## Aim

To understand and implement basic SQL commands including **DDL, DQL, DML, DCL, and TCL**, and to create a database with a table using appropriate data types and constraints.

---

## Software / Tools Required

* XAMPP (Apache + MySQL)
* MySQL Client / phpMyAdmin
* VS Code (for documentation)
* Operating System: Windows / macOS / Linux

---

## Theory

SQL (Structured Query Language) is used to store, retrieve, manipulate, and manage data in relational databases.

SQL commands are categorized into the following types:

### 1. DDL – Data Definition Language

Used to define and modify database structures.

* `CREATE`
* `DROP`
* `ALTER`
* `TRUNCATE`
* `RENAME`

### 2. DQL – Data Query Language

Used to retrieve data from the database.

* `SELECT`

> **Note:** `WHERE`, `GROUP BY`, `HAVING`, `ORDER BY`, `DISTINCT`, `LIMIT` are clauses of `SELECT`, not separate commands.

### 3. DML – Data Manipulation Language

Used to manipulate data inside tables.

* `INSERT`
* `UPDATE`
* `DELETE`

### 4. DCL – Data Control Language

Used to control access and permissions.

* `GRANT`
* `REVOKE`

### 5. TCL – Transaction Control Language

Used to manage transactions.

* `COMMIT`
* `ROLLBACK`
* `SAVEPOINT`

---

## Common Data Types in MySQL

| Data Type      | Description                    |
| -------------- | ------------------------------ |
| `CHAR(n)`      | Fixed-length character data    |
| `VARCHAR(n)`   | Variable-length character data |
| `INT`          | Integer values                 |
| `FLOAT`        | Decimal numbers                |
| `DATE`         | Date in `YYYY-MM-DD` format    |
| `DECIMAL(p,s)` | Fixed-point decimal numbers    |

---

## Constraints

| Constraint    | Description                             |
| ------------- | --------------------------------------- |
| `NOT NULL`    | Prevents NULL values                    |
| `UNIQUE`      | Ensures all values are unique           |
| `DEFAULT`     | Sets default value                      |
| `PRIMARY KEY` | Uniquely identifies each record         |
| `FOREIGN KEY` | References primary key of another table |
| `CHECK`       | Validates condition on values           |

---

## Procedure

### Step 1: Start MySQL

* Open XAMPP
* Start **Apache** and **MySQL**

### Step 2: Open MySQL Terminal

**For Windows:**

```bash
cd C:\xampp\mysql\bin
mysql -u root
```

**For macOS:**

```bash
/Applications/XAMPP/xamppfiles/bin/mysql -u root
```

---

## SQL Queries

### 1. Show Databases

```sql
SHOW DATABASES;
```

### 2. Create Database

```sql
CREATE DATABASE iilm;
USE iilm;
```

### 3. Create Table: Student

```sql
CREATE TABLE Student (
    student_id INT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    dob DATE NOT NULL,
    course VARCHAR(50) NOT NULL,
    fees DECIMAL(8,2) CHECK (fees > 0)
);
```

### 4. Insert Records

```sql
INSERT INTO Student VALUES
(1, 'Ali', 'Khan', 'ali@gmail.com', '2003-05-10', 'CSE', 45000),
(2, 'Aman', 'Verma', 'aman@gmail.com', '2002-08-12', 'IT', 42000),
(3, 'Riya', 'Sharma', 'riya@gmail.com', '2003-02-18', 'ECE', 40000),
(4, 'Neha', 'Singh', 'neha@gmail.com', '2002-11-25', 'CSE', 46000),
(5, 'Arjun', 'Mehta', 'arjun@gmail.com', '2003-07-30', 'ME', 38000);
```

### 5. Display Table Data

```sql
SELECT * FROM Student;
```

### 6. Describe Table Structure

```sql
DESC Student;
```

---

## Result

The database **iilm** and table **Student** were successfully created. Records were inserted and retrieved using SQL queries.

---

## Conclusion

This experiment helped in understanding basic SQL commands, data types, constraints, and table operations using MySQL.

---

## Viva Questions (Practice)

1. What is the difference between DDL and DML?
2. What is a PRIMARY KEY?
3. What is the use of CHECK constraint?
4. Difference between CHAR and VARCHAR?
5. What is a transaction?

---
