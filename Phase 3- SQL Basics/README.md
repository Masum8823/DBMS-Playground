<details>
    <summary><b>Introduction to SQL</b></summary>
 
# Introduction to SQL

SQL এর full form হলো **Structured Query Language**।

এটি একটি standard programming/query language, যেটা relational database এর সাথে communicate করার জন্য ব্যবহার করা হয়।

👉 সহজভাবে:  
**SQL = database এর সাথে কথা বলার language**

---

# Why SQL is Used?

SQL ব্যবহার করা হয় database এর data:

- store করতে
- retrieve করতে
- update করতে
- delete করতে
- manage করতে

---

# Real-life Example

ধরো university database এ হাজার হাজার student data আছে।

যদি তুমি জানতে চাও:

- কোন student এর CGPA সবচেয়ে বেশি
- কোন department এ কত student আছে
- কোন student DBMS course নিচ্ছে

👉 এসব information SQL query লিখে বের করা হয়।

---

# History of SQL

SQL originally IBM company develop করেছিল 1970s এ।

পরে ANSI (American National Standards Institute) এবং ISO এটাকে standard language হিসেবে approve করে।

---

# Features of SQL

## 1. Easy to Learn

SQL syntax খুব simple এবং human-readable।

📌 Example:

```sql
SELECT * FROM Students;
```

👉 Meaning:  
Students table এর সব data দেখাও

---

## 2. Used in Almost Every Database

প্রায় সব relational DBMS SQL support করে।

📌 Example:

- MySQL
- Oracle
- PostgreSQL
- SQL Server

---

## 3. Fast Data Processing

Large amount of data খুব দ্রুত handle করতে পারে।

---

## 4. Supports Data Security

User permissions এবং access control manage করা যায়।

---

## 5. Portable Language

এক database system থেকে অন্য database system এ relatively সহজে use করা যায়।

---

# Types of SQL Commands

SQL commands সাধারণত 5 ভাগে ভাগ করা হয়।

---

## 1. DDL (Data Definition Language)

Database structure define করার command।

📌 Commands:

- CREATE
- ALTER
- DROP
- TRUNCATE

👉 Table create/change/delete করতে use হয়

---

## 2. DML (Data Manipulation Language)

Data manipulate করার command।

📌 Commands:

- INSERT
- UPDATE
- DELETE

👉 Table এর data manage করতে use হয়

---

## 3. DQL (Data Query Language)

Data retrieve করার command।

📌 Command:

- SELECT

👉 Data দেখার জন্য use হয়

---

## 4. DCL (Data Control Language)

Access permission control করার command।

📌 Commands:

- GRANT
- REVOKE

---

## 5. TCL (Transaction Control Language)

Transaction manage করার command।

📌 Commands:

- COMMIT
- ROLLBACK
- SAVEPOINT

---

# Basic SQL Workflow

📌 Step-by-step:

1. Database create
2. Table create
3. Data insert
4. Data retrieve
5. Data update/delete

---

# Example of a Simple SQL Query

## Student Table

| ID  | Name  | CGPA |
|-----|--------|------|
| 101 | Rahim | 3.90 |
| 102 | Karim | 3.75 |

### Query

```sql
SELECT Name FROM Students;
```

👉 Meaning:  
Students table থেকে শুধু Name column দেখাও

---

# Important Characteristics of SQL

- SQL is not case sensitive
- SQL keywords usually UPPERCASE এ লেখা হয়
- Every query semicolon (`;`) দিয়ে শেষ করা ভালো practice

📌 Example:

```sql
SELECT * FROM Students;
```

---

# Advantages of SQL

- Easy syntax
- Fast query processing
- Large database handle করতে পারে
- Standard language
- Secure data management

---

# Disadvantages of SQL

- Complex queries difficult হতে পারে
- Some database vendors different syntax use করে
- Large systems এ optimization knowledge দরকার হয়

---

# SQL vs DBMS

| SQL | DBMS |
|------|------|
| Language | Software/System |
| Used to communicate with DB | Used to manage database |
| Query writing tool | Complete database manager |

👉 সহজভাবে:

- DBMS = software
- SQL = DBMS এর language

---

# Quick Summary

- SQL = Structured Query Language
- Used for relational databases
- Used to create, retrieve, update, delete data
- Most important command = SELECT
- SQL works with tables

👉 সহজভাবে:  
**SQL হলো database control করার language**
()
---

</details>


<details> 
    <summary> <b>Installing Database Software</b> </summary>

# Installing Database Software

Database নিয়ে কাজ করার জন্য প্রথমে database software install করতে হয়। Different DBMS এর জন্য different tools ব্যবহার করা হয়।

---

## 📌 Common Database Software

- MySQL
- XAMPP
- phpMyAdmin
- SQL Server
- SQL Server Management Studio (SSMS)

