# Experiment 2: DDL Commands

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
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL


```sql
CREATE TABLE ProjectAssignments(
AssignmentID INTEGER PRIMARY KEY,
EmployeeID integer,
ProjectID integer,
AssignmentDate Date NOT NULL,
foreign key (EmployeeID) references Employees(EmployeeID),
foreign key(ProjectID) references Projects(ProjectID)
);
```

**Output:**
![image](https://github.com/user-attachments/assets/250a93d9-a753-4799-b4a3-fc44cea27114)

**Question 2**
---
Write a SQL query to Add a new column State as text in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0

```sql
ALTER TABLE Student_details
ADD column State TEXT;
```

**Output:**
![image](https://github.com/user-attachments/assets/14dcfcf1-40bc-401b-8649-936a4fce8e27)

**Question 3**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.
```sql
create table jobs(
job_id integer,
job_title varchar(70) default '',
min_salary integer default(8000),
max_salary integer default null
);
```

**Output:**
![image](https://github.com/user-attachments/assets/93a950ce-4c39-46f2-979e-aad2c6503e89)

**Question 4**
---
Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'


```sql
Alter table books
Add column ISBN varchar(30) ;
Alter table books
Add column domain_dept varchar(30);

```

**Output:**
![image](https://github.com/user-attachments/assets/143a9a13-3b8d-4af0-bcc6-9308a143819e)

**Question 5**
---
Insert the following customers into the Customers table:

CustomerID  Name         Address     City        ZipCode
----------  -----------  ----------  ----------  ----------
302         Laura Croft  456 Elm St  Seattle     98101
303         Bruce Wayne  789 Oak St  Gotham      10001
```sql
Insert  into Customers(CustomerID,Name,Address,City,Zipcode)
values(302,'Laura Croft','456 Elm St','Seattle',98101),
(303,'Bruce Wayne','789 Oak St','Gotham',10001);
```

**Output:**
![image](https://github.com/user-attachments/assets/1af68e0c-c25c-4e1a-aa55-a34a3650e4b7)

**Question 6**
---
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.
```sql
CREATE TABLE Products (
ProductID INTEGER PRIMARY KEY,
ProductName varchar(30) NOT NULL,
Price REAL CHECK(Price>0),
Stock INTEGER CHECK(Stock>=0)
);
```

**Output:**
![image](https://github.com/user-attachments/assets/4a58a970-a937-4657-9342-b20fd8c51676)

**Question 7**
---
Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE
```sql
CREATE TABLE Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE
);
```

**Output:**
![image](https://github.com/user-attachments/assets/f56ab494-b2c5-4243-815c-6fe9fa5548c0)

**Question 8**
---
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock
```sql
INSERT INTO Products(ProductID,ProductName,Price,Stock)
SELECT ProductID,ProductName,Price,Stock FROM Discontinued_products;
```

**Output:**
![image](https://github.com/user-attachments/assets/cebcc727-1298-49c3-8ab9-e6c74dc5d74d)


**Question 9**
---
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.
```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
values("978-1234567890","Data Science Essentials","Jane Doe","TechBooks",2024);
```

**Output:**
![image](https://github.com/user-attachments/assets/d243dff6-8ae6-4a2c-a240-f1c98df39551)

**Question 10**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT NOT NULL,
rate INTEGER NOT NULL,
icom_id TEXT check(length(4)),
foreign key(icom_id) references company(com_id)
on update set null
on delete set null

);
```

**Output:**
![image](https://github.com/user-attachments/assets/9b61a162-6731-47fa-93f2-4a0565d09833)

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
