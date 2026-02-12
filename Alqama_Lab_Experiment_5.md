# LAB ASSIGNMENT 5

> **Date:** 11/FEBRUARY/2026  
> **Database:** ALQAMA SAEED
___

(Using Aggregate & String Functions)

## 📋 Aim / Objective

To study and implement SQL aggregate and string functions for data analysis on employee records.

___

## Table Structures

### Table 1: DEPARTMENT

| Field  | Type        | Null | Key | Default | Extra |
|--------|-------------|------|-----|---------|-------|
| DEPTNO | INT(2)      | NO   | PRI | NULL    |       |
| DNAME  | VARCHAR(15) | NO   |     | NULL    |       |

### Table 2: EMPLOYEE

| Field    | Type        | Null | Key | Default | Extra       |
|----------|-------------|------|-----|---------|-------------|
| EMPNO    | INT(4)      | NO   | PRI | NULL    |             |
| ENAME    | VARCHAR(20) | NO   |     | NULL    |             |
| JOB      | VARCHAR(20) | YES  |     | NULL    |             |
| MGR      | INT(4)      | YES  |     | NULL    |             |
| HIREDATE | DATE        | YES  |     | NULL    |             |
| SAL      | INT(10)     | YES  |     | NULL    |             |
| COMM     | INT(7)      | YES  |     | NULL    |             |
| DEPTNO   | INT(2)      | YES  | MUL | NULL    | Foreign Key |

___

### DEPARTMENT Table

| DEPTNO | DNAME      |
|--------|------------|
| 10     | RESEARCH   |
| 20     | ACCOUNTING |
| 30     | SALES      |
| 40     | OPERATIONS |

### EMPLOYEE Table

| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
|-------|--------|-----------|------|------------|------|------|--------|
| 7369  | SMITH  | CLERK     | 7902 | 1980-12-17 | 800  | NULL | 20     |
| 7499  | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 | 300  | 30     |
| 7521  | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 | 300  | 30     |
| 7566  | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL | 20     |
| 7654  | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 | 30     |
| 7698  | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL | 30     |
| 7782  | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL | 20     |
| 7788  | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL | 40     |
| 7839  | KING   | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL | 20     |
| 7844  | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 | 0    | 30     |
| 7876  | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1100 | NULL | 20     |
| 7900  | JAMES  | CLERK     | 7698 | 1981-12-03 | 950  | NULL | 30     |
| 7902  | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL | 20     |
| 7934  | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL | 10     |

### QUERY 1. Display the total number of employee working in the company

```sql
SELECT COUNT(*) AS TOTAL_EMPLOYEES
FROM EMPLOYEE;
```

**Output:**

```text
MariaDB [alqama]> SELECT COUNT(*) AS TOTAL_EMPLOYEES
    -> FROM EMPLOYEE;
+-----------------+
| TOTAL_EMPLOYEES |
+-----------------+
|              14 |
+-----------------+
1 row in set (0.040 sec)
```

### QUERY 2. Display the total salary being paid to all employees

```sql
SELECT SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE;
```

**Output:**

```text
MariaDB [alqama]> SELECT SUM(SAL) AS TOTAL_SALARY
    -> FROM EMPLOYEE;
+--------------+
| TOTAL_SALARY |
+--------------+
|     31367.50 |
+--------------+
1 row in set (0.010 sec)
```

### QUERY 3.Display the maximum salary from employee table

```sql
SELECT MAX(SAL) AS MAX_SALARY
FROM EMPLOYEE;
```

**Output:**

```text
MariaDB [alqama]> SELECT MAX(SAL) AS MAX_SALARY
    -> FROM EMPLOYEE;
+------------+
| MAX_SALARY |
+------------+
|    5500.00 |
+------------+
1 row in set (0.004 sec)
```

### QUERY 4.Display the minimum salary from employee table

```sql
SELECT MIN(SAL) AS MIN_SALARY
FROM EMPLOYEE;
```

