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
--
<img width="1200" height="360" alt="image" src="https://github.com/user-attachments/assets/ba1267d8-fcbe-47ca-99e6-418772453c3d" />

```sql
create table Employees(
EmployeeID integer primary key,
FirstName   text not null,
LastName  text not null,
Email  text unique,
Salary real check (Salary>0),
DepartmentID integer,
foreign key (DepartmentID) references Departments(DepartmentID));
```

**Output:**

<img width="1225" height="382" alt="image" src="https://github.com/user-attachments/assets/d6e1f0b9-bbae-48b3-bdad-a3adbcda55b7" />

**Question 2**
---
<img width="903" height="352" alt="image" src="https://github.com/user-attachments/assets/d6de39b5-6172-419b-ba5e-026ef2315d2d" />

```sql
insert into Employee (EmployeeID,Name,Position)
values (4,"Emily White","Analyst")
```

**Output:**

<img width="1078" height="271" alt="image" src="https://github.com/user-attachments/assets/ece7179b-ca01-42cd-bbf7-66abd29cf64a" />

**Question 3**
---
<img width="838" height="308" alt="image" src="https://github.com/user-attachments/assets/c7196516-754d-4088-8201-091488a77f04" />


```sql
insert into customers (CustomerID, Name, Address, Email)
select CustomerID, Name, Address, Email
from  Old_customers
```

**Output:**

<img width="1227" height="249" alt="image" src="https://github.com/user-attachments/assets/d1341814-da00-4583-8ef4-5f76d97d8a1c" />

**Question 4**
---
<img width="1133" height="365" alt="image" src="https://github.com/user-attachments/assets/33a68a18-6d62-4d6e-aa73-3d8e7b8b1ce6" />

```sql
alter table Student_details add column  MobileNumber NUMBER;
alter table Student_details add column Address VARCHAR(100);
```

**Output:**

<img width="1222" height="349" alt="image" src="https://github.com/user-attachments/assets/5ce14c96-fa0b-42b0-83f8-d11f0a61f7bc" />

**Question 5**
---
<img width="763" height="333" alt="image" src="https://github.com/user-attachments/assets/c6024564-b071-4915-b87a-3ff8cd914bf9" />

```sql
create table Products(
ProductID integer Primarykey,
ProductName Not Null,
Price real check(Price>0),
Stock integer Check(Stock>0));
```

**Output:**

<img width="1204" height="243" alt="image" src="https://github.com/user-attachments/assets/886f8ade-8616-4f3d-ab66-b657f09c4670" />

**Question 6**
---
<img width="899" height="347" alt="image" src="https://github.com/user-attachments/assets/61190f24-355d-41aa-8fa8-ba2f493731da" />

```sql
create table Tasks(
TaskID  INTEGER,
TaskName  TEXT,
DueDate DATE);
```

**Output:**

<img width="1232" height="331" alt="image" src="https://github.com/user-attachments/assets/3f1da6a9-cfd1-42c6-b0aa-b72999def51d" />

**Question 7**
---
<img width="780" height="356" alt="image" src="https://github.com/user-attachments/assets/0d953bb8-3c42-4529-aab7-34c8bc4ea7ec" />

```sql
insert into Employee(EmployeeID, Name,Position,Department,Salary)
Values(2,"John Smith","Developer","IT",75000);
insert into Employee(EmployeeID, Name,Position,Department,Salary)
values(3,"Anna Bell","Designer","Marketing", 68000);
```

**Output:**

<img width="1234" height="326" alt="image" src="https://github.com/user-attachments/assets/d77ac046-62f8-400e-81ee-2e1d730418bf" />

**Question 8**
---
<img width="1198" height="290" alt="image" src="https://github.com/user-attachments/assets/a11f032e-96f8-488f-8143-f3f1a99aa353" />

```sql
create table Shipments(
ShipmentID integer primary key,
ShipmentDate Date,
SupplierID Integer,
OrderID Integer,
foreign key (SupplierID) references Suppliers(SupplierID),
foreign key  (OrderID) references Orders(OrderID));
```

**Output:**

<img width="1223" height="215" alt="image" src="https://github.com/user-attachments/assets/a0cfc10d-0841-491c-8341-692209900885" />

**Question 9**
---
<img width="1156" height="279" alt="image" src="https://github.com/user-attachments/assets/d94ec56d-7793-45f0-bdb5-090adee15cde" />

```sql
alter table employee add column first_name varchar(50);
alter table employee add column last_name varchar(50);
```

**Output:**

<img width="1244" height="292" alt="image" src="https://github.com/user-attachments/assets/7b791331-3fcd-424c-a998-dd26c6791bd1" />

**Question 10**
---
<img width="1258" height="403" alt="image" src="https://github.com/user-attachments/assets/aa27ce42-62b0-4679-8959-eabe1e76a7c8" />

```sql
create table contacts(
contact_id INTEGER primary key,
first_name  TEXT  not NULL,
last_name TEXT  not NULL,
email TEXT,
phone text  not null check(length(phone)>=10));
```

**Output:**

<img width="1223" height="282" alt="image" src="https://github.com/user-attachments/assets/1c400eb0-61e4-4f96-bf5b-399646f560f0" />

## Grade
<img width="1380" height="70" alt="image" src="https://github.com/user-attachments/assets/9adb0edd-b7af-432b-8bf2-384960412ca8" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
