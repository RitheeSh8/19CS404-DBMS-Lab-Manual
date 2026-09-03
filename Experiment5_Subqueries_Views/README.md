# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
```
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 2.5 Lakh

Employee Table

name             type

------------   ---------------

id                    INTEGER

name              TEXT

age                 INTEGER

city                 TEXT

income           INTEGER
```

```sql
SELECT * FROM Employee WHERE age < (SELECT AVG(age) FROM Employee WHERE income > 250000 );
```

**Output:**

<img width="1323" height="535" alt="image" src="https://github.com/user-attachments/assets/fee98f8e-fee7-4f03-9bae-fd71ff076b33" />

**Question 2**
```
Write a SQL query to Find employees who have an age less than the average age of employees with incomes over 1 million

Employee Table

name             type

------------   ---------------

id                    INTEGER

name              TEXT

age                 INTEGER

city                 TEXT

income           INTEGER
```

```sql
SELECT * FROM Employee WHERE age < (SELECT AVG(age) FROM Employee WHERE income > 1000000 );
```

**Output:**

<img width="1297" height="452" alt="image" src="https://github.com/user-attachments/assets/71319b05-fd55-4823-a753-10974b27757c" />

**Question 3**
---
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is LESS than $2500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000


```

```sql
SELECT * FROM CUSTOMERS WHERE ID IN (SELECT ID FROM CUSTOMERS WHERE salary < 2500 );
```

**Output:**

<img width="1113" height="477" alt="image" src="https://github.com/user-attachments/assets/f7609a41-7f14-4383-a93b-91a6fab4f51c" />

**Question 4**
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose Address as Delhi and age below 30

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000
```

```sql
SELECT * FROM CUSTOMERS WHERE AGE<30 AND ID IN 
(SELECT ID FROM CUSTOMERS WHERE ADDRESS='Delhi');
```

**Output:**

<img width="1116" height="399" alt="image" src="https://github.com/user-attachments/assets/1231b23f-b15d-4ed0-9c51-546fb560fcbf" />

**Question 5**
---
<img width="1490" height="348" alt="image" src="https://github.com/user-attachments/assets/94915f67-e963-4edf-9f40-ab71002e0f15" />


```sql
SELECT * FROM GRADES g WHERE grade = (SELECT MAX(grade) FROM GRADES WHERE subject=g.subject);
```

**Output:**

<img width="1445" height="489" alt="image" src="https://github.com/user-attachments/assets/e2f57550-4804-49cc-a7c8-2caf3a1951a7" />

**Question 6**
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose salary is EQUAL TO $1500.

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000
```

```sql
SELECT * FROM CUSTOMERS WHERE ID IN ( SELECT ID FROM CUSTOMERS WHERE SALARY=1500 );
```

**Output:**

<img width="1102" height="394" alt="image" src="https://github.com/user-attachments/assets/b052d6fb-0a03-41d4-ad83-0dc3d25f16f7" />

**Question 7**
---
<img width="1333" height="381" alt="image" src="https://github.com/user-attachments/assets/a3a30204-f7a5-4e78-bb9e-2b4cd1135f42" />


```sql
SELECT o.ord_no,o.purch_amt,o.ord_date,o.customer_id,o.salesman_id FROM Orders o
JOIN Salesman s ON o.salesman_id = s.salesman_id WHERE s.name='Paul Adam';
```

**Output:**

<img width="1184" height="445" alt="image" src="https://github.com/user-attachments/assets/9f7d1b61-3f34-4c86-8058-4fe706cc9ebc" />


**Question 8**
```
Write a SQL query to Retrieve the names and cities of customers who have the same city as customers with IDs 3 and 7

SAMPLE TABLE: customer

name             type
---------------  ---------------
id               INTEGER
name             TEXT
city             TEXT
email            TEXT
phone            INTEGER
```
```sql
SELECT name,city FROM customer WHERE city IN (SELECT city FROM customer WHERE id IN (3,7) );
```

**Output:**

<img width="683" height="509" alt="image" src="https://github.com/user-attachments/assets/3d5bcfed-08e2-4a6d-823e-eae64100a963" />


**Question 9**
```
Write a SQL query to retrieve all columns from the CUSTOMERS table for customers whose AGE is LESS than $30

Sample table: CUSTOMERS

ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------

1          Ramesh     32              Ahmedabad     2000
2          Khilan        25              Delhi                 1500
3          Kaushik      23              Kota                  2000
4          Chaitali       25             Mumbai            6500
5          Hardik        27              Bhopal              8500
6          Komal         22              Hyderabad       4500

7           Muffy          24              Indore            10000

```

```sql
SELECT * FROM CUSTOMERS WHERE ID IN (SELECT ID FROM CUSTOMERS WHERE AGE < 30);```
```

**Output:**

<img width="1331" height="595" alt="image" src="https://github.com/user-attachments/assets/6451b0a3-0bd4-4374-b258-ecf0b647a61a" />


**Question 10**
```
From the following tables write a SQL query to find the order values greater than the average order value of 10th October 2012. Return ord_no, purch_amt, ord_date, customer_id, salesman_id.

Note: date should be yyyy-mm-dd format

ORDERS TABLE

name            type
----------     ----------
ord_no          int
purch_amt    real
ord_date       text
customer_id  int
salesman_id  int
```

```sql
SELECT * FROM ORDERS WHERE purch_amt > (SELECT AVG(purch_amt) FROM ORDERS WHERE ord_date='2012-10-10');
```

**Output:**

<img width="1145" height="496" alt="image" src="https://github.com/user-attachments/assets/ff237022-8624-4bf3-bac9-463a12464db3" />


## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