---

# MySQL

MySQL হলো সবচেয়ে popular relational database management system (RDBMS) গুলোর একটি।

এটা Oracle company maintain করে।

👉 সহজভাবে:
MySQL = database software যেখানে data store করা হয়

---

## Features of MySQL

- Open-source
- Fast performance
- SQL support করে
- Web development এ খুব popular
- Large database handle করতে পারে

---

## Where MySQL is Used?

- Websites
- University systems
- Banking systems
- E-commerce websites

📌 Example:
Facebook এর early versions এ MySQL use করা হতো

---

# XAMPP

XAMPP হলো একটি local server package, যেটা web development এর জন্য use করা হয়।

👉 XAMPP এর ভিতরে থাকে:

- Apache Server
- MySQL / MariaDB
- PHP
- phpMyAdmin

---

## Full Form of XAMPP

| Letter | Meaning |
|--------|--------|
| X | Cross-platform |
| A | Apache |
| M | MySQL/MariaDB |
| P | PHP |
| P | Perl |

---

## Why XAMPP is Used?

- Localhost server create করতে
- PHP project run করতে
- MySQL database manage করতে

---

## XAMPP Installation Process

### Step 1
Official website থেকে XAMPP download করো (Windows version)

---

### Step 2
Installer run করো

---

### Step 3
Components select করো:

- Apache
- MySQL
- phpMyAdmin
- PHP

---

### Step 4
Install location choose করো

📌 Usually:
```text
C:\xampp
```

Step 5:
Install complete হলে XAMPP Control Panel open করো

---

Step 6:
Apache এবং MySQL Start করো

যদি সব ঠিক থাকে তাহলে green status show করবে

---

# phpMyAdmin

phpMyAdmin হলো web-based MySQL database management tool।

👉 সহজভাবে:
phpMyAdmin = browser দিয়ে MySQL control করার interface

---

## Why phpMyAdmin is Used?

- Database create করা
- Table create করা
- SQL query run করা
- Data insert/update/delete করা

---

## How to Open phpMyAdmin

XAMPP start করার পর browser এ যাও:

```
http://localhost/phpmyadmin
```

---

## Features of phpMyAdmin

- GUI based interface
- Easy for beginners
- SQL query editor আছে
- Database import/export করা যায়

---

# SQL Server

SQL Server হলো Microsoft এর relational DBMS।

👉 Enterprise level application এ অনেক use হয়।

📌 Example:

- Banking software
- Corporate systems
- Large business applications

---

# SQL Server Management Studio (SSMS)

SSMS হলো Microsoft SQL Server manage করার official graphical tool।

👉 সহজভাবে:
SSMS = SQL Server control করার software/interface

---

## Why SSMS is Important?

তুমি যেহেতু SSMS দিয়ে SQL শিখছো, তাই এটা important।

এখানে:

- SQL query লেখা যায়
- Database create করা যায়
- Table manage করা যায়
- Data দেখা যায়
- Backup নেওয়া যায়

---

# Installing SQL Server Management Studio (SSMS)

## Step 1: Install SQL Server First

SSMS install করার আগে SQL Server install থাকতে হবে।

📌 Download:
Microsoft SQL Server Developer Edition download করতে হয়

---

## Step 2: Run SQL Server Installer

Installer open করার পর:

- Basic installation select করো

---

## Step 3: Wait for Installation

SQL Server engine install হতে কিছু time লাগবে

---

## Step 4: Install SSMS

এখন SQL Server Management Studio download করো

📌 Official tool by Microsoft

---

## Step 5: Run SSMS Installer

Installer open করে:

- Install button click করো

---

## Step 6: Restart PC (Optional)

কখনো restart লাগতে পারে

Step 7: Open SSMS

Windows search এ:

SQL Server Management Studio

search করে open করো

---

# Connecting to SQL Server in SSMS

SSMS open করলে “Connect to Server” window আসবে।

---

## Server Name

Usually:
```
localhost
```

or
```
.\SQLEXPRESS
```

---

## Authentication

Usually:

Windows Authentication use করা হয় beginners এর জন্য

---

## Connect Button Click

সব ঠিক থাকলে SQL Server connect হয়ে যাবে

---

# Inside SSMS

Connect হওয়ার পর left side এ Object Explorer দেখা যাবে।

এখানে:

- Databases
- Tables
- Views
- Security
- Programmability

সব manage করা যায়।

---

# SQL Query Window

New Query button click করলে query editor open হবে।

📌 Example:

```sql
SELECT * FROM Students;
```

# Quick Summary

| Software | Purpose |
|----------|--------|
| MySQL | Database server |
| XAMPP | Local server package |
| phpMyAdmin | Web-based MySQL manager |
| SQL Server | Microsoft DBMS |
| SSMS | SQL Server GUI tool |

