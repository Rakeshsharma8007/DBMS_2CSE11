<center><h2>EXERCISE 6</h2></center>
<h4>Queries:</h4>

### 1.Display empno, ename, deptno from employee table. Instead 
of display department numbers display the related department 
name (Use decode function). 
~~~sql
SELECT EMPNO, ENAME, DEPTNO, DECODE(DEPTNO, 10, 'ACCOUNTING', 20, 'RESEARCH', 30, 'SALES', 'OPERATIONS') AS DNAME FROM EMPLOYEE;
~~~
### 2.. Display your age in days. 
~~~sql
SELECT DATEDIFF(CURDATE(), '1997-08-15') AS AGE_IN_DAYS;
~~~
###3. Display your age in months. 
~~~sql
SELECT PERIOD_DIFF(EXTRACT(YEAR_MONTH FROM CURDATE()), EXTRACT(YEAR_MONTH FROM '1997-08-15')) AS AGE_IN_MONTHS;
~~~

###4. Display the current date as 15th August Friday Nineteen 
Ninety-Seven. 
~~~sql
SELECT DATE_FORMAT(CURDATE(), '%D %M %W %Y') AS FORMATTED_DATE;
~~~
###5. Display the following output for each row from employee 
table. 
~~~sql
SELECT CONCAT(ENAME, ' HAS JOINED THE COMPANY ON ', DATE_FORMAT(HIREDATE, '%W %D %M %Y')) FROM EMPLOYEE WHERE ENAME = 'SCOTT';
~~~
###6. Scott has joined the company on Wednesday 13th August 
Nineteen Ninety 
~~~sql
SELECT CONCAT(ENAME, ' HAS JOINED THE COMPANY ON ', DATE_FORMAT(HIREDATE, '%W %D %M %Y')) FROM EMPLOYEE WHERE ENAME = 'SCOTT';
~~~
###7. Find the date for nearest Saturday after current date.
~~~sql
SELECT DATE_ADD(CURDATE(), INTERVAL (12 - DAYOFWEEK(CURDATE())) % 7 DAY) AS NEXT_SATURDAY;
~~~
###8. Display current time. 
~~~sql
SELECT CURTIME();
~~~
###9. Display the date three months Before the current date .
~~~sql
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH);
~~~

###10. Display those employees who joined in the company in the 
month of Dec. 
~~~sql
SELECT * FROM EMPLOYEE WHERE MONTH(HIREDATE) = 12;
~~~
###11. Display those employees whose first 2 characters from hire 
date -last 2 characters of salary. 
~~~sql
SELECT * FROM EMPLOYEE WHERE LEFT(HIREDATE, 2) = RIGHT(SAL, 2);
~~~
###12. Display those employees whose 10% of salary is equal to the 
year of joining. 
~~~sql
SELECT * FROM EMPLOYEE WHERE (SAL * 0.10) = YEAR(HIREDATE);
~~~
###13. Display those employees who joined the company before 15 of 
the months. 
~~~sql
SELECT * FROM EMPLOYEE WHERE DAY(HIREDATE) < 15;
~~~
###14. Display those employees who has joined before 15th of the 
month 
~~~sql
SELECT * FROM EMPLOYEE WHERE DAY(HIREDATE) < 15;
~~~
###15. Display those employees whose joining DATE is available in deptno 
~~~sql
SELECT * FROM EMPLOYEE WHERE DAY(HIREDATE) = DEPTNO;
~~~
