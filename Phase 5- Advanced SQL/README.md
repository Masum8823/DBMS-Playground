<h1 align="center">Advanced SQL</h1>

> ### Explore each topic to understand the core concepts in detail
<p align="center">
  ⬇<b> Click any section below to expand </b> ⬇
</p>

---

<details>  
  <summary><b>Joins</b></summary>

# Joins in SQL

Join হলো SQL-এর সবচেয়ে important topics এর একটি।

JOIN ব্যবহার করা হয় দুই বা তার বেশি table এর data একসাথে combine করার জন্য।

👉 **সহজভাবে:**

JOIN = Multiple tables এর related data একসাথে দেখানো

---

## Why Do We Need JOIN?

Real-world database এ data normally এক table এ রাখা হয় না।

উদাহরণ:

### Students Table

| StudentID | Name | DeptID |
|------------|------|--------|
| 101 | Rahim | 1 |
| 102 | Karim | 2 |
| 103 | Sakib | 1 |

---

### Departments Table

| DeptID | DeptName |
|--------|----------|
| 1 | CSE |
| 2 | EEE |

---

এখন যদি জানতে চাই:

Rahim কোন department এ পড়ে?

Karim কোন department এ পড়ে?

Students table এ DeptID আছে, কিন্তু DeptName নেই।

Departments table এ DeptName আছে, কিন্তু Student Name নেই।

তাই দুই table join করতে হবে।

---

## JOIN Visualization
```sql
Students                Departments

DeptID  ←────────→  DeptID

```
---

## General Syntax
```sql
SELECT columns
FROM Table1
JOIN Table2
ON Table1.column = Table2.column;

```
---

## Tables Used Throughout This Chapter

### Students

| StudentID | Name | DeptID |
|------------|--------|--------|
| 101 | Rahim | 1 |
| 102 | Karim | 2 |
| 103 | Sakib | 1 |
| 104 | Nayeem | 3 |
| 105 | Arafat | NULL |

---

### Departments

| DeptID | DeptName |
|--------|----------|
| 1 | CSE |
| 2 | EEE |
| 4 | BBA |

---

খেয়াল করুন:

- DeptID 3 Departments table এ নেই
- DeptID 4 Students table এ নেই
- Arafat এর DeptID NULL

এই data দিয়েই JOIN গুলো বুঝবো।

---

# 1. INNER JOIN

INNER JOIN শুধুমাত্র matching records return করে।

👉 দুই table এ common data থাকলে শুধু সেটাই দেখাবে।

---

## Syntax
```sql
SELECT *
FROM Students
INNER JOIN Departments
ON Students.DeptID = Departments.DeptID;

```
---

## Query
```sql
SELECT s.Name, d.DeptName
FROM Students s
INNER JOIN Departments d
ON s.DeptID = d.DeptID;

```
---

## Matching Analysis

| Student | DeptID |
|----------|--------|
| Rahim | 1 |
| Karim | 2 |
| Sakib | 1 |

Match পাওয়া গেছে।

---

### Nayeem:
```sql
DeptID = 3
```
---

Departments table এ নেই।

---

### Arafat:
```sql
NULL
```
---

Match হবে না।

---

## Output

| Name | DeptName |
|------|----------|
| Rahim | CSE |
| Karim | EEE |
| Sakib | CSE |

---

👉 শুধুমাত্র matching rows এসেছে।

---

## INNER JOIN Visualization
```sql
Students      Departments

     (Overlap)

        ✔

```
---
# 2. LEFT JOIN

LEFT JOIN বাম পাশের (left table) সব rows দেখায়।

Match থাকলে right table এর data দেখাবে।

Match না থাকলে NULL দেখাবে।

---

## Syntax
```sql
SELECT *
FROM Students
LEFT JOIN Departments
ON Students.DeptID = Departments.DeptID;

```
---

## Query
```sql
SELECT s.Name, d.DeptName
FROM Students s
LEFT JOIN Departments d
ON s.DeptID = d.DeptID;

```
---

## Output

| Name | DeptName |
|------|----------|
| Rahim | CSE |
| Karim | EEE |
| Sakib | CSE |
| Nayeem | NULL |
| Arafat | NULL |

---

### ব্যাখ্যা:

### Nayeem
```sql
DeptID = 3
```
---

Match নেই।

তাই:
```sql
DeptName = NULL
```
---

### Arafat
```sql
DeptID = NULL
```
---

Match নেই।

তাই:
```sql
NULL
```
---

## LEFT JOIN Visualization
```sql
Students      Departments

✔✔✔✔✔
   ✔✔

```
---

👉 Left table এর সব data আসবে।

---
# 3. RIGHT JOIN

RIGHT JOIN ডান পাশের (right table) সব rows দেখায়।

Match থাকলে left table data দেখাবে।

Match না থাকলে NULL দেখাবে।

---

## Syntax
```sql
SELECT *
FROM Students
RIGHT JOIN Departments
ON Students.DeptID = Departments.DeptID;

```
---

## Query
```sql
SELECT s.Name, d.DeptName
FROM Students s
RIGHT JOIN Departments d
ON s.DeptID = d.DeptID;

```
---

## Output

| Name | DeptName |
|------|----------|
| Rahim | CSE |
| Sakib | CSE |
| Karim | EEE |
| NULL | BBA |

---

### ব্যাখ্যা:

Departments table এ:
```sql
DeptID = 4
BBA

```
---

কিন্তু কোনো student নেই।

তাই:
```sql
Name = NULL
```
---

## RIGHT JOIN Visualization
```sql
Students      Departments

   ✔✔
✔✔✔✔✔

```
---

👉 Right table এর সব data আসবে।

---
---
</details>  



<details>  
  <summary><b>Subqueries</b></summary>


---
</details>  



<details>  
  <summary><b>Nested Queries</b></summary>


---
</details>  



<details>  
  <summary><b>UNION</b></summary>


---
</details>  



<details>  
  <summary><b>Views</b></summary>


---
</details>  



<details>  
  <summary><b>Indexing</b></summary>


---
</details>  



<details>  
  <summary><b>Stored Procedure</b></summary>


---
</details>  



<details>  
  <summary><b>Trigger</b></summary>


---
</details>  



<details>  
  <summary><b>Functions</b></summary>


---
</details>  



<details>  
  <summary><b>Transactions</b></summary>


---
</details>  



<details>  
  <summary><b>Commit & Rollback</b></summary>


---
</details>  