---

👉 সহজভাবে:

- MySQL = database  
- XAMPP = local server package  
- phpMyAdmin = browser দিয়ে database control  
- SQL Server = Microsoft DBMS  
- SSMS = SQL শেখার GUI tool  
()
---

</details>


<details> 
    <summary> <b>Creating Database and Database Table </b> </summary>

# Creating Database

Database create করা হলো SQL শেখার প্রথম practical step।

👉 সহজভাবে:
Database = container যেখানে tables এবং data store করা হয়

---

## SQL Syntax for Creating Database
``` sql
CREATE DATABASE database_name;
```
Example:
```sql
CREATE DATABASE UniversityDB;
```
👉 এখানে:

- CREATE DATABASE = নতুন database তৈরি করার command  
- UniversityDB = database এর নাম  

---

## How to Run in SSMS

### Step 1:
SSMS open করো

### Step 2:
New Query button এ click করো

### Step 3:
Query লিখো:

```sql
CREATE DATABASE UniversityDB;
```

### Step 4:
Execute button press করো

---

## Output
```sql
Command(s) completed successfully.
```

👉 Database successfully create হয়েছে

---

## Refresh Database List

Object Explorer → Databases → Refresh

👉 সেখানে UniversityDB দেখতে পাবে

---

## Using a Database

Database create করার পরে সেটাকে use করতে হয়।

### Syntax:
```sql
USE database_name;
```
Example:

```sql
USE UniversityDB;
```
👉 এখন থেকে সব table এই database এর ভিতরে create হবে

---

# Creating Tables

Table হলো database এর main structure যেখানে actual data store হয়।

👉 সহজভাবে:
Table = organized data sheet

---

## Table Structure

Table তৈরি করার সময় define করতে হয়:

- Column name  
- Data type  
- Constraints  

---

## Basic Syntax
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype
);
```
---

## Example 1: Simple Student Table

```sql
CREATE TABLE Students (
    ID INT,
    Name VARCHAR(50),
    CGPA FLOAT
);
```

### Explanation

| Part | Meaning |
|------|--------|
| Students | Table name |
| ID | Column |
| INT | Integer data type |
| Name | Text column |
| VARCHAR(50) | Maximum 50 characters |
| CGPA | Decimal value |
| FLOAT | Floating number |

---

## Data Types in SQL

### INT
Integer number store করে

📌 Example:
```sql
ID INT
```
---

### VARCHAR(n)
Text/string store করে

📌 Example:
```sql
Name VARCHAR(50)
```
👉 Maximum 50 characters

---

### FLOAT
Decimal number store করে

📌 Example:
```sql
CGPA FLOAT
```
---

### DATE
Date store করে

📌 Example:
```sql
BirthDate DATE
```
---

## Example 2: Table with Constraints
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    CGPA FLOAT CHECK (CGPA <= 4.00)
);
```
### Explanation

- PRIMARY KEY → StudentID unique হবে এবং NULL হবে না  
- NOT NULL → Name অবশ্যই দিতে হবে  
- UNIQUE → Same email repeat করা যাবে না  
- CHECK → CGPA 4.00 এর বেশি হতে পারবে না  

---

## Example 3: Department Table
```sql
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY,
    DeptName VARCHAR(50)
);
```
---

