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
--
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
-- SELECT o.ord_no,o.ord_date,o.purch_amt,c.cust_name AS "Customer Name",c.grade,s.name AS "Salesman",s.commission FROM orders o JOIN customer c
   ON o.customer_id = c.customer_id JOIN salesman s ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="1764" height="1154" alt="image" src="https://github.com/user-attachments/assets/9cd6a04b-b084-4c8d-93ff-e4634484eabb" />

**Question 2**
---
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

<img width="1324" height="517" alt="image" src="https://github.com/user-attachments/assets/c0c4ea32-ac3a-4633-8994-e1c7ffe9f37d" />


**Question 3**
---

<img width="1769" height="382" alt="image" src="https://github.com/user-attachments/assets/52caf28f-5648-48be-aab6-db0f46c02860" />


```sql
SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt FROM CUSTOMER c LEFT JOIN ORDERS o
ON c.customer_id = o.customer_id WHERE c.city='London';
```

**Output:**

<img width="1751" height="502" alt="image" src="https://github.com/user-attachments/assets/8e6ebdc7-7b64-4f1d-a1c3-aa5fa3d9bcf9" />


**Question 4**
---
<img width="1766" height="389" alt="image" src="https://github.com/user-attachments/assets/dde17e21-634d-4a4e-83e6-ef30d72c132c" />

```sql
SELECT p.first_name AS "patient_name" FROM PATIENTS p INNER JOIN DOCTORS d ON 
p.doctor_id = d.doctor_id WHERE d.first_name='Emily' AND d.last_name='Johnson' AND p.discharge_date IS NOT NULL;
```

**Output:**

<img width="852" height="440" alt="image" src="https://github.com/user-attachments/assets/bdd81ebc-eb9a-45c3-a344-30f04c35c766" />


**Question 5**
---
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
p.patient_id = s.patient_id WHERE s.surgery_date='2024-01-15';```
```

**Output:**

<img width="829" height="448" alt="image" src="https://github.com/user-attachments/assets/c5555d5d-675a-4e44-9d93-fe39f532057b" />

**Question 6**
---
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

<img width="1605" height="908" alt="image" src="https://github.com/user-attachments/assets/0e13e730-313b-4eed-a22a-1ff3e0934f5a" />


**Question 7**
---

<img width="1724" height="388" alt="image" src="https://github.com/user-attachments/assets/1daa403a-3b23-4b87-a2bf-de278f9a7731" />


```sql
SELECT c.* FROM CUSTOMER c LEFT JOIN ORDERS o ON 
c.customer_id = o.customer_id WHERE o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';
```

**Output:**

<img width="1500" height="495" alt="image" src="https://github.com/user-attachments/assets/028b311c-50a3-4223-adc8-c93d869eb2fa" />


**Question 8**
---

<img width="1765" height="398" alt="image" src="https://github.com/user-attachments/assets/603d578c-8b60-4b0f-bc2a-6653b46e1b47" />


```sql
SELECT n.*,d.department_name FROM NURSES n INNER JOIN DEPARTMENTS d ON
n.department_id = d.department_id ;
```

**Output:**

<img width="1561" height="568" alt="image" src="https://github.com/user-attachments/assets/9aa66797-d379-497f-9776-64257d861850" />

**Question 9**
---
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
SELECT * FROM orders NATURAL JOIN customer NATURAL JOIN salesman;```
```

**Output:**

<img width="1759" height="577" alt="image" src="https://github.com/user-attachments/assets/88e6c4f9-7ad4-4c06-875e-f004b83705b5" />


**Question 10**
---
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
specialization   VARCHAR(100)
```


```sql
SELECT p.*,d.first_name AS "doctor_name" FROM PATIENTS p INNER JOIN DOCTORS d on 
p.doctor_id = d.doctor_id ;
```

**Output:**

<img width="1754" height="576" alt="image" src="https://github.com/user-attachments/assets/8c433a8a-a4b9-4efa-b11b-2ccecd4feef9" />

## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
