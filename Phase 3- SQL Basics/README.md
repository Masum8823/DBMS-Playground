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