## Example 4: Foreign Key Relationship
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    DeptID INT,
    FOREIGN KEY (DeptID) REFERENCES Departments(DeptID)
);
```
### Explanation

👉 এখানে:

- DeptID foreign key  
- এটা Departments table এর DeptID কে reference করছে  

---

## Viewing Tables in SSMS

Method:

Database → Tables → Refresh

👉 সব created tables দেখা যাবে

---

## Common Errors While Creating Table

### 1. Missing Comma
❌ Wrong:

```sql
ID INT
Name VARCHAR(50)
```
✅ Correct:

```sql
ID INT,
Name VARCHAR(50)
```


### 2. Missing Parenthesis
❌ Wrong:
```sql
CREATE TABLE Students
ID INT
);
```
---

## Best Practices

- Meaningful table names use করো  
- Proper data type choose করো  
- Primary key use করো  
- Constraints use করো data validation এর জন্য  

---

## Real-life Example

University Database:

- Students  
- Teachers  
- Courses  
- Departments  

👉 সব table মিলেই complete database system তৈরি হয়  

---

## Quick Summary

| Command | Purpose |
|----------|--------|
| CREATE DATABASE | New database তৈরি |
| USE | Database select |
| CREATE TABLE | New table তৈরি |

---

👉 সহজভাবে:

Database তৈরি → USE → Table তৈরি  
Table এ columns + data types define করতে হয়
---

</details>


<details> 
    <summary> <b>Data Types in SQL</b> </summary>

# Data Types in SQL

SQL এ data type define করে একটি column এ কী ধরনের data store করা যাবে।

👉 **সহজভাবে:**  
**Data Type = column এ কোন ধরনের value রাখা যাবে তার rule**

---

## Why Data Types are Important?

Proper data type use করলে:

- Storage save হয়
- Performance better হয়
- Invalid data prevent করা যায়
- Database efficient হয়

---

## Categories of SQL Data Types

Mainly SQL data types কয়েক ভাগে divide করা হয়:

- Numeric Data Types
- Character/String Data Types
- Date & Time Data Types
- Boolean Data Type

---

# 1. Numeric Data Types

এগুলো number store করার জন্য use হয়।

## INT

পূর্ণ সংখ্যা (integer) store করে।

📌 **Example:**

```sql
Age INT
```

👉 **Valid Values:**
- 10
- 25
- 100

❌ **Invalid:**
- 10.5

---

## BIGINT

খুব বড় integer value store করে।

📌 **Example:**

```sql
Phone BIGINT
```

👉 বড় large numbers এর জন্য use হয়

---

## FLOAT

Decimal/floating point numbers store করে।

📌 **Example:**
```sql
CGPA FLOAT
```
👉 **Valid:**
- 3.75
- 4.00

---

## DECIMAL(p,s)

Fixed decimal value store করে।

📌 **Example:**
```sql
Salary DECIMAL(10,2)
```
👉 এখানে:

- 10 = total digits
- 2 = decimal places

📌 **Example Value:**

- 25000.50

---

### Numeric Data Type Example
```sql
CREATE TABLE Students (
    ID INT,
    CGPA FLOAT,
    Salary DECIMAL(10,2)
);

```
---

# 2. Character / String Data Types

Text/string store করার জন্য use হয়।

## CHAR(n)

Fixed length string store করে।

📌 **Example:**
```sql
Gender CHAR(1)
```
👉 যদি value হয়:
```sql
'M'
```
তাহলে remaining space automatically fill হয়

---

## VARCHAR(n)

Variable length string store করে।

📌 **Example:**
```sql
Name VARCHAR(50)
```
👉 Maximum 50 characters পর্যন্ত store করতে পারবে

---

## TEXT

Large text store করার জন্য use হয়।

📌 **Example:**
```sql
Address TEXT
```
---

## CHAR vs VARCHAR

| CHAR | VARCHAR |
|--------|--------|
| Fixed length | Variable length |
| Faster | Storage efficient |
| Extra space নেয় | Only needed space নেয় |

---

### Example
```sql
CREATE TABLE Teachers (
    Name VARCHAR(100),
    Gender CHAR(1)
);

```
---

# 3. Date & Time Data Types

Date এবং time related data store করার জন্য use হয়।

## DATE

শুধু date store করে।

📌 **Format:**
```txt
YYYY-MM-DD
```
📌 **Example:**
```sql
BirthDate DATE
```
---

## TIME

শুধু time store করে।

📌 **Example:**
```sql
TIME
```
---

## DATETIME

Date + time একসাথে store করে।

📌 **Example:**
```sql
JoinDate DATETIME
```
---

### Example
```sql
CREATE TABLE Employees (
    JoinDate DATE,
    LoginTime TIME
);

```
---

# 4. Boolean Data Type

True/False values store করার জন্য use হয়।
📌 **Example:**
```sql
IsActive BIT
```

👉 **Usually:**

- 1 = True
- 0 = False

---

## Complete Practical Example
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Gender CHAR(1),
    CGPA FLOAT,
    Salary DECIMAL(10,2),
    BirthDate DATE
);

```
---

## Explanation

| Column | Data Type | Purpose |
|----------|----------|----------|
| StudentID | INT | Integer ID |
| Name | VARCHAR | Student name |
| Gender | CHAR | Single character |
| CGPA | FLOAT | Decimal number |
| Salary | DECIMAL | Exact decimal |
| BirthDate | DATE | Date |

---

## Choosing Correct Data Type

### Example:

- ID → INT
- Name → VARCHAR
- Price → DECIMAL
- Date → DATE
- Gender → CHAR(1)

---

## Common Mistakes

### 1. Wrong Data Type

❌ **Example:**
```sql
Phone INT
```
👉 **Problem:**  
Phone number বড় হলে issue হতে পারে

✅ **Better:**
```sql
Phone BIGINT
```
---

### 2. Small VARCHAR Size

❌ **Example:**
```sql
Name VARCHAR(5)
```
👉 “Rahim Hasan” store হবে না

---

## Quick Summary

| Data Type | Used For |
|----------|----------|
| INT | Integer |
| BIGINT | Large integer |
| FLOAT | Decimal number |
| DECIMAL | Exact decimal |
| CHAR | Fixed text |
| VARCHAR | Variable text |
| TEXT | Large text |
| DATE | Date |
| TIME | Time |
| DATETIME | Date & time |
| BIT | Boolean |

