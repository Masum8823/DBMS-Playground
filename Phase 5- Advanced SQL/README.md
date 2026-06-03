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


