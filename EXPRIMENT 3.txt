
C:\xampp\mysql\bin>mysql -u root -p
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 11
Server version: 10.4.32-MariaDB mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| 2cse11             |
| collage            |
| college            |
| expremenr1         |
| iilm               |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| rakesh             |
| test               |
+--------------------+
11 rows in set (0.001 sec)

MariaDB [(none)]> show tables;
ERROR 1046 (3D000): No database selected
MariaDB [(none)]> create databases rakesh;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'databases rakesh' at line 1
MariaDB [(none)]> create database Rakesh;
ERROR 1007 (HY000): Can't create database 'rakesh'; database exists
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| 2cse11             |
| collage            |
| college            |
| expremenr1         |
| iilm               |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| rakesh             |
| test               |
+--------------------+
11 rows in set (0.001 sec)

MariaDB [(none)]> create databases Rakesh;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'databases Rakesh' at line 1
MariaDB [(none)]> create database Rakesh;
ERROR 1007 (HY000): Can't create database 'rakesh'; database exists
MariaDB [(none)]> use rakesh
Database changed
MariaDB [rakesh]> show databases;
+--------------------+
| Database           |
+--------------------+
| 2cse11             |
| collage            |
| college            |
| expremenr1         |
| iilm               |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| rakesh             |
| test               |
+--------------------+
11 rows in set (0.001 sec)

MariaDB [rakesh]> use rakesh;
Database changed
MariaDB [rakesh]> create table department(deptno int(2) primary key auto_increment,dname varchar(15) not null;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '' at line 1
MariaDB [rakesh]> create table department(deptno int(2) primary key auto_increment,dname varchar(15) not null);
Query OK, 0 rows affected (0.019 sec)

MariaDB [rakesh]> show tables;
+------------------+
| Tables_in_rakesh |
+------------------+
| department       |
+------------------+
1 row in set (0.001 sec)

MariaDB [rakesh]> desc department;
+--------+-------------+------+-----+---------+----------------+
| Field  | Type        | Null | Key | Default | Extra          |
+--------+-------------+------+-----+---------+----------------+
| deptno | int(2)      | NO   | PRI | NULL    | auto_increment |
| dname  | varchar(15) | NO   |     | NULL    |                |
+--------+-------------+------+-----+---------+----------------+
2 rows in set (0.036 sec)

MariaDB [rakesh]> INSERT INTO DEPARTMENT VALUES(10,"RESEARCH"),(20,"ACCOUNTING"),(30,"SALES"),(40,"OPERATIONS");
Query OK, 4 rows affected (0.066 sec)
Records: 4  Duplicates: 0  Warnings: 0

MariaDB [rakesh]> SELECTE *FROM DEPARTMENT;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'SELECTE *FROM DEPARTMENT' at line 1
MariaDB [rakesh]> SELECT *FROM DEPARTMENT;
+--------+------------+
| deptno | dname      |
+--------+------------+
|     10 | RESEARCH   |
|     20 | ACCOUNTING |
|     30 | SALES      |
|     40 | OPERATIONS |
+--------+------------+
4 rows in set (0.001 sec)

MariaDB [rakesh]> create table employee(EMPO int(4) primary key auto_increment, empname varchar(15) not null, job varchar(20), mgr int(4), hiredate date, sal int(10), comm int(2), constraint fk_deptno foreign key(deptno) references department(deptno));
ERROR 1072 (42000): Key column 'deptno' doesn't exist in table
MariaDB [rakesh]> create table employee(EMPO int(4) primary key auto_increment, ename varchar(20) not null, job varchar(20), mgr int(4), hiredate date, sal int(10), comm int(2),DEPTNO INT(2), constraint fk_deptno foreign key(deptno) references department(deptno));
Query OK, 0 rows affected (0.053 sec)

MariaDB [rakesh]> SHOW TABLES;
+------------------+
| Tables_in_rakesh |
+------------------+
| department       |
| employee         |
+------------------+
2 rows in set (0.001 sec)

MariaDB [rakesh]> DESC EMPLOYEE;
+----------+-------------+------+-----+---------+----------------+
| Field    | Type        | Null | Key | Default | Extra          |
+----------+-------------+------+-----+---------+----------------+
| EMPO     | int(4)      | NO   | PRI | NULL    | auto_increment |
| ename    | varchar(20) | NO   |     | NULL    |                |
| job      | varchar(20) | YES  |     | NULL    |                |
| mgr      | int(4)      | YES  |     | NULL    |                |
| hiredate | date        | YES  |     | NULL    |                |
| sal      | int(10)     | YES  |     | NULL    |                |
| comm     | int(2)      | YES  |     | NULL    |                |
| DEPTNO   | int(2)      | YES  | MUL | NULL    |                |
+----------+-------------+------+-----+---------+----------------+
8 rows in set (0.040 sec)

MariaDB [rakesh]> INSERT INTO EMPLOYEE VALUES(7369,"SMITH","CLERK",7902,"1980-12-17",800,NULL,20);
Query OK, 1 row affected (0.010 sec)

MariaDB [rakesh]> SELECT *FROM EMPLOYEE;
+------+-------+-------+------+------------+------+------+--------+
| EMPO | ename | job   | mgr  | hiredate   | sal  | comm | DEPTNO |
+------+-------+-------+------+------------+------+------+--------+
| 7369 | SMITH | CLERK | 7902 | 1980-12-17 |  800 | NULL |     20 |
+------+-------+-------+------+------------+------+------+--------+
1 row in set (0.001 sec)

MariaDB [rakesh]> INSERT INTO employee VALUES
    ->     (7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30),
    ->     (7521,'WARD','SALESMAN',7698,'1981-02-22',1250,300,30),
    ->      (7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20),
    ->      (7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30),
    ->      (7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30),
    ->      (7782,'CLARK','MANAGER',7839,'1981-06-09',2450,NULL,20),
    ->      (7788,'SCOTT','ANALYST',7566,'1982-12-09',3000,NULL,40),
    ->      (7839,'KING','PRESEDENT',NULL,'1981-11-17',5000,NULL,20),
    ->      (7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30),
    ->      (7876,'ADAMS','SALESMAN',7698,'1981-09-08',1500,0,30),
    ->
    ->      (7900,'JAMES','CLERK',7788,'1981-12-03',950,NULL,30),
    ->      (7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20),
    ->      (7934,'MILLER','CLERK',7782,'1982-01-23',1300,NULL,10);
Query OK, 13 rows affected (0.004 sec)
Records: 13  Duplicates: 0  Warnings: 0

MariaDB [rakesh]> SELECT *FROM EMPLOYEE;
+------+--------+-----------+------+------------+------+------+--------+
| EMPO | ename  | job       | mgr  | hiredate   | sal  | comm | DEPTNO |
+------+--------+-----------+------+------------+------+------+--------+
| 7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800 | NULL |     20 |
| 7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
| 7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
| 7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL |     20 |
| 7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
| 7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL |     30 |
| 7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL |     20 |
| 7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL |     40 |
| 7839 | KING   | PRESEDENT | NULL | 1981-11-17 | 5000 | NULL |     20 |
| 7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
| 7876 | ADAMS  | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
| 7900 | JAMES  | CLERK     | 7788 | 1981-12-03 |  950 | NULL |     30 |
| 7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL |     20 |
| 7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL |     10 |
+------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.001 sec)

