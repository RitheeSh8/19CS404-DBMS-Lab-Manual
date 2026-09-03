# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
```
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```

```sql
SELECT o.ord_no,o.ord_date,o.purch_amt,c.cust_name AS "Customer Name",c.grade,s.name AS "Salesman",s.commission FROM orders o JOIN customer c
ON o.customer_id = c.customer_id JOIN salesman s ON o.salesman_id = s.salesman_id;```
```

**Output:**

<img width="1729" height="1183" alt="image" src="https://github.com/user-attachments/assets/1db02e79-915f-41b5-9f50-0ec93e1d07a7" />

**Question 2**
```
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
```

```sql

SELECT o.ord_no,o.purch_amt,c.cust_name,c.city FROM orders o JOIN customer c 
ON o.customer_id = c.customer_id WHERE o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**

<img width="1360" height="507" alt="image" src="https://github.com/user-attachments/assets/9e91a6f8-53b4-42c6-ac38-015697e7a6ab" />

**Question 3**
---
<img width="1713" height="386" alt="image" src="https://github.com/user-attachments/assets/527236e8-8ff5-448e-a6d5-b4f877e4c202" />


```sql
SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt FROM CUSTOMER c LEFT JOIN ORDERS o
ON c.customer_id = o.customer_id WHERE c.city='London';
```

**Output:**

<img width="1496" height="507" alt="image" src="https://github.com/user-attachments/assets/85f90157-ff03-4fff-a601-67232465de66" />

**Question 4**
---

<img width="1761" height="402" alt="image" src="https://github.com/user-attachments/assets/7cdf36de-fcec-4cc5-a9c2-648610b85ad8" />


```sql
SELECT p.first_name AS "patient_name" FROM PATIENTS p INNER JOIN DOCTORS d ON 
p.doctor_id = d.doctor_id WHERE d.first_name='Emily' AND d.last_name='Johnson' AND p.discharge_date IS NOT NULL;
```

**Output:**

<img width="484" height="442" alt="image" src="https://github.com/user-attachments/assets/13898927-ce1e-409d-acb9-5beb183c2bd3" />


**Question 5**
```
Write the SQL query that achieves the selection of the first name from the "patients" table, with an inner join on the "patient_id" column and a condition filtering for surgeries with a surgery date of '2024-01-15'.:

PATIENTS TABLE:

name             type
---------------  ---------------
patient_id       INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
date_of_birth    DATE
admission_date   DATE
discharge_date   DATE
doctor_id        INT

SURGERIES TABLE:

name             type
---------------  ---------------
surgery_id       INT
patient_id       INT
surgeon_id       INT
surgery_date     DATE
```

```sql
SELECT p.first_name FROM PATIENTS p INNER JOIN SURGERIES s ON
p.patient_id = s.patient_id WHERE s.surgery_date='2024-01-15';
```

**Output:**

<img width="507" height="447" alt="image" src="https://github.com/user-attachments/assets/4641d87d-dca4-41b8-ba1b-5060c0e88677" />

**Question 6**
```
From the following tables write a SQL query to display the customer name, customer city, grade, salesman, salesman city. The results should be sorted by ascending customer_id.  

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```
```sql
SELECT c.cust_name,c.city,c.grade,s.name AS "Salesman",s.city FROM customer c JOIN salesman s
ON c.salesman_id=s.salesman_id ORDER BY c.customer_id ASC;
```

**Output:**

<img width="1460" height="923" alt="image" src="https://github.com/user-attachments/assets/276a2904-6628-445f-83a1-cf6044b340cf" />

**Question 7**

<img width="1746" height="388" alt="image" src="https://github.com/user-attachments/assets/2fe452a4-3dff-4993-9375-970580c8239f" />

```sql
SELECT c.* FROM CUSTOMER c LEFT JOIN ORDERS o ON 
c.customer_id = o.customer_id WHERE o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';
```

**Output:**

<img width="1499" height="524" alt="image" src="https://github.com/user-attachments/assets/4928125a-8ae6-44bc-8e34-b1cf706b4e06" />


**Question 8**
---

<img width="1697" height="404" alt="image" src="https://github.com/user-attachments/assets/50563de8-1d3e-4dc1-8eb0-eab9582f6c34" />

```sql
SELECT n.*,d.department_name FROM NURSES n INNER JOIN DEPARTMENTS d ON
n.department_id = d.department_id ;
```

**Output:**

<img width="1604" height="603" alt="image" src="https://github.com/user-attachments/assets/721bbd43-2e28-43a1-b242-2e67c700a949" />

**Question 9**
```
Write a SQL statement to join the tables salesman, customer and orders so that the same column of each table appears once and only the relational rows are returned. 

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id
----------  ----------  ----------  -----------  -----------
70001       150.5       2012-10-05  3005         5002
70009       270.65      2012-09-10  3001         5005
70002       65.26       2012-10-05  3002         5001
70004       110.5       2012-08-17  3009         5003
70007       948.5       2012-09-10  3005         5002
70005       2400.6      2012-07-27  3007         5001
70008       5760        2012-09-10  3002         5001
70010       1983.43     2012-10-10  3004         5006
70003       2480.4      2012-10-10  3009         5003
70012       250.45      2012-06-27  3008         5002
70011       75.29       2012-08-17  3003         5007
70013       3045.6      2012-04-25  3002         5001
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
        3008 | Julian Green   | London     |   300 |        5002
        3004 | Fabian Johnson | Paris      |   300 |        5006
        3009 | Geoff Cameron  | Berlin     |   100 |        5003
        3003 | Jozy Altidor   | Moscow     |   200 |        5007
        3001 | Brad Guzan     | London     |       |        5005
Sample table : salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11
        5006 | Mc Lyon    | Paris    |       0.14
        5007 | Paul Adam  | Rome     |       0.13
        5003 | Lauson Hen | San Jose |       0.12
```


```sql
SELECT * FROM orders NATURAL JOIN customer NATURAL JOIN salesman;
```

**Output:**

<img width="1733" height="580" alt="image" src="https://github.com/user-attachments/assets/4f9186ed-b901-4583-9373-71472166fdd0" />

**Question 10**
```
Write the SQL query that accomplishes the selection of all columns from the "patients" table and the first name of doctors from the "doctors" table, with an inner join on the "doctor_id" column.

PATIENTS TABLE:
name             type
---------------  ---------------
patient_id       INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
date_of_birth    DATE
admission_date   DATE
discharge_date   DATE
doctor_id        INT

DOCTORS TABLE:

name             type
---------------  ---------------
doctor_id        INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
specialization   VARCHAR(100
```

```sql
SELECT p.*,d.first_name AS "doctor_name" FROM PATIENTS p INNER JOIN DOCTORS d on 
p.doctor_id = d.doctor_id ;
```

**Output:**

<img width="1813" height="583" alt="image" src="https://github.com/user-attachments/assets/1d16de68-cc95-4d27-b092-41d2668ed753" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
