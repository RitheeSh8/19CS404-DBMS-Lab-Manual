# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
```
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```

```sql
SELECT MAX(age) - MIN(age) AS age_difference FROM employee;
```

**Output:**

<img width="543" height="359" alt="image" src="https://github.com/user-attachments/assets/faafbfcf-911e-42f1-8abf-9e06a77f84af" />

**Question 2**
```
Write a SQL query to find the average length of names for people living in Chennai?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
```


```sql
SELECT AVG(LENGTH(name)) AS avg_name_length FROM customer WHERE city='Chennai';
```

**Output:**

<img width="434" height="366" alt="image" src="https://github.com/user-attachments/assets/b183f6ea-166e-48df-88c4-fe839544802d" />

**Question 3**
```
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
```


```sql
SELECT SUM(income) AS total_income FROM employee WHERE age>=40;
```


**Output:**

<img width="439" height="364" alt="image" src="https://github.com/user-attachments/assets/5b49f0aa-10ea-4421-ac63-3cd05b16cb9f" />


**Question 4**

<img width="939" height="230" alt="image" src="https://github.com/user-attachments/assets/98c8d019-9b3f-478f-aa9a-210c33ebf7f4" />

```sql
SELECT Specialty,COUNT(*) AS TotalDocto FROM Doctors GROUP BY Specialty;
```

**Output:**

<img width="753" height="667" alt="image" src="https://github.com/user-attachments/assets/4af20cc7-e55f-4526-be94-ef5d5af3c2e9" />

**Question 5**

<img width="1008" height="235" alt="image" src="https://github.com/user-attachments/assets/dd92a682-32b0-42b0-bd54-dea0a1d6589d" />


```sql
SELECT diagnosis,COUNT(*) AS DiagnosisCount FROM MedicalRecords GROUP BY Diagnosis 
ORDER BY DiagnosisCount DESC LIMIT 1;
```

**Output:**

<img width="879" height="349" alt="image" src="https://github.com/user-attachments/assets/931e4782-075b-4f18-98f4-458ebff6084f" />

**Question 6**
---
<img width="1038" height="245" alt="image" src="https://github.com/user-attachments/assets/77f96fb1-ea0b-4854-90ff-4ca303dd10a9" />

```sql
SELECT DoctorID,COUNT(*) AS TotalAppointments FROM Appointments GROUP BY DoctorID;
```

**Output:**

<img width="737" height="642" alt="image" src="https://github.com/user-attachments/assets/17000f4f-29c2-4c9c-a6b7-a4a96bf71e99" />

**Question 7**
---

<img width="1769" height="244" alt="image" src="https://github.com/user-attachments/assets/7f1135a8-f4fb-4dff-b4fb-e5d442232c9b" />

```sql
SELECT jdate,SUM(workhour) FROM employee1 GROUP BY jdate HAVING SUM(workhour) > 40;
```

**Output:**

<img width="657" height="423" alt="image" src="https://github.com/user-attachments/assets/c60990e4-e3d9-4557-84c6-68094734727d" />


**Question 8**
---

<img width="903" height="220" alt="image" src="https://github.com/user-attachments/assets/e8225285-cc94-48ba-b2d4-4f6306249326" />

```sql
SELECT address,AVG(salary) FROM customer1 GROUP BY address HAVING AVG(salary) < 15000;
```


**Output:**

<img width="578" height="613" alt="image" src="https://github.com/user-attachments/assets/e5fd9b93-2805-4315-bb87-2f94dc370995" />

**Question 9**
---

<img width="1821" height="243" alt="image" src="https://github.com/user-attachments/assets/c93eb174-18b2-48e1-9283-e1dfc1600762" />

```sql
SELECT age,SUM(income) FROM employee GROUP BY age HAVING SUM(income) > 1000000;
```


**Output:**

<img width="796" height="450" alt="image" src="https://github.com/user-attachments/assets/9b31f4b1-70a1-4426-968b-178f389ae4de" />

**Question 10**

<img width="1785" height="263" alt="image" src="https://github.com/user-attachments/assets/e4c126ce-ada9-4fb3-b7de-0b4de7946b4b" />


```sql
SELECT occupation,AVG(workhour) FROM employee1 GROUP BY occupation HAVING AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**

<img width="668" height="451" alt="image" src="https://github.com/user-attachments/assets/080c8630-b6e0-41c3-9f6a-73565344af06" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
