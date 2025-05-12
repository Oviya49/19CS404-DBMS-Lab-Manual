# Experiment 3: DML Commands

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
Question 1 :
---
Write a SQL statement to Update the reorder level to 20 where the quantity in stock is less than 10 and product category is 'Snacks' in the products table.
```
Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id
```
## SQL Code:
```
update products
set reorder_lvl=20
where (quantity <10) and 
category='Snacks';
```
## Output:
![image](https://github.com/user-attachments/assets/2c9efd39-28e0-4895-9b46-2ee070eb5f18)
Question 2 :
---
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.
```
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
```
## SQL Code:
```
update Employees
set email='Unavailable';
```
## Output:
![image](https://github.com/user-attachments/assets/f070de33-4d7f-485d-a9c4-32ac22036e15)

Question 3 :
---
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
```
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT
```
## SQL Code:
```
update products
set reorder_lvl=cast(reorder_lvl *1.3 as integer)
where category='Food' and quantity<(reorder_lvl*0.5);
```
## Output:
![image](https://github.com/user-attachments/assets/359f0c1a-5da0-4556-8258-75adad8c5028)

Question 4 :
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)
## SQL Code:
```
update suppliers
set supplier_name='A1 Suppliers'
where supplier_id =8 ;
```
## Output:
![image](https://github.com/user-attachments/assets/5d96d59e-8348-4a2d-bfe4-25f39247867e)

Question 5 :
---
Write a SQL statement to change salary of employee to 8000 whose Employee ID is 105, if the existing salary is less than 5000.
```
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
```
## SQL Code:
```
update Employees
set salary='8000'
where employee_id=105
and (salary<5000);
```
## Output:
![image](https://github.com/user-attachments/assets/821ab608-f45f-4f46-b8f0-c5b9ef5530a2)

Question 6 :
---
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
## SQL Code:
```
delete from Doctors
where specialization ='Pediatrics'
and first_name ='Michael';
```
## Output:
![image](https://github.com/user-attachments/assets/ca1009e1-c291-49f6-a06d-61f56a661de6)

Question 7 :
---
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3
Sample table: Customer
```
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB
``` 
## SQL Code:
```
delete from Customer
where CUST_COUNTRY not in ('UK','USA','Canada')
and (GRADE>=3);
```
## Output:
![image](https://github.com/user-attachments/assets/8a2b12b4-73db-4648-975a-6ed65e5c4e37)

Question 8 :
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date
## SQL Code:
```
delete from Surgeries
where surgery_id ='3';
```
## Output:
![image](https://github.com/user-attachments/assets/d0e70bac-01a7-457b-9595-cd0956502944)

Question 9 :
---
Write a query to list all products where the discount amount exceeds $50. The discount amount is calculated as original_price * discount_percentage. Return product_id, original_price, discount_percentage, and discount_amount.

Sample table: Products
```
product_id | original_price | discount_percentage

-----------------------------------------------------------

"101" "50" "0.1"

"102" "150" "0.15"

"103" "200" "0.2"

"104" "300" "0.25"

```

## SQL Code:
```
select product_id, original_price, discount_percentage,  original_price* discount_percentage as discount_amount
from Products
where discount_amount > 50;
```
## Output:
![image](https://github.com/user-attachments/assets/ab47fb81-9438-4dd4-846a-a9237f4a0908)

Question 10 :
---
Write a SQL query to find all employees who were hired on a weekend (Saturday or Sunday) from the emp table

emp table
```
cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT         
```
## SQL Code:
```
select ename,hiredate, strftime("%w",hiredate) as day_of_week
from emp

where strftime("%w",hiredate) in('0','6');

```
## Output:
![image](https://github.com/user-attachments/assets/78931931-6ab9-414d-80e8-6c9b638993bd)

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
