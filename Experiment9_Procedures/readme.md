# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

**Expected Output:**  
Square of 6 is 36

## Program
```sql
CREATE OR REPLACE PROCEDURE find_square(num IN NUMBER) IS
  square_val NUMBER;
BEGIN
  square_val := num * num;
  DBMS_OUTPUT.PUT_LINE('Square of ' || num || ' is ' || square_val);
END;
/
BEGIN
  find_square(6);
END;
/

```
## Output

<img width="734" height="110" alt="image" src="https://github.com/user-attachments/assets/8b5e99a5-ab9f-4849-985e-33cd7ac00b73" />


## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

**Expected Output:**  
Factorial of 5 is 120

## Program
```sql
CREATE OR REPLACE FUNCTION get_factorial(n IN NUMBER)
RETURN NUMBER
IS
  fact NUMBER := 1;
BEGIN
  FOR i IN 1..n LOOP
    fact := fact * i;
  END LOOP;
  RETURN fact;
END;
/
BEGIN
  DBMS_OUTPUT.PUT_LINE('Factorial of 5 is ' || get_factorial(5));
END;
/

```
## Output

<img width="543" height="136" alt="image" src="https://github.com/user-attachments/assets/7aa8719e-0556-421d-ae68-9f6354828e0d" />

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
12 is Even

## Program
```sql
CREATE OR REPLACE PROCEDURE check_even_odd(num IN NUMBER)
IS
BEGIN
  IF MOD(num, 2) = 0 THEN
    DBMS_OUTPUT.PUT_LINE(num || ' is Even');
  ELSE
    DBMS_OUTPUT.PUT_LINE(num || ' is Odd');
  END IF;
END;
/

BEGIN
  check_even_odd(12);
END;
/

```
## Output

<img width="436" height="140" alt="image" src="https://github.com/user-attachments/assets/b86038f6-7494-43d8-be00-bf83ed8e9fcb" />

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

**Expected Output:**  
Reversed number of 1234 is 4321

## Program
```sql
CREATE OR REPLACE FUNCTION reverse_number(num IN NUMBER)
RETURN NUMBER
IS
  rev NUMBER := 0;
  n NUMBER := num;
BEGIN
  WHILE n > 0 LOOP
    rev := (rev * 10) + MOD(n, 10);
    n := TRUNC(n / 10);
  END LOOP;
  RETURN rev;
END;
/
BEGIN
  DBMS_OUTPUT.PUT_LINE('Reversed number of 1234 is ' || reverse_number(1234));
END;
/

```
## Output

<img width="396" height="104" alt="image" src="https://github.com/user-attachments/assets/0acb7a80-3f91-404d-8a68-59672321de71" />

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

## Program
```sql
CREATE OR REPLACE PROCEDURE print_table(num IN NUMBER)
IS
BEGIN
  DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || num || ':');
  FOR i IN 1..10 LOOP
    DBMS_OUTPUT.PUT_LINE(num || ' x ' || i || ' = ' || (num * i));
  END LOOP;
END;
/
BEGIN
  print_table(5);
END;
/

```
## Output

<img width="403" height="341" alt="image" src="https://github.com/user-attachments/assets/f2146beb-bb03-4de5-b250-11de6fb17419" />

## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