---

👉 **সহজভাবে:**

- Numbers → INT/FLOAT
- Text → VARCHAR
- Date → DATE
- True/False → BIT

---

</details>


<details> 
    <summary> <b>INSERT Query</b> </summary>

# INSERT Query in SQL

INSERT query ব্যবহার করা হয় table এর ভিতরে নতুন data/record add করার জন্য।

👉 সহজভাবে:

**INSERT = table এ নতুন data ঢোকানো**

---

## Basic Syntax of INSERT Query
```sql
INSERT INTO table_name
VALUES (value1, value2, value3);

```
---

## Example 1: Simple Insert

ধরো আমাদের Students নামে table আছে।

```sql
CREATE TABLE Students (
    ID INT,
    Name VARCHAR(50),
    CGPA FLOAT
);

```
### Insert Data

```sql
INSERT INTO Students
VALUES (101, 'Rahim', 3.90);

```
---

## Explanation

| Part | Meaning |
|--------|--------|
| INSERT INTO | data insert করার command |
| Students | table name |
| VALUES | values provide করা |
| 101 | ID |
| 'Rahim' | Name |
| 3.90 | CGPA |

---

## Viewing Inserted Data

```sql
SELECT * FROM Students;
```
### Output

| ID | Name | CGPA |
|----|------|------|
| 101 | Rahim | 3.90 |

---

## Important Rule

String/Text values অবশ্যই single quotation (' ') এর ভিতরে লিখতে হয়।

✅ Correct:
```sql
'Rahim'
```
❌ Wrong:
```sql
Rahim
```
---

## Insert Multiple Rows

এক query দিয়েও multiple rows insert করা যায়।

---

## Example 2
```sql
INSERT INTO Students
VALUES
(101, 'Rahim', 3.90),
(102, 'Karim', 3.75),
(103, 'Sakib', 3.80);

```
### Output

| ID | Name | CGPA |
|----|------|------|
| 101 | Rahim | 3.90 |
| 102 | Karim | 3.75 |
| 103 | Sakib | 3.80 |

👉 এটা faster এবং professional way

---

## Insert Specific Columns

সব column এ data insert না করে specific columns এও insert করা যায়।

### Syntax
```sql
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);

```
---

## Example 3
```sql
INSERT INTO Students (ID, Name)
VALUES (104, 'Nayeem');

```
### What Happens?

CGPA value দেওয়া হয়নি, তাই:

- NULL হবে

or

- DEFAULT value বসবে (if defined)

---

## Example with DEFAULT Constraint
```sql
CREATE TABLE Students (
    ID INT,
    Name VARCHAR(50),
    City VARCHAR(30) DEFAULT 'Dhaka'
);

```
### Insert Query
```sql
INSERT INTO Students (ID, Name)
VALUES (105, 'Arafat');

```
### Output

| ID | Name | City |
|----|------|------|
| 105 | Arafat | Dhaka |

👉 City automatic "Dhaka" হয়েছে

---

## INSERT with DATE Data Type
 
---

## Example 4
```sql
CREATE TABLE Employees (
    ID INT,
    Name VARCHAR(50),
    JoinDate DATE
);

```
### Insert Data
```sql
INSERT INTO Employees
VALUES (1, 'Rahim', '2026-05-26');

```
👉 Date format:
```sql
YYYY-MM-DD
```
---

## INSERT with Foreign Key

### Parent Table
```sql
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY,
    DeptName VARCHAR(50)
);

```
### Insert Department Data
```sql
INSERT INTO Departments
VALUES
(1, 'CSE'),
(2, 'EEE');

```
### Child Table
```sql
CREATE TABLE Students (
    StudentID INT,
    Name VARCHAR(50),
    DeptID INT,
    FOREIGN KEY (DeptID)
    REFERENCES Departments(DeptID)
);

```
### Insert Student Data
```sql
INSERT INTO Students
VALUES
(101, 'Rahim', 1),
(102, 'Karim', 2);

```
👉 এখানে:

- DeptID = 1 means CSE
- DeptID = 2 means EEE

---

## INSERT Using NULL

---

## Example 5
```sql
INSERT INTO Students
VALUES (106, 'Sabbir', NULL);

```
👉 CGPA value এখন empty

---

## Common Errors in INSERT Query

### 1. Column Count Mismatch

❌ Wrong:
```sql
INSERT INTO Students
VALUES (101, 'Rahim');

```

👉 কিন্তু table এ 3টা column আছে

---

### 2. Wrong Data Type

❌ Wrong:
```sql
INSERT INTO Students
VALUES ('ABC', 'Rahim', 3.90

```
👉 ID INT হওয়ায় error দিবে

---

### 3. Missing Quotes

