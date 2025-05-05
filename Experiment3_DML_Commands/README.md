# Experiment 3: DML Commands

### Name :OVIYA P
### Reg No: 212223110033

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
```
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.
products table
---------------
product_id
product_name
category_id
availability
```
```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;
```

**Output:**

![image](https://github.com/user-attachments/assets/59d4b39d-628b-43db-a47c-4a24742cb5b3)


**Question 2**
```
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'
Employees table
---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
For example:
Test	Result
SELECT EMPLOYEE_ID, FIRST_NAME, EMAIL, SALARY, JOB_ID FROM EMPLOYEES 
WHERE department_id = 20;
EMPLOYEE_ID  FIRST_NAME  EMAIL       SALARY      JOB_ID
-----------  ----------  ----------  ----------  ----------
201          Michael     MHARTSTE    26000       MK_MAN
202          Pat         PFAY        6000        MK_REP
```

```sql
UPDATE Employees
SET salary = salary*2
WHERE department_id = 20 and job_id LIKE '%MAN';
```

**Output:**

![image](https://github.com/user-attachments/assets/7b83c2bf-e31e-45a2-8b5f-3d962ac0a85e)


**Question 3**
```
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.
Products Table 
name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lv     INT        
quantity       INT        
supplier_id    INT           
For example:
Test	Result
select changes();
changes()
----------
4
```
```sql
UPDATE products
SET sell_price=sell_price * 1.15
WHERE quantity < 50 AND supplier_id = 10;
```

**Output:**

![image](https://github.com/user-attachments/assets/34d48009-85c1-4df1-a439-886860bb7bc8)


**Question 4**
```
Write a SQL query to Delete customers from 'customer' table where 'AGENT_CODE' is either 'A003' or 'A008'.
Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:
Test	Result
select distinct(agent_code)from customer;
AGENT_CODE
----------
A003
A008
A011
A006
A005
A010
A002
A004
A009
A007
A012
A001
AGENT_CODE
----------
A011
A006
A005
A010
A002
A004
A009
A007
A012
A001
```
```sql
DELETE FROM customer
WHERE AGENT_CODE IN('A003','A008');
```

**Output:**

![image](https://github.com/user-attachments/assets/177905dd-0966-4b56-bf7a-3d22d238d13a)


**Question 5**
```
Write a SQL query to Delete All Doctors with a NULL Specialization
Sample table: Doctors
attributes : doctor_id, first_name, last_name, specialization
For example:
Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
4           Febin       Jones
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
```

```sql
DELETE FROM Doctors
WHERE specialization IS NULL;
```

**Output:**

![image](https://github.com/user-attachments/assets/3518f23b-76be-4d0c-a2be-c46598ed5a37)


**Question 6**
```
Write a SQL query to Delete customers from 'customer' table where 'CUST_CITY' is not 'New York' and 'OUTSTANDING_AMT' is greater than 5000.
Sample table: Customer
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
For example:
Test	Result
select changes();
changes()
----------
16
```

```sql
DELETE from Customer
WHERE CUST_CITY <> 'New York' AND OUTSTANDING_AMT > 5000
```

**Output:**

![image](https://github.com/user-attachments/assets/82b7d754-353d-43fd-a961-83569a0ceec7)


**Question 7**
```
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.
Sample table: Doctors
attributes : doctor_id, first_name, last_name, specialization
```
```sql
delete from Doctors
where Specialization IS 'Pediatrics' AND first_name IS 'Michael'
```

**Output:**

![image](https://github.com/user-attachments/assets/7c06e471-6b02-4f89-af50-40e288646ff0)



**Question 8**
```
Write a query to find all the employees whose salary is between 50000 to 100000 from employeeposition table.
EmpID
EmpPosition
DateOfJoining
Salary
1
Manager
01/05/2024
500000
2
Executive
02/05/2024
75000
For example:
Result
EmpID       EmpPosition  DateOfJoining  Salary
----------  -----------  -------------  ----------
2           Executive    2024-05-02     75000
3           Manager      2024-05-01     90000
2           Lead         2024-05-02     85000
```
```sql
SELECT EmpID,EmpPosition,DateOfJoining,Salary 
FROM employeeposition
WHERE Salary BETWEEN 50000 and 100000;
```

**Output:**

![image](https://github.com/user-attachments/assets/222fd128-e8fc-40a8-babb-8930d3929425)


**Question 9**
```
Write a SQL statement to Find the salesmen with all information who gets the commission within a range of 0.12 and 0.14.
salesman table
cid         name         type        notnull     dflt_value  pk
----------  -----------  ----------  ----------  ----------  ----------
0           salesman_id  numeric(5)    0                       1
1           name         varchar(30)   0                       0
2           city         varchar(15)   0                       0
3           commission   decimal(5,2)  0                       0

For example:
Result
salesman_id  name        city        commission
-----------  ----------  ----------  ----------
5002         Nail Knite  Paris       0.13
5006         Mc Lyon     Paris       0.14
5007         Paul Adam   Rome        0.13
5003         Lauson Hen  San Jose    0.12
```

```sql
select * from salesman
where commission BETWEEN 0.12 and 0.14;
```

**Output:**

![image](https://github.com/user-attachments/assets/f93df386-b8a4-432c-b549-7af9934c6c6e)


**Question 10**
```
Write a SQL query to round the decimal column to 3 decimal places from the Calculations table.
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0
For example:
Result
id          rounded_value
----------  -------------
1           123.457
2           567.891
3           78.234
4           45.78
```

```sql
select id,ROUND("decimal", 3) AS
rounded_value
from Calculations
```

**Output:**

![image](https://github.com/user-attachments/assets/19b0a63d-8718-4229-916b-3c3d0aeec990)


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
