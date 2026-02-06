
# DBMS Lab Experiment – 2

## Experiment Title

Study and Implementation of SQL Data Query Language (DQL)

---

## Aim

To study and implement **Data Query Language (DQL)** commands in SQL
using the **SELECT** statement and its clauses.

---

## Software / Tools Used

- Database: **MySQL**
- Interface: **XAMPP / phpMyAdmin / MySQL Terminal**
- Operating System: **macOS**
- Editor: **VS Code**

---

## Theory

Data Query Language (DQL) is used to retrieve data from a database.
The SELECT command is the only DQL command and is used with clauses such as
WHERE, DISTINCT, BETWEEN, IN, and ORDER BY.

---

## Table Structure

### Table Name: Movie

| Column Name      | Data Type        | Constraints        |
|------------------|------------------|--------------------|
| MovieID          | CHAR(3)          | PRIMARY KEY        |
| MovieName        | VARCHAR(30)      | NOT NULL, UNIQUE   |
| Category         | VARCHAR(15)      | NOT NULL           |
| ReleaseDate      | DATE             | NULL allowed       |
| ProductionCost   | DECIMAL(10,2)    | —                  |
| BusinessCost     | DECIMAL(10,2)    | —                  |

---

## SQL Commands Used

- CREATE
- INSERT
- SELECT

---

## Experiment Description

### Step 1: Create Database

```sql
CREATE DATABASE iilm;
USE iilm;
CREATE TABLE Movie (
    MovieID CHAR(3) PRIMARY KEY,
    MovieName VARCHAR(30) NOT NULL UNIQUE,
    Category VARCHAR(15) NOT NULL,
    ReleaseDate DATE,
    ProductionCost DECIMAL(10,2),
    BusinessCost DECIMAL(10,2)
);
INSERT INTO Movie VALUES
('001', 'Hindi_Movie',   'Musical',  '2018-04-23', 124500, 130000),
('002', 'Tamil_Movie',   'Action',   '2016-05-17', 112000, 118000),
('003', 'English_Movie', 'Horror',   '2017-08-06', 245000, 360000),
('004', 'Bengali_Movie', 'Adventure','2017-01-04', 72000,  100000),
('005', 'Telugu_Movie',  'Action',    NULL,        100000, NULL),
('006', 'Punjabi_Movie', 'Comedy',    NULL,        30500,  NULL);
---

## Queries and Results

### (a) List business done by the movies  
(Display only MovieID, MovieName and BusinessCost)

MariaDB [alqama]> SELECT MovieID, MovieName, BusinessCost
 -> FROM Movie;
+---------+---------------+--------------+
| MovieID | MovieName     | BusinessCost |
+---------+---------------+--------------+
| 001     | Hindi_Movie   |    130000.00 |
| 002     | Tamil_Movie   |    118000.00 |
| 003     | English_Movie |    360000.00 |
| 004     | Bengali_Movie |    100000.00 |
| 005     | Telugu_Movie  |         NULL |
| 006     | Punjabi_Movie |         NULL |
+---------+---------------+--------------+

(b) List different categories of movies
(USE DISTINCT keyword)
MariaDB [alqama]> SELECT DISTINCT Category
    -> FROM Movie;
+-----------+
| Category  |
+-----------+
| Musical   |
| Action    |
| Horror    |
| Adventure |
| Comedy    |
+-----------+

(c) Find the net profit of each movie

Net Profit = BusinessCost − ProductionCost
Label the column as NetProfit
MariaDB [alqama]> SELECT 
    ->     MovieID,
    ->     MovieName,
    ->     (BusinessCost - ProductionCost) AS NetProfit
    -> FROM Movie;
+---------+---------------+-----------+
| MovieID | MovieName     | NetProfit |
+---------+---------------+-----------+
| 001     | Hindi_Movie   |   5500.00 |
| 002     | Tamil_Movie   |   6000.00 |
| 003     | English_Movie | 115000.00 |
| 004     | Bengali_Movie |  28000.00 |
| 005     | Telugu_Movie  |      NULL |
| 006     | Punjabi_Movie |      NULL |
+---------+---------------+-----------+

(d) List movies with ProductionCost

Greater than 80,000 and less than 1,25,000
MariaDB [alqama]> SELECT MovieID, MovieName, ProductionCost
    -> FROM Movie
    -> WHERE ProductionCost > 80000
    ->   AND ProductionCost < 125000;
+---------+--------------+----------------+
| MovieID | MovieName    | ProductionCost |
+---------+--------------+----------------+
| 001     | Hindi_Movie  |      124500.00 |
| 002     | Tamil_Movie  |      112000.00 |
| 005     | Telugu_Movie |      100000.00 |
+---------+--------------+----------------+

(e) List movies in Comedy or Action category

MariaDB [alqama]> SELECT MovieID, MovieName, Category
    -> FROM Movie
    -> WHERE Category IN ('Comedy', 'Action');
+---------+---------------+----------+
| MovieID | MovieName     | Category |
+---------+---------------+----------+
| 002     | Tamil_Movie   | Action   |
| 005     | Telugu_Movie  | Action   |
| 006     | Punjabi_Movie | Comedy   |
+---------+---------------+----------+

f) List movies which have not been released yet

(ReleaseDate is NULL)
MariaDB [alqama]> SELECT MovieID, MovieName
    -> FROM Movie
    -> WHERE ReleaseDate IS NULL;
+---------+---------------+
| MovieID | MovieName     |
+---------+---------------+
| 005     | Telugu_Movie  |
| 006     | Punjabi_Movie |
+---------+---------------+
