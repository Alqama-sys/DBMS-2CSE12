# LAB ASSIGNMENT 4

> **Date:** 09/FEBRUARY/2026  
> **Database:** ALQAMA SAEED
___

## 📋 Objective

Objective

Create and manipulate the EMPLOYEE table to perform the following operations:
Retrieve employee records using conditional operators and date comparisons
Apply pattern matching using LIKE operator
Filter records using logical operators (AND, OR, NOT)
Compute annual salary and total salary using arithmetic expressions
Sort records using ORDER BY clause
Update salary records based on specified conditions
Perform aggregate and string functions on employee data
This experiment focuses on practical implementation of SQL queries for data retrieval and modification.

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

---

### QUERY 1. Display the list of employees who have joined the company before 30th June 80 or after 31st Dec 81

```sql
SELECT *
FROM EMPLOYEE
WHERE HIREDATE < '1980-06-30'
   OR HIREDATE > '1981-12-31';
```

**Output:**

```text
+-------+--------+---------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB     | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+---------+------+------------+---------+------+--------+
|  7788 | SCOTT  | ANALYST | 7566 | 1982-12-09 | 3000.00 | NULL |     40 |
|  7876 | ADAMS  | CLERK   | 7788 | 1983-01-12 | 1100.00 | NULL |     20 |
|  7934 | MILLER | CLERK   | 7782 | 1982-01-23 | 1300.00 | NULL |     10 |
+-------+--------+---------+------+------------+---------+------+--------+
3 rows in set (0.007 sec)
```

**Verification:**

### QUERY 2. Display the names of employees whose names have second alphabet A in their names

```sql
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```

**Output:**

```text
MariaDB [alqama]> 
MariaDB [alqama]> SELECT ENAME
    -> FROM EMPLOYEE
    -> WHERE ENAME LIKE '_A%';
+--------+
| ENAME  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+
3 rows in set (0.004 sec)
```

### QUERY 3. Display the names of employees whose name is exactly five characters in length

```sql
SELECT ENAME
FROM EMPLOYEE
WHERE LENGTH(ENAME) = 5;
```

**Output:**

```text

MariaDB [alqama]> SELECT ENAME
    -> FROM EMPLOYEE
    -> WHERE LENGTH(ENAME) = 5;
+-------+
| ENAME |
+-------+
| SMITH |
| ALLEN |
| JONES |
| BLAKE |
| CLARK |
| SCOTT |
| ADAMS |
| JAMES |
+-------+
8 rows in set (0.005 sec)
```

### QUERY 4. Display the names of employees whose names have second alphabet A in their names

```sql
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```

**Output:**

```text
MariaDB [alqama]> SELECT ENAME
    -> FROM EMPLOYEE
    -> WHERE ENAME LIKE '_A%';
+--------+
| ENAME  |
+--------+
| WARD   |
| MARTIN |
| JAMES  |
+--------+
3 rows in set (0.001 sec)
```

### QUERY 5. Display the names of employees who are not working as salesman or clerk or analyst

```sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
```

**Output:**

```text
MariaDB [alqama]> SELECT ENAME
    -> FROM EMPLOYEE
    -> WHERE JOB NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
+-------+
| ENAME |
+-------+
| JONES |
| BLAKE |
| CLARK |
| KING  |
+-------+
4 rows in set (0.003 sec)
```

### QUERY 6. Display the name of the employee along with their annual salary (sal*12). The name of the employee earning highest salary should appear first

```sql
SELECT ENAME,
       SAL * 12 AS ANNUAL_SALARY
FROM EMPLOYEE
ORDER BY ANNUAL_SALARY DESC;
```

**Output:**

```text
MariaDB [alqama]> SELECT ENAME,
    ->        SAL * 12 AS ANNUAL_SALARY
    -> FROM EMPLOYEE
    -> ORDER BY ANNUAL_SALARY DESC;
+--------+---------------+
| ENAME  | ANNUAL_SALARY |
+--------+---------------+
| KING   |      60000.00 |
| SCOTT  |      36000.00 |
| FORD   |      36000.00 |
| JONES  |      35700.00 |
| BLAKE  |      34200.00 |
| CLARK  |      29400.00 |
| ALLEN  |      19200.00 |
| TURNER |      18000.00 |
| MILLER |      15600.00 |
| MARTIN |      15000.00 |
| WARD   |      15000.00 |
| ADAMS  |      13200.00 |
| JAMES  |      11400.00 |
| SMITH  |       9600.00 |
+--------+---------------+
14 rows in set (0.005 sec)
```

### QUERY 7. Display name, sal, hra, pf, da, totalsal for each employee. The output should be in the order of total sal, hra 15% of sal, da 10% of sal, pf 5% of sal. Total salary will be (sal*hra*da)-pf

```sql
SELECT ENAME,
       SAL,
       SAL * 0.15 AS HRA,
       SAL * 0.10 AS DA,
       SAL * 0.05 AS PF,
       (SAL + (SAL * 0.15) + (SAL * 0.10) - (SAL * 0.05)) AS TOTALSAL
FROM EMPLOYEE
ORDER BY TOTALSAL;
```