**Output:**

```text
MariaDB [alqama]> SELECT MIN(SAL) AS MIN_SALARY
    -> FROM EMPLOYEE;
+------------+
| MIN_SALARY |
+------------+
|     880.00 |
+------------+
1 row in set (0.004 sec)
```

### QUERY 5. Display the average salary from employee table

```sql
SELECT AVG(SAL) AS AVERAGE_SALARY
FROM EMPLOYEE;
```

**Output:**

```text
MariaDB [alqama]> SELECT AVG(SAL) AS AVERAGE_SALARY
    -> FROM EMPLOYEE;
+----------------+
| AVERAGE_SALARY |
+----------------+
|    2240.535714 |
+----------------+
1 row in set (0.002 sec)
```

### QUERY 6. Display the maximum salary being paid to clerk

```sql
SELECT MAX(SAL) AS MAX_CLERK_SALARY
FROM EMPLOYEE
WHERE JOB = 'CLERK';
```

**Output:**

```text
MariaDB [alqama]> SELECT MAX(SAL) AS MAX_CLERK_SALARY
    -> FROM EMPLOYEE
    -> WHERE JOB = 'CLERK';
+------------------+
| MAX_CLERK_SALARY |
+------------------+
|          1430.00 |
+------------------+
1 row in set (0.006 sec)
```

### QUERY 7.Display the maximum salary being paid in dept no 20

```sql
SELECT MAX(SAL) AS MAX_DEPT20_SALARY
FROM EMPLOYEE
WHERE DEPTNO = 20;
```

**Output:**

```text
MariaDB [alqama]> SELECT MAX(SAL) AS MAX_DEPT20_SALARY
    -> FROM EMPLOYEE
    -> WHERE DEPTNO = 20;
+-------------------+
| MAX_DEPT20_SALARY |
+-------------------+
|           5500.00 |
+-------------------+
1 row in set (0.008 sec)
```

### QUERY 8. Display the minimum salary paid to any salesman

```sql
SELECT MIN(SAL) AS MIN_SALESMAN_SALARY
FROM EMPLOYEE
WHERE JOB = 'SALESMAN';
```

**Output:**

```text
MariaDB [alqama]> SELECT MIN(SAL) AS MIN_SALESMAN_SALARY
    -> FROM EMPLOYEE
    -> WHERE JOB = 'SALESMAN';
+---------------------+
| MIN_SALESMAN_SALARY |
+---------------------+
|             1250.00 |
+---------------------+
1 row in set (0.003 sec)
```

### QUERY 9. Display the average salary drawn by managers

```sql
SELECT AVG(SAL) AS AVG_MANAGER_SALARY
FROM EMPLOYEE
WHERE JOB = 'MANAGER';
```

**Output:**

```text
MariaDB [alqama]> SELECT AVG(SAL) AS AVG_MANAGER_SALARY
    -> FROM EMPLOYEE
    -> WHERE JOB = 'MANAGER';
+--------------------+
| AVG_MANAGER_SALARY |
+--------------------+
|        3034.166667 |
+--------------------+
1 row in set (0.002 sec)
```

### QUERY 10.Display the total salary drawn by analyst working in dept no 40

```sql
SELECT SUM(SAL) AS TOTAL_ANALYST_SALARY
FROM EMPLOYEE
WHERE JOB = 'ANALYST'
AND DEPTNO = 40;
```

**Output:**

```text
MariaDB [alqama]> SELECT SUM(SAL) AS TOTAL_ANALYST_SALARY
    -> FROM EMPLOYEE
    -> WHERE JOB = 'ANALYST'
    -> AND DEPTNO = 40;
+----------------------+
| TOTAL_ANALYST_SALARY |
+----------------------+
|              3300.00 |
+----------------------+
1 row in set (0.005 sec)
```

### QUERY 11. Display the names of the employee in Uppercase