MariaDB [rakesh]> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| 2cse11             |
| collage            |
| college            |
| expremenr1         |
| iilm               |
| information_schema |
| mysql              |
| performance_schema |
| phpmyadmin         |
| rakesh             |
| test               |
+--------------------+
11 rows in set (0.010 sec)

MariaDB [rakesh]> SHOW TABLES;
+------------------+
| Tables_in_rakesh |
+------------------+
| department       |
| employee         |
+------------------+
2 rows in set (0.001 sec)

MariaDB [rakesh]> SELECT DEPTNO,ENAME ,SAL FROM EMPLOYEE WHERE DEPTNO=30 ORDER BY SAL DESE;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'DESE' atline 1
MariaDB [rakesh]> SELECT DEPTNO,ENAME ,SAL FROM EMPLOYEE WHERE DEPTNO=30 ORDER BY SAL desc;
+--------+--------+------+
| DEPTNO | ENAME  | SAL  |
+--------+--------+------+
|     30 | BLAKE  | 2850 |
|     30 | ALLEN  | 1600 |
|     30 | TURNER | 1500 |
|     30 | ADAMS  | 1500 |
|     30 | WARD   | 1250 |
|     30 | MARTIN | 1250 |
|     30 | JAMES  |  950 |
+--------+--------+------+
7 rows in set (0.001 sec)

MariaDB [rakesh]> select ename,deptno,jobfrom employee where ename like "A__N";
ERROR 1054 (42S22): Unknown column 'ename' in 'field list'
MariaDB [rakesh]> select ename,deptno,jobfrom employee where ENAME like "A__N";
ERROR 1054 (42S22): Unknown column 'ename' in 'field list'
MariaDB [rakesh]> SELECT ENAME,DEPTNO,JOB FROM EMPLOYEE WHERE ENAME LIKE "A__N";
Empty set (0.001 sec)

MariaDB [rakesh]> SELECT *FROM EMPLOYEE WHERE ENAME LIKE "S%";
+------+-------+---------+------+------------+------+------+--------+
| EMPO | ename | job     | mgr  | hiredate   | sal  | comm | DEPTNO |
+------+-------+---------+------+------------+------+------+--------+
| 7369 | SMITH | CLERK   | 7902 | 1980-12-17 |  800 | NULL |     20 |
| 7788 | SCOTT | ANALYST | 7566 | 1982-12-09 | 3000 | NULL |     40 |
+------+-------+---------+------+------------+------+------+--------+
2 rows in set (0.001 sec)

