# Experiment 2: DDL Commands
### Name :OVIYA P
### Reg No: 212223110033

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**

```
Create a new table named orders with the following specifications:
ord_id as TEXT with a length of 4.
item_id as TEXT.
ord_date as DATE.
ord_qty as INTEGER.
cost as INTEGER.
The primary key is a composite key consisting of item_id and ord_date.
ord_id and item_id should not accept NULL
For example:

Test	Result
INSERT INTO orders (ord_id, item_id, ord_date, ord_qty, cost) VALUES ('O001', 'I001', '2023-08-01', 10, 100);
SELECT * FROM orders;
ord_id      item_id     ord_date    ord_qty     cost
----------  ----------  ----------  ----------  ----------
O001        I001        2023-08-01  10          100
```

```sql
CREATE TABLE orders(
     ord_id  TEXT NOT NULL CHECK(LENGTH(ord_id)=4),
     item_id  TEXT NOT NULL,
     ord_date DATE,
     ord_qty  INTEGER,
     cost  INTEGER,
     primary key(item_id,ord_date)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/1777b47c-d9e8-474d-b424-8cfac59b9dfa)


**Question 2**
```
Write a SQL query to Rename the "city" column to "location" in the "customer" table.
Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
 
For example:
Test	Result
pragma table_info('customer');
cid         name         type                               notnull     dflt_value  pk
----------  -----------  ---------------------------------  ----------  ----------  ----------
0           customer_id  integer primarykey auto increment  0                       0
1           cust_name    varchar2(30)                       0                       0
2           location     varchar(30)                        0                       0
3           grade        number                             0                       0
4           salesman_id  number                             0                       0
```

```sql

ALTER TABLE customer RENAME COLUMN city TO location;
```

**Output:**
![image](https://github.com/user-attachments/assets/1c9d87b6-b6ae-4c5b-b1b1-6b17982f3bff)


**Question 3**
```
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
For example:
Test	Result
INSERT INTO Shipments (ShipmentID, ShipmentDate, SupplierID, OrderID) VALUES (2, '2024-08-03', 99, 1);
Error: FOREIGN KEY constraint failed
```

```sql
CREATE TABLE Shipments(
   ShipmentID INTEGER  primary key,
   ShipmentDate  DATE,
   SupplierID INTEGER,
   OrderID INTEGER,
   foreign key(SupplierID) REFERENCES Suppliers(SupplierID),
   foreign key(OrderID) REFERENCES Orders(OrderID)

);
```

**Output:**

![image](https://github.com/user-attachments/assets/5332ee23-6a27-4932-a683-69d6e807ebaa)


**Question 4**
```
Create a table named Events with the following columns:
EventID as INTEGER
EventName as TEXT
EventDate as DATE
For example:
Test	Result
pragma table_info('Events');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           EventID     INTEGER     0                       0
1           EventName   TEXT        0                       0
2           EventDate   DATE        0                       0
```

```sql
CREATE TABLE Events(
   EventID  INTEGER,
   EventName  TEXT,
   EventDate DATE
);

```

**Output:**

![image](https://github.com/user-attachments/assets/c5a154fe-9cec-467d-9300-3be0dfc0196a)


**Question 5**

```
Insert all customers from Old_customers into Customers
Table attributes are CustomerID, Name, Address, Email
For example:
Test	Result
select * from Customers;
CustomerID  Name             Address         Email
----------  ---------------  --------------  ---------------------
301         Michael Johnson  123 Elm Street  michael.j@example.com
302         Sarah Lee        456 Oak Avenue  sarah.lee@example.com
303         David Wilson     789 Pine Road   david.w@example.com
```

```sql
INSERT INTO Customers(CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email FROM Old_customers;

```

**Output:**

![image](https://github.com/user-attachments/assets/83f1d7b0-f7ac-4b69-8055-c8e77c9272a6)


**Question 6**

```
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.
For example:
Test	Result
SELECT * FROM Books;
ISBN            Title                    Author      Publisher   Year
--------------  -----------------------  ----------  ----------  ----------
978-1234567890  Data Science Essentials  Jane Doe    TechBooks   2024

```
```sql
INSERT INTO Books(ISBN, Title, Author, Publisher, Year )
VALUES('978-1234567890','Data Science Essentials', 'Jane Doe', 'TechBooks','2024');

```

**Output:**

![image](https://github.com/user-attachments/assets/349eb0f2-a883-4c5c-95ba-0ed3f8dfc335)


**Question 7**

```
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.
For example:

Test	Result
-- Attempt to insert a record with NULL FirstName
INSERT INTO Employees (EmployeeID, FirstName, LastName, Email, Salary, DepartmentID)
VALUES (1, NULL, 'Doe', 'john.doe@example.com', 50000, 1);
Error: NOT NULL constraint failed: Employees.FirstName
```

```sql
CREATE TABLE Employees(
    EmployeeID INT primary key,
    FirstName VARCHAR(255) NOT NULL,
    LastName VARCHAR(255) NOT NULL,
    Email VARCHAR(255) UNIQUE,
    Salary CHECK(Salary>0),
    DepartmentID INTEGER,
    foreign key(DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/794588ba-5546-47c6-913b-e3243ff10e16)


**Question 8**
```
Create a table named Invoices with the following constraints:

InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
DueDate as DATE should be greater than the InvoiceDate.
Amount as REAL should be greater than 0.
For example:

Test	Result
INSERT INTO Invoices (InvoiceID, InvoiceDate)
VALUES (1, '2024-08-08'),(1,'2024-09-08');
Error: UNIQUE constraint failed: Invoices.InvoiceID
```

```sql
CREATE TABLE Invoices(
   InvoiceID  INTEGER  primary key,
   InvoiceDate  DATE,
   DueDate  DATE CHECK(DueDate>InvoiceDate),
   Amount REAL CHECK(Amount>0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/389a134f-8588-4044-8cca-9efb90513ee9)


**Question 9**
```
Insert the following employees into the Employee table:

EmployeeID  Name        Position    Department  Salary
----------  ----------  ----------  ----------  ----------
2           John Smith  Developer   IT          75000
3           Anna Bell   Designer    Marketing   68000
For example:

Test	Result
SELECT * FROM Employee;

EmployeeID  Name        Position    Department  Salary
----------  ----------  ----------  ----------  ----------
2           John Smith  Developer   IT          75000
3           Anna Bell   Designer    Marketing   68000
```

```sql

INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES('2','John Smith','Developer','IT','75000'),
('3','Anna Bell','Designer','Marketing','68000')

```

**Output:**

![image](https://github.com/user-attachments/assets/5a45ee79-f999-46d6-a8fb-371bfaae85ad)


**Question 10**
```
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
designation as VARCHAR(50)
net_salary as NUMBER
dob as DATE
 

 

For example:

Test	Result
pragma table_info('Companies');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          int         0                       0
1           name        varchar(50  0                       0
2           address     text        0                       0
3           email       varchar(50  0                       0
4           phone       varchar(10  0                       0
5           designatio  varchar(50  0                       0
6           net_salary  number      0                       0
7           dob         date        0                       0

```

```sql

ALTER TABLE Companies
ADD designation varchar(50);
ALTER TABLE Companies
ADD net_salary number;
ALTER TABLE Companies
ADD dob date;

```

**Output:**

![image](https://github.com/user-attachments/assets/fb61dc53-bf7b-43bc-98e0-161fff380968)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
