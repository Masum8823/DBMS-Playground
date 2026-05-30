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
    <summary> <b> </b> </summary>


---

</details>


<details> 
    <summary> <b> </b> </summary>


---

</details>


<details> 
    <summary> <b> </b> </summary>


---

</details>


<details> 
    <summary> <b> </b> </summary>


---

</details>


<details> 
    <summary> <b> </b> </summary>


---

</details>


<details> 
    <summary> <b> </b> </summary>


---

</details>


<details> 
    <summary> <b> </b> </summary>


---

</details>


<details> 
    <summary> <b> </b> </summary>


---

</details>




