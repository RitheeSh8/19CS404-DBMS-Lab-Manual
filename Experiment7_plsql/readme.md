# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Program
```
DECLARE 
    n1 NUMBER;
    n2 NUMBER;
BEGIN
    n1:= 10;
    n2:= 49;
    IF n1>n2 THEN
        DBMS_OUTPUT.PUT_LINE('Greatest = ' || n1);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greatest = ' || n2);
    END IF;
END;
```

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Greater number is: 80

**Output:**

<img width="888" height="312" alt="image" src="https://github.com/user-attachments/assets/4546b7af-7340-4872-9c6d-44861af90805" />


---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Program 
```
DECLARE
    n1 NUMBER;
    ad NUMBER:=0;
    k NUMBER:=1;
BEGIN
    n1:=&n1;
    WHILE k<=n1 LOOP
        ad:=ad+k;
        k:=k+1;
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Sum of first '|| n1 || ' natural numbers is: ' || ad);
END;
/
```

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 6 natural numbers is: 21

**Output**

<img width="951" height="345" alt="image" src="https://github.com/user-attachments/assets/665df9b4-2628-4edf-96a2-016b437aea5e" />


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Program
```
DECLARE
    n1 NUMBER:=&n;
    a NUMBER:=0;
    b NUMBER:=1;
    c NUMBER;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonnaci Series : ');
    FOR i IN 1..n1 LOOP
        DBMS_OUTPUT.PUT(a || ' ');
        c:=a+b;
        a:=b;
        b:=c;
    END LOOP;
    DBMS_OUTPUT.NEW_LINE;
END;
/
```

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

**Output**

<img width="883" height="322" alt="image" src="https://github.com/user-attachments/assets/31845304-74e5-431e-8ec5-ed79e361d3f7" />


---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Program 
```
DECLARE
    n1 NUMBER;
    rev NUMBER:=0;
    digit NUMBER;
BEGIN
    n1:=&n1;

    WHILE n1>0 LOOP
        digit:=MOD(n1,10);
        rev:=rev*10+digit;
        n1:=TRUNC(n1/10);
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Reverse Number: ' || rev);
END;
/
```

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

**OUtput**

<img width="936" height="337" alt="image" src="https://github.com/user-attachments/assets/e4675808-8c41-4cca-bb08-b1a133e0a7a7" />


---

## 5. Write a PL/SQL program to find the largest of three numbers

### Program
```

```
### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