❌ Wrong:
```sql
INSERT INTO Students
VALUES (101, Rahim, 3.90);

```
---

## Best Practices

- Column names specify করা ভালো practice
- Proper data types use করো
- Multiple insert use করো performance এর জন্য
- String values quotes এর ভিতরে লিখো

---

## Real-life Example

### Online Shopping System

### Products Table
```sql
CREATE TABLE Products (
    ProductID INT,
    ProductName VARCHAR(100),
    Price DECIMAL(10,2)
);

```
### Insert Products
```sql
INSERT INTO Products
VALUES
(1, 'Laptop', 85000.50),
(2, 'Mouse', 1200.00),
(3, 'Keyboard', 2500.00);

```
---

## Quick Summary

| Query | Purpose |
|---------|---------|
| INSERT INTO | Data insert |
| VALUES | Inserted values |
| Multiple VALUES | Multiple rows insert |

---

👉 সহজভাবে:

- INSERT = new data add
- VALUES = inserted values
- Multiple rows একসাথে insert করা যায়
---

</details>


<details> 
    <summary> <b>SELECT Query</b> </summary>

# SELECT Query in SQL

SELECT query হলো SQL এর সবচেয়ে important এবং সবচেয়ে বেশি ব্যবহার হওয়া query।

এটা database table থেকে data retrieve/show করার জন্য use করা হয়।

👉 **সহজভাবে:**

**SELECT = database থেকে data দেখা**

---

## Basic Syntax
```sql
SELECT column_name
FROM table_name;

```
---

## Example Table

ধরো আমাদের Students table আছে:

| StudentID | Name  | Department | CGPA |
|------------|--------|------------|------|
| 101 | Rahim | CSE | 3.90 |
| 102 | Karim | EEE | 3.75 |
| 103 | Sakib | CSE | 3.85 |

---

## SELECT All Columns

সব data দেখতে * ব্যবহার করা হয়।

### Example 1
```sql
SELECT * FROM Students;
```
### Output

| StudentID | Name | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.90 |
| 102 | Karim | EEE | 3.75 |
| 103 | Sakib | CSE | 3.85 |

👉 **\* means all columns**

---

## SELECT Specific Columns

সব column না দেখিয়ে specific columns ও show করা যায়।

### Example 2
```sql
SELECT Name, CGPA
FROM Students;

```
### Output

| Name | CGPA |
|------|------|
| Rahim | 3.90 |
| Karim | 3.75 |
| Sakib | 3.85 |

👉 শুধু Name এবং CGPA show হবে

---

## Using WHERE Clause

WHERE condition ব্যবহার করে specific data filter করা হয়।

👉 **সহজভাবে:**

**WHERE = condition based selection**

### Syntax
```sql
SELECT column_name
FROM table_name
WHERE condition;

```
### Example 3: Exact Match
```sql
SELECT *
FROM Students
WHERE Department = 'CSE';

```
### Output

| StudentID | Name | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.90 |
| 103 | Sakib | CSE | 3.85 |

👉 শুধু CSE students show করবে

---

## Comparison Operators

| Operator | Meaning |
|-----------|---------|
| = | Equal |
| > | Greater than |
| < | Less than |
| >= | Greater or equal |
| <= | Less or equal |
| <> / != | Not equal |

---

### Example 4: Greater Than
```sql
SELECT *
FROM Students
WHERE CGPA > 3.80;

```
### Output

| StudentID | Name | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |
| 103 | Sakib | 3.85 |

---

## AND Operator

Multiple conditions একসাথে use করতে AND ব্যবহার হয়।

### Example 5
```sql
SELECT *
FROM Students
WHERE Department = 'CSE'
AND CGPA > 3.85;

```
### Output

| StudentID | Name | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.90 |

👉 দুই condition true হতে হবে

---

## OR Operator

একাধিক condition এর যেকোনো একটি true হলেই data show হবে।

### Example 6
```sql
SELECT *
FROM Students
WHERE Department = 'EEE'
OR CGPA > 3.85;

```
---

## NOT Operator

Condition reverse করতে use হয়।

### Example 7
```sql
SELECT *
FROM Students
WHERE NOT Department = 'CSE';

```
👉 CSE ছাড়া সব students দেখাবে

---

## ORDER BY

Data sorting করার জন্য use হয়।

### Ascending Order (ASC)

### Example 8
```sql
SELECT *
FROM Students
ORDER BY CGPA ASC;

```
👉 ছোট থেকে বড় order

### Descending Order (DESC)

### Example 9

👉 বড় থেকে ছোট order
```sql
SELECT *
FROM Students
ORDER BY CGPA DESC;

```
---

## DISTINCT Keyword

Duplicate values remove করে unique values show করে।

### Example 10
```sql
SELECT DISTINCT Department
FROM Students;

```
### Output