**Output:**

```text
MariaDB [alqama]> SELECT ENAME,
    ->        SAL,
    ->        SAL * 0.15 AS HRA,
    ->        SAL * 0.10 AS DA,
    ->        SAL * 0.05 AS PF,
    ->        (SAL + (SAL * 0.15) + (SAL * 0.10) - (SAL * 0.05)) AS TOTALSAL
    -> FROM EMPLOYEE
    -> ORDER BY TOTALSAL;
+--------+---------+----------+----------+----------+-----------+
| ENAME  | SAL     | HRA      | DA       | PF       | TOTALSAL  |
+--------+---------+----------+----------+----------+-----------+
| SMITH  |  800.00 | 120.0000 |  80.0000 |  40.0000 |  960.0000 |
| JAMES  |  950.00 | 142.5000 |  95.0000 |  47.5000 | 1140.0000 |
| ADAMS  | 1100.00 | 165.0000 | 110.0000 |  55.0000 | 1320.0000 |
| WARD   | 1250.00 | 187.5000 | 125.0000 |  62.5000 | 1500.0000 |
| MARTIN | 1250.00 | 187.5000 | 125.0000 |  62.5000 | 1500.0000 |
| MILLER | 1300.00 | 195.0000 | 130.0000 |  65.0000 | 1560.0000 |
| TURNER | 1500.00 | 225.0000 | 150.0000 |  75.0000 | 1800.0000 |
| ALLEN  | 1600.00 | 240.0000 | 160.0000 |  80.0000 | 1920.0000 |
| CLARK  | 2450.00 | 367.5000 | 245.0000 | 122.5000 | 2940.0000 |
| BLAKE  | 2850.00 | 427.5000 | 285.0000 | 142.5000 | 3420.0000 |
| JONES  | 2975.00 | 446.2500 | 297.5000 | 148.7500 | 3570.0000 |
| FORD   | 3000.00 | 450.0000 | 300.0000 | 150.0000 | 3600.0000 |
| SCOTT  | 3000.00 | 450.0000 | 300.0000 | 150.0000 | 3600.0000 |
| KING   | 5000.00 | 750.0000 | 500.0000 | 250.0000 | 6000.0000 |
+--------+---------+----------+----------+----------+-----------+
```

### QUERY 8. Update the salary of each employee by 10% increment who are not eligible for commission

```sql
UPDATE EMPLOYEE
SET SAL = SAL * 1.10
WHERE COMM IS NULL;
```

**Output:**

```text
MariaDB [alqama]> UPDATE EMPLOYEE
    -> SET SAL = SAL * 1.10
    -> WHERE COMM IS NULL;
Query OK, 10 rows affected (0.005 sec)
Rows matched: 10  Changed: 10  Warnings: 0
```

### QUERY 9. Display those employees whose salary is more than 3000 after giving 20% increment

```sql
SELECT *
FROM EMPLOYEE
WHERE SAL * 1.20 > 3000;
```

**Output:**

```text

MariaDB [alqama]> SELECT *
    -> FROM EMPLOYEE
    -> WHERE SAL * 1.20 > 3000;
+-------+-------+-----------+------+------------+---------+------+--------+
| EMPNO | ENAME | JOB       | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+-------+-----------+------+------------+---------+------+--------+
|  7566 | JONES | MANAGER   | 7839 | 1981-04-02 | 3272.50 | NULL |     20 |
|  7698 | BLAKE | MANAGER   | 7839 | 1981-05-01 | 3135.00 | NULL |     30 |
|  7782 | CLARK | MANAGER   | 7839 | 1981-06-09 | 2695.00 | NULL |     20 |
|  7788 | SCOTT | ANALYST   | 7566 | 1982-12-09 | 3300.00 | NULL |     40 |
|  7839 | KING  | PRESIDENT | NULL | 1981-11-17 | 5500.00 | NULL |     20 |
|  7902 | FORD  | ANALYST   | 7566 | 1981-12-03 | 3300.00 | NULL |     20 |
+-------+-------+-----------+------+------------+---------+------+--------+
6 rows in set (0.002 sec)
```

### QUERY 10. Display those employees whose salary contains atleast 3 digits

```sql
SELECT *
FROM EMPLOYEE
WHERE SAL >= 100;
```

**Output:**

```text

MariaDB [alqama]> SELECT *
    -> FROM EMPLOYEE
    -> WHERE SAL >= 100;
+-------+--------+-----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  880.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  300.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 3272.50 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 3135.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2695.00 |    NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3300.00 |    NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5500.00 |    NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1210.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 | 1045.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3300.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1430.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
14 rows in set (0.007 sec)
```

**Conclusion:**

Thus, various SQL queries were successfully executed using conditional operators, pattern matching, arithmetic expressions, sorting, and update statements. The experiment demonstrated practical implementation of WHERE, LIKE, ORDER BY, aggregate calculations within expressions, and UPDATE operations on the EMPLOYEE table. The results verified correct data retrieval and modification based on specified criteria.