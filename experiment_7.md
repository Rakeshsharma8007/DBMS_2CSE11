<center><h2>Experiment 7</h2></center>
<h4>Queries:</h4>

### 1.Compute the no. of days remaining in this year.
~~~sql
SELECT DATEDIFF(LAST_DAY(STR_TO_DATE(CONCAT(YEAR(CURDATE()), '-12-01'), '%Y-%m-%d')), CURDATE()) AS DAYS_REMAINING;
~~~

### 2. Find the highest and lowest salaries and the difference between 
of them.
~~~sql
SELECT MAX(SAL) AS HIGHEST, MIN(SAL) AS LOWEST, (MAX(SAL) - MIN(SAL)) AS DIFFERENCE FROM EMPLOYEE;
~~~

### 3. List employee whose commission is greater than 25 % of their 
salaries.
~~~sql
SELECT * FROM EMPLOYEE WHERE COMM > (SAL * 0.25);
~~~

### 4. Make a query that displays salary in dollar format.
~~~sql
SELECT ENAME, CONCAT('$', FORMAT(SAL, 2)) AS SALARY_IN_DOLLARS FROM EMPLOYEE;
~~~

### 5. Create a matrix query to display the job, the salary for that job 
based on department number, and the total salary for that job 
for all departments, giving each column an appropriate 
heading.
~~~sql
SELECT JOB, SUM(IF(DEPTNO = 10, SAL, 0)) AS DEPT_10, SUM(IF(DEPTNO = 20, SAL, 0)) AS DEPT_20, SUM(IF(DEPTNO = 30, SAL, 0)) AS DEPT_30, SUM(SAL) AS TOTAL_SALARY FROM EMPLOYEE GROUP BY JOB;
~~~

### 6. Query that will display the total no of employees, and of that 
total the number who were hired in 1980,1981,1982 and 1983. 
Give appropriate column heading.
~~~sql
SELECT COUNT(*) AS TOTAL_EMP, SUM(IF(YEAR(HIREDATE)=1980, 1, 0)) AS "1980", SUM(IF(YEAR(HIREDATE)=1981, 1, 0)) AS "1981", SUM(IF(YEAR(HIREDATE)=1982, 1, 0)) AS "1982", SUM(IF(YEAR(HIREDATE)=1983, 1, 0)) AS "1983" FROM EMPLOYEE;
~~~~
### 7. Query to get the last Sunday of Any Month. 
~~~sql
SELECT DATE_SUB(LAST_DAY(CURDATE()), INTERVAL (WEEKDAY(LAST_DAY(CURDATE())) + 1) % 7 DAY) AS LAST_SUNDAY;
~~~
### 8. Display department numbers and total number of employees 
working in each department. 
~~~sql
SELECT DEPTNO, COUNT(*) AS TOTAL_EMPLOYEES FROM EMPLOYEE GROUP BY DEPTNO;
~~~
### 9. Display the various jobs and total number of employees within 
each job group. 
~~~sql
SELECT JOB, COUNT(*) AS TOTAL_EMPLOYEES FROM EMPLOYEE GROUP BY JOB;
~~~
### 10. Display the depart numbers and total salary for each department. 
~~~sql
SELECT DEPTNO, SUM(SAL) AS TOTAL_DEPARTMENT_SALARY FROM EMPLOYEE GROUP BY DEPTNO;
~~~
 
