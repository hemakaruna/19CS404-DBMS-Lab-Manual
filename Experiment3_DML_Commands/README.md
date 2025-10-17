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
**Question 1**
--
-- Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

<img width="345" height="197" alt="image" src="https://github.com/user-attachments/assets/73caefd4-5587-44b6-a432-7fe1335b3ec1" />


```sql

UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15
  AND sale_date = '2023-01-31';


```

**Output:**
<img width="1308" height="306" alt="image" src="https://github.com/user-attachments/assets/0d1057f3-4687-439a-9009-d277dce0ab6d" />


**Question 2**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

<img width="266" height="282" alt="image" src="https://github.com/user-attachments/assets/1411bab7-82a4-4b67-a3eb-985c2929251a" />


```sql
UPDATE suppliers
SET supplier_name = UPPER(supplier_name)
WHERE contact_person LIKE '% Singh';

```

**Output:**

<img width="1382" height="172" alt="image" src="https://github.com/user-attachments/assets/1c47ea44-4d9c-46a7-90eb-3021d34fba98" />


**Question 3**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

<img width="258" height="152" alt="image" src="https://github.com/user-attachments/assets/d53bd2de-ee62-4015-9e5d-a3802c5bf77e" />


```sql
UPDATE suppliers
SET supplier_name = 'A1 Suppliers'
WHERE supplier_id = 8;

```

**Output:**

<img width="1140" height="182" alt="image" src="https://github.com/user-attachments/assets/ca0729b8-a598-4050-95f3-9d08d35a46ac" />


**Question 4**
---
Write a query to fetch all the records from the EmployeeInfo table ordered by EmpLname in descending order and Department in the ascending order.

<img width="758" height="358" alt="image" src="https://github.com/user-attachments/assets/496a9436-1343-42e5-ab0e-11300ca79d9b" />


```sql
SELECT EmpID, EmpFname, EmpLname, Department,Project, Address,  DOB, Gender
FROM EmployeeInfo
ORDER BY  EmpFname DESC;
```

**Output:**
<img width="1418" height="228" alt="image" src="https://github.com/user-attachments/assets/30fd15a8-a798-4564-92d1-5bbcc1181919" />


**Question 5**
---
Write a SQL statement to display name and commission of first 5 salesmen.

table info

salesman(name,commission) 

<img width="215" height="180" alt="image" src="https://github.com/user-attachments/assets/6c0de0b5-c0a7-4d92-82f0-0002bb6d5ada" />


```sql
SELECT name, commission
FROM salesman
LIMIT 5;

```

**Output:**

<img width="475" height="335" alt="image" src="https://github.com/user-attachments/assets/b6dcaab3-5ff4-49c8-9e5d-c6d10d5d0125" />


**Question 6**
---
Write a SQL query to determine the age group of value1 in the Calculations table as 'Child' if it is less than 13, 'Teen' if it is between 13 and 19, and 'Adult' if it is 20 or older.

<img width="477" height="382" alt="image" src="https://github.com/user-attachments/assets/615b95ab-cd39-4755-b468-9ba1404a2107" />


```sql
SELECT
  id,
  value1,
  CASE
    WHEN value1 < 13 THEN 'Child'
    WHEN value1 BETWEEN 13 AND 19 THEN 'Teen'
    ELSE 'Adult'
  END AS age_group
FROM Calculations;

```

**Output:**

 <img width="602" height="273" alt="image" src="https://github.com/user-attachments/assets/c31940dc-5cdf-433d-96a9-a7c471b337c7" />

**Question 7**
---
Write a query to find the top 2 products with the highest discount percentage. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage

-----------------------------------------------------------

"101" "50" "0.1"

"102" "150" "0.15"

"103" "200" "0.2"

"104" "300" "0.25"

<img width="537" height="182" alt="image" src="https://github.com/user-attachments/assets/3c417c88-4fdf-437c-a127-615fd8f997ae" />

```sql
SELECT 
    product_id,
    original_price,
    discount_percentage,
    ROUND(original_price * (1 - discount_percentage), 2) AS discounted_price
FROM 
    products
ORDER BY 
    discount_percentage DESC
LIMIT 2;
```

**Output:**

<img width="1023" height="176" alt="image" src="https://github.com/user-attachments/assets/39354258-09e1-4a7a-a2cf-4ff95d08b66a" />


**Question 8**
---
Write a query to calculate the discounted_price and  discounted_price_percentage for each product from the products table. Return product_id, original_price, discount_percentage, discounted_price, and discounted_price_percentage.

Discounted Price: Calculate the price of the product after applying the discount.

Discounted Price Percentage: Calculate the percentage that the discounted price represents relative to the original price.

<img width="672" height="193" alt="image" src="https://github.com/user-attachments/assets/6c2d2cba-be03-4d87-a807-3252073b525e" />


```sql
SELECT 
    product_id,
    original_price,
    discount_percentage,
    ROUND(original_price * (1 - discount_percentage), 2) AS discounted_price,
    CAST(ROUND((1 - discount_percentage) * 100) AS INT) || '%' AS discounted_price_percentage
FROM 
    products;

```

**Output:**

<img width="1421" height="210" alt="image" src="https://github.com/user-attachments/assets/2ef88cda-ab4d-4782-b46a-38ad63b1883b" />

**Question 9**
---
Create a report that shows the capitalized FirstName and capitalized LastName renamed as FirstName and Lastname respectively and EmployeeId from the employees table sorted by EmployeeId in descending order.

<img width="295" height="197" alt="image" src="https://github.com/user-attachments/assets/888bd345-da50-41ee-bd8f-051526f05bd1" />

```sql
SELECT 
    UPPER(FirstName) AS FirstName,
    UPPER(LastName) AS LastName,
    EmployeeID
FROM 
    employees
ORDER BY 
    EmployeeID DESC;

```

**Output:**

<img width="642" height="412" alt="image" src="https://github.com/user-attachments/assets/8adcd90c-1c0f-4b7e-a1fb-ab3fc3f41736" />



**Question 10**
---
Write a SQL query to find all employees who were hired in the year 2022 from emp table.


<img width="656" height="237" alt="image" src="https://github.com/user-attachments/assets/ce47745b-10d8-47d4-af81-747862feaf4f" />


```sql
SELECT *
FROM emp
WHERE strftime('%Y', hiredate) = '2022';

```

**Output:**

<img width="1427" height="256" alt="image" src="https://github.com/user-attachments/assets/a5b41e60-ca5c-4cb4-8a0f-5cb480b4cd58" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