MariaDB [rakesh]> SELECT *FROM EMPLOYEE WHERE ENAME LIKE "%S";
+------+-------+----------+------+------------+------+------+--------+
| EMPO | ename | job      | mgr  | hiredate   | sal  | comm | DEPTNO |
+------+-------+----------+------+------------+------+------+--------+
| 7566 | JONES | MANAGER  | 7839 | 1981-04-02 | 2975 | NULL |     20 |
| 7876 | ADAMS | SALESMAN | 7698 | 1981-09-08 | 1500 |    0 |     30 |
| 7900 | JAMES | CLERK    | 7788 | 1981-12-03 |  950 | NULL |     30 |
+------+-------+----------+------+------------+------+------+--------+
3 rows in set (0.001 sec)

MariaDB [rakesh]> SELECT *FROM EMPLOYEE WHERE DEPTNO IN(10,20,30) OR JOB IN ("CLERK","ANALYST","SALESMAN");
+------+--------+-----------+------+------------+------+------+--------+
| EMPO | ename  | job       | mgr  | hiredate   | sal  | comm | DEPTNO |
+------+--------+-----------+------+------------+------+------+--------+
| 7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800 | NULL |     20 |
| 7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
| 7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
| 7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL |     20 |
| 7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
| 7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL |     30 |
| 7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL |     20 |
| 7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3000 | NULL |     40 |
| 7839 | KING   | PRESEDENT | NULL | 1981-11-17 | 5000 | NULL |     20 |
| 7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
| 7876 | ADAMS  | SALESMAN  | 7698 | 1981-09-08 | 1500 |    0 |     30 |
| 7900 | JAMES  | CLERK     | 7788 | 1981-12-03 |  950 | NULL |     30 |
| 7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000 | NULL |     20 |
| 7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300 | NULL |     10 |
+------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.001 sec)

MariaDB [rakesh]> SELECT EMPNO, ENAME FROM EMPLOYEE WHERE COMM IS NOT NULL AND COMM>0;
ERROR 1054 (42S22): Unknown column 'EMPNO' in 'field list'
MariaDB [rakesh]> SELECT DEPTNO, ENAME FROM EMPLOYEE WHERE COMM IS NOT NULL AND COMM>0;
+--------+--------+
| DEPTNO | ENAME  |
+--------+--------+
|     30 | ALLEN  |
|     30 | WARD   |
|     30 | MARTIN |
+--------+--------+
3 rows in set (0.001 sec)

MariaDB [rakesh]> SELECT DEPTNO,SAL+IFNULL(COMM,0) AS TOTAL_SALARY FROM EMPLOYEE;
+--------+--------------+
| DEPTNO | TOTAL_SALARY |
+--------+--------------+
|     20 |          800 |
|     30 |         1900 |
|     30 |         1550 |
|     20 |         2975 |
|     30 |         2650 |
|     30 |         2850 |
|     20 |         2450 |
|     40 |         3000 |
|     20 |         5000 |
|     30 |         1500 |
|     30 |         1500 |
|     30 |          950 |
|     20 |         3000 |
|     10 |         1300 |
+--------+--------------+
14 rows in set (0.001 sec)

MariaDB [rakesh]> SELECT DEPTNO,SAL*12 AS ANNUAL_SALARY FROM EMPLOYEE;
+--------+---------------+
| DEPTNO | ANNUAL_SALARY |
+--------+---------------+
|     20 |          9600 |
|     30 |         19200 |
|     30 |         15000 |
|     20 |         35700 |
|     30 |         15000 |
|     30 |         34200 |
|     20 |         29400 |
|     40 |         36000 |
|     20 |         60000 |
|     30 |         18000 |
|     30 |         18000 |
|     30 |         11400 |
|     20 |         36000 |
|     10 |         15600 |
+--------+---------------+
14 rows in set (0.001 sec)

MariaDB [rakesh]> SELECT ENAME FROM EMPLOYEE WHER JOB="CLERK" AND SAL>3000;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'JOB="CLERK" AND SAL>3000' at line 1
MariaDB [rakesh]> SELECT ENAME FROM EMPLOYEE WHER JOB="CLERK" and SAL > 3000;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'JOB="CLERK" and SAL > 3000' at line 1
MariaDB [rakesh]> SELECT ENAME FROM EMPLOYEE WHERE JOB="CLERK" and SAL > 3000;
Empty set (0.008 sec)

0;riaDB [rakesh]> SELECT ENAME FROM EMPLOYEE WHERE JOB IN ("CLERK","ANALYST"
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '0' at line 1
MariaDB [rakesh]> SELECT ENAME FROM EMPLOYEE WHERE JOB IN ("CLERK","ANALYST","SALESMAN") AND SAL>3000;
Empty set (0.001 sec)

MariaDB [rakesh]>