```sql
SELECT UPPER(ENAME) AS EMPLOYEE_NAME
FROM EMPLOYEE;
```

**Output:**

```text
MariaDB [alqama]> SELECT UPPER(ENAME) AS EMPLOYEE_NAME
    -> FROM EMPLOYEE;
+---------------+
| EMPLOYEE_NAME |
+---------------+
| SMITH         |
| ALLEN         |
| WARD          |
| JONES         |
| MARTIN        |
| BLAKE         |
| CLARK         |
| SCOTT         |
| KING          |
| TURNER        |
| ADAMS         |
| JAMES         |
| FORD          |
| MILLER        |
+---------------+
14 rows in set (0.007 sec)
```

### QUERY 12. Display the names of the employee in Lowercase

```sql
SELECT LOWER(ENAME) AS EMPLOYEE_NAME
FROM EMPLOYEE;
```

**Output:**

```text
MariaDB [alqama]> SELECT LOWER(ENAME) AS EMPLOYEE_NAME
    -> FROM EMPLOYEE;
+---------------+
| EMPLOYEE_NAME |
+---------------+
| smith         |
| allen         |
| ward          |
| jones         |
| martin        |
| blake         |
| clark         |
| scott         |
| king          |
| turner        |
| adams         |
| james         |
| ford          |
| miller        |
+---------------+
14 rows in set (0.003 sec)
```

### QUERY 13. Display the names of the employee in Proper case

```sql
SELECT CONCAT(UPPER(LEFT(ENAME,1)),
              LOWER(SUBSTRING(ENAME,2))) AS PROPER_NAME
FROM EMPLOYEE;
```

**Output:**

```text
MariaDB [alqama]> SELECT CONCAT(UPPER(LEFT(ENAME,1)),
    ->               LOWER(SUBSTRING(ENAME,2))) AS PROPER_NAME
    -> FROM EMPLOYEE;
+-------------+
| PROPER_NAME |
+-------------+
| Smith       |
| Allen       |
| Ward        |
| Jones       |
| Martin      |
| Blake       |
| Clark       |
| Scott       |
| King        |
| Turner      |
| Adams       |
| James       |
| Ford        |
| Miller      |
+-------------+
14 rows in set (0.003 sec)
```

### QUERY 14. Display the length of Your name using appropriate function

```sql
SELECT LENGTH('MOHDASIF') AS NAME_LENGTH;
```

**Output:**

```text
MariaDB [alqama]> SELECT LENGTH('MOHDASIF') AS NAME_LENGTH;
+-------------+
| NAME_LENGTH |
+-------------+
|           8 |
+-------------+
1 row in set (0.001 sec)
```

### QUERY 15. Display the length of all the employee names

```sql
SELECT ENAME,
       LENGTH(ENAME) AS NAME_LENGTH
FROM EMPLOYEE;
```

**Output:**

```text

MariaDB [alqama]> SELECT ENAME,
    ->        LENGTH(ENAME) AS NAME_LENGTH
    -> FROM EMPLOYEE;
+--------+-------------+
| ENAME  | NAME_LENGTH |
+--------+-------------+
| SMITH  |           5 |
| ALLEN  |           5 |
| WARD   |           4 |
| JONES  |           5 |
| MARTIN |           6 |
| BLAKE  |           5 |
| CLARK  |           5 |
| SCOTT  |           5 |
| KING   |           4 |
| TURNER |           6 |
| ADAMS  |           5 |
| JAMES  |           5 |
| FORD   |           4 |
| MILLER |           6 |
+--------+-------------+
14 rows in set (0.003 sec)
```

**Conclusion**
Thus, SQL aggregate and string functions were successfully applied to analyze employee data. The experiment demonstrated the use of functions such as COUNT, SUM, AVG, MAX, MIN, UPPER, LOWER, and LENGTH for summarizing data, performing calculations, and formatting text efficiently.