| Department |
|------------|
| CSE |
| EEE |

👉 Duplicate department remove হয়েছে

---

## TOP Keyword (SQL Server)

নির্দিষ্ট সংখ্যক rows show করার জন্য use হয়।

### Example 11
```sql
SELECT TOP 2 *
FROM Students;

```
👉 প্রথম 2টা row show করবে

---

## LIKE Operator

Pattern matching এর জন্য use হয়।

### Wildcards

| Symbol | Meaning |
|---------|---------|
| % | Any characters |
| _ | Single character |

### Example 12: Name Starts with R
```sql
SELECT *
FROM Students
WHERE Name LIKE 'R%';

```
👉 R দিয়ে শুরু হওয়া names show করবে

### Example 13: Ends with m

👉 m দিয়ে শেষ হওয়া names show করবে
```sql
SELECT *
FROM Students
WHERE Name LIKE '%m';

```
---

## BETWEEN Operator

Range এর মধ্যে value check করে।

### Example 14
```sql
SELECT *
FROM Students
WHERE CGPA BETWEEN 3.70 AND 4.00;

```
👉 3.70 থেকে 4.00 এর মধ্যে CGPA

---

## IN Operator

Multiple values check করার জন্য use হয়।

### Example 15
```sql
SELECT *
FROM Students
WHERE Department IN ('CSE', 'EEE');

```
👉 CSE এবং EEE students show করবে

---

## IS NULL

NULL values check করার জন্য use হয়।

### Example 16
```sql
SELECT *
FROM Students
WHERE CGPA IS NULL;

```
👉 যাদের CGPA empty তাদের দেখাবে

---

## Aliasing (AS)

Temporary column name দেওয়া যায়।

### Example 17
```sql
SELECT Name AS Student_Name
FROM Students;

```
---

## Aggregate Functions with SELECT

### COUNT()
```sql
SELECT COUNT(*) FROM Students;
```
👉 মোট কত student আছে

### AVG()
```sql
SELECT AVG(CGPA) FROM Students;
```
👉 Average CGPA

### MAX()
```sql
SELECT MAX(CGPA) FROM Students;
```
👉 Highest CGPA

### MIN()
```sql
SELECT MIN(CGPA) FROM Students;
```
👉 Lowest CGPA

---

## Real-life Example

### Online Store

### Products Table

| ProductID | ProductName | Price |
|------------|------------|--------|
| 1 | Laptop | 85000 |
| 2 | Mouse | 1200 |
| 3 | Keyboard | 2500 |

### Query
```sql
SELECT ProductName, Price
FROM Products
WHERE Price > 2000;

```
👉 ২০০০ টাকার বেশি products show করবে

---

## Common Errors

### 1. Missing Quotes

❌ Wrong:
```sql
WHERE Name = Rahim
```
✅ Correct:
```sql
WHERE Name = 'Rahim'
```
### 2. Wrong Column Name

❌ Wrong:
```sql
SELECT Marks FROM Students;
```
👉 যদি Marks column না থাকে error দিবে

---

## Quick Summary

| Keyword | Purpose |
|----------|----------|
| SELECT | Data retrieve |
| WHERE | Filtering |
| ORDER BY | Sorting |
| DISTINCT | Unique values |
| LIKE | Pattern matching |
| BETWEEN | Range check |
| IN | Multiple values |
| IS NULL | NULL checking |

---

👉 **সহজভাবে:**

- SELECT = data show
- WHERE = filter
- ORDER BY = sort
- DISTINCT = unique
- LIKE = pattern search

---

</details>


<details> 
    <summary> <b>WHERE Clause</b> </summary>

# WHERE Clause in SQL

WHERE clause ব্যবহার করা হয় SQL query এর মধ্যে condition দিয়ে data filter করার জন্য।

👉 **সহজভাবে:**

**WHERE = নির্দিষ্ট condition অনুযায়ী data select করা**

---

## Basic Syntax
```sql
SELECT column_name
FROM table_name
WHERE condition;

```
---

## Example Table (Students)

| StudentID | Name | Department | CGPA | Age |
|------------|--------|------------|------|-----|
| 101 | Rahim | CSE | 3.90 | 21 |
| 102 | Karim | EEE | 3.75 | 22 |
| 103 | Sakib | CSE | 3.85 | 20 |
| 104 | Nayeem | BBA | 3.60 | 23 |
| 105 | Arafat | CSE | 3.95 | 21 |

---

## 1. Simple WHERE (Equality)

### Example 1
```sql
SELECT *
FROM Students
WHERE Department = 'CSE';

```
👉 CSE department এর সব students দেখাবে

---

## 2. WHERE with Number Condition

### Example 2
```sql
SELECT *
FROM Students
WHERE CGPA > 3.80;

```
👉 CGPA 3.80 এর বেশি students দেখাবে

