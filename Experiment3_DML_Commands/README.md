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
<img width="872" height="256" alt="image" src="https://github.com/user-attachments/assets/ed45134b-5062-4a62-a4a8-1e52b2052bc4" />

```sql
UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15
  AND sale_date = '2023-01-31';
```

**Output:**
<img width="1227" height="398" alt="image" src="https://github.com/user-attachments/assets/d583cda7-d529-4f74-a245-019f25d48b39" />

**Question 2**
---
<img width="692" height="71" alt="image" src="https://github.com/user-attachments/assets/7a2b121a-e9f5-4730-a735-feafa2572b75" />

```sql
update customer
set grade=5
where city="Chennai"
```

**Output:**

<img width="1269" height="456" alt="image" src="https://github.com/user-attachments/assets/7ea87b92-2f0f-4159-ab9b-9c01e100fc3b" />

**Question 3**
---
<img width="1124" height="498" alt="image" src="https://github.com/user-attachments/assets/fb538a7e-ce16-4b15-aa83-2f62378f0293" />

```sql
UPDATE products
SET sell_price = sell_price * 1.15
WHERE quantity < 50
  AND supplier_id = 10;
```

**Output:**

<img width="1221" height="441" alt="image" src="https://github.com/user-attachments/assets/e60df5ba-5b3b-4def-8450-02e09a9243a0" />

**Question 4**
---
<img width="891" height="460" alt="image" src="https://github.com/user-attachments/assets/a80207eb-f879-4445-8e30-64c76ad9eac7" />

```sql
update suppliers 
set address ='58 Lakeview, Magnolia'
where supplier_id=5;
```

**Output:**

<img width="1211" height="352" alt="image" src="https://github.com/user-attachments/assets/de05a4e9-6ba7-461a-af23-80c2c1581701" />

**Question 5**
---
<img width="1271" height="489" alt="image" src="https://github.com/user-attachments/assets/ffd70805-1a28-4811-886c-8647fcf1a9ec" />

```sql
UPDATE products
SET reorder_lvl = CAST(reorder_lvl * 1.3 AS INT)
WHERE category = 'Food'
  AND quantity < (reorder_lvl * 0.5);
```

**Output:**

<img width="1244" height="441" alt="image" src="https://github.com/user-attachments/assets/01ea1977-302a-494a-83c0-34caaa14be1d" />

**Question 6**
---
<img width="1224" height="447" alt="image" src="https://github.com/user-attachments/assets/5f6bc525-7a7d-48bc-8b29-4f6f58244904" />

```sql
delete from doctors
where last_name='Brown'
and specialization in ('Pediatrics','Cardiology');
```

**Output:**

<img width="1154" height="808" alt="image" src="https://github.com/user-attachments/assets/8faff117-31d3-42a6-86f0-221d01270c94" />

**Question 7**
---
<img width="676" height="502" alt="image" src="https://github.com/user-attachments/assets/fe7c0320-7751-4e30-8efa-ae7bb08f22e2" />

```sql
delete from doctors
where last_name is NULL;
```

**Output:**

<img width="1186" height="616" alt="image" src="https://github.com/user-attachments/assets/9342f141-2afe-494f-bd46-e3038e236b39" />

**Question 8**
---
<img width="1268" height="624" alt="image" src="https://github.com/user-attachments/assets/5cac666b-db12-4d16-a40e-569095a33fdb" />

```sql
delete from customer 
where grade>=2;
```

**Output:**

<img width="644" height="502" alt="image" src="https://github.com/user-attachments/assets/7d071223-c245-4a45-a245-05be29212649" />

**Question 9**
---
<img width="1307" height="257" alt="image" src="https://github.com/user-attachments/assets/8c52a4cd-6318-4314-b03a-ffc19f9077f4" />

```sql
delete from customer
where  CUST_COUNTRY not in ( 'India', 'USA');
```

**Output:**

<img width="1254" height="490" alt="image" src="https://github.com/user-attachments/assets/0e46cff0-ebee-4b4a-aa41-7dd89c4fbcef" />

**Question 10**
---
<img width="1257" height="282" alt="image" src="https://github.com/user-attachments/assets/7955bb54-f528-48e9-9da7-aef65da8de72" />

```sql
delete from customer
where (grade>2 and payment_amt<(select avg(payment_amt)
from customer))
or outstanding_amt>8000;
```

**Output:**

<img width="1233" height="592" alt="image" src="https://github.com/user-attachments/assets/056e7653-72b3-4652-b174-3021c06c9089" />             
## Grade
<img width="1381" height="72" alt="image" src="https://github.com/user-attachments/assets/8a93917b-6a90-4f84-ad55-158f610be3b1" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