### Example 3
```sql
SELECT *
FROM Students
WHERE Age >= 21;

```
👉 21 বা তার বেশি বয়সের students

---

## 3. WHERE with NOT EQUAL

### Example 4
```sql
SELECT *
FROM Students
WHERE Department <> 'EEE';

```
👉 EEE ছাড়া সব departments

---

## 4. WHERE with AND Operator

AND মানে সব condition true হতে হবে

### Example 5
```sql
SELECT *
FROM Students
WHERE Department = 'CSE'
AND CGPA > 3.85;

```
👉 CSE department + CGPA 3.85 এর বেশি

### Output

- Rahim (3.90)
- Arafat (3.95)

---

## 5. WHERE with OR Operator

OR মানে যেকোনো এক condition true হলেই data আসবে

### Example 6
```sql
SELECT *
FROM Students
WHERE Department = 'EEE'
OR CGPA > 3.90;

```
👉 EEE students + high CGPA students

---

## 6. WHERE with NOT Operator

NOT মানে condition reverse করা

### Example 7
```sql
SELECT *
FROM Students
WHERE NOT Department = 'CSE';

```
👉 CSE ছাড়া সব students

---

## 7. WHERE with BETWEEN

BETWEEN ব্যবহার হয় range check করার জন্য

### Example 8
```sql
SELECT *
FROM Students
WHERE CGPA BETWEEN 3.70 AND 3.90;

```
👉 3.70 থেকে 3.90 এর মধ্যে CGPA

---

## 8. WHERE with IN

IN ব্যবহার হয় multiple specific values check করার জন্য

### Example 9
```sql
SELECT *
FROM Students
WHERE Department IN ('CSE', 'EEE');

```
👉 শুধু CSE এবং EEE students

---

## 9. WHERE with LIKE (Pattern Matching)

LIKE ব্যবহার হয় text pattern search করার জন্য

### Example 10: Starts with 'R'
```sql
SELECT *
FROM Students
WHERE Name LIKE 'R%';

```
👉 R দিয়ে শুরু হওয়া নাম

### Example 11: Ends with 'm'
```sql
SELECT *
FROM Students
WHERE Name LIKE '%m';

```
👉 m দিয়ে শেষ হওয়া নাম

### Example 12: Contains 'a'
```sql
SELECT *
FROM Students
WHERE Name LIKE '%a%';

```
👉 নামের মধ্যে কোথাও 'a' আছে এমন

---

## 10. WHERE with NULL

NULL মানে কোনো value নাই

### Example 13
```sql
SELECT *
FROM Students
WHERE CGPA IS NULL;

```
👉 যাদের CGPA দেওয়া নাই

---

## 11. WHERE with NOT NULL

### Example 14
```sql
SELECT *
FROM Students
WHERE CGPA IS NOT NULL;

```
👉 যাদের CGPA আছে

---

## 12. Complex WHERE Condition

### Example 15
```sql
SELECT *
FROM Students
WHERE Department = 'CSE'
AND CGPA > 3.80
AND Age = 21;

```
👉 CSE + CGPA > 3.80 + Age 21

---

## 13. WHERE with Arithmetic Condition

### Example 16
```sql
SELECT *
FROM Students
WHERE CGPA + 0.1 > 4.00;

```
👉 calculated condition use করা যায়

---

## 14. Real-life Example

### Online Shop Table

| ProductID | Name | Price | Stock |
|------------|--------|--------|--------|
| 1 | Laptop | 85000 | 10 |
| 2 | Mouse | 1200 | 0 |
| 3 | Keyboard | 2500 | 5 |

### Example Query
```sql
SELECT *
FROM Products
WHERE Price > 2000
AND Stock > 0;

```
👉 শুধু available + expensive products

---

# Common Mistakes

## 1. Missing Quotes

❌ Wrong:
```sql
WHERE Name = Rahim
```
✅ Correct:
```sql
WHERE Name = 'Rahim'
```
---

## 2. Wrong NULL Check

❌ Wrong:
```sql
WHERE CGPA = NULL
```
✅ Correct:
```sql
WHERE CGPA IS NULL
```
---

# Quick Summary

| Operator | Meaning |
|-----------|---------|
| = | Equal |
| > < | Comparison |
| AND | All true |
| OR | Any true |
| NOT | Reverse |
| BETWEEN | Range |
| IN | Multiple values |
| LIKE | Pattern |
| IS NULL | Empty check |

---

👉 **সহজভাবে:**

**WHERE = data filter system**
---

</details>


<details> 
    <summary> <b>ORDER BY</b> </summary>


---

</details>


<details> 
    <summary> <b>LIMIT</b> </summary>


---

</details>


<details> 
    <summary> <b>DISTINCT</b> </summary>


---

</details>





