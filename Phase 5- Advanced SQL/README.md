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
# 4. FULL JOIN (FULL OUTER JOIN)

FULL JOIN দুই table এর সব rows দেখায়।

Match থাকলে combine করবে।

Match না থাকলে NULL দিবে।

---

## Syntax
```sql
SELECT *
FROM Students
FULL JOIN Departments
ON Students.DeptID = Departments.DeptID;

```
---

## Query
```sql
SELECT s.Name, d.DeptName
FROM Students s
FULL JOIN Departments d
ON s.DeptID = d.DeptID;

```
---

## Output

| Name | DeptName |
|------|----------|
| Rahim | CSE |
| Sakib | CSE |
| Karim | EEE |
| Nayeem | NULL |
| Arafat | NULL |
| NULL | BBA |

---

👉 দুই table এর সব data এসেছে।

---

## FULL JOIN Visualization
```sql
Students      Departments

✔✔✔✔✔✔✔✔✔✔

```
---

সব data।

---
## Comparison Table

| JOIN Type | Matching Rows | Unmatched Left | Unmatched Right |
|------------|--------------|----------------|-----------------|
| INNER JOIN | ✅ | ❌ | ❌ |
| LEFT JOIN | ✅ | ✅ | ❌ |
| RIGHT JOIN | ✅ | ❌ | ✅ |
| FULL JOIN | ✅ | ✅ | ✅ |

---

## Easy Memory Trick

### INNER JOIN
```sql
Only Common Friends
```
---

### LEFT JOIN
```sql
Take All From Left
```
---

### RIGHT JOIN
```sql
Take All From Right
```
---

### FULL JOIN
```sql
Take Everything
```
---

## Real-Life University Example

### Students + Departments
```sql
SELECT s.Name, d.DeptName
FROM Students s
INNER JOIN Departments d
ON s.DeptID = d.DeptID;

```
---

### Output:
```sql
Rahim  → CSE
Karim  → EEE
Sakib  → CSE

```
---

### Students Without Department
```sql
SELECT s.Name
FROM Students s
LEFT JOIN Departments d
ON s.DeptID = d.DeptID
WHERE d.DeptID IS NULL;

```
---

### Output:
```sql
Nayeem
Arafat

```
---

👉 Interview এবং viva তে খুব common question।

---

## Common Mistakes

### Mistake 1

ON condition ভুল দেওয়া

❌
```sql
ON Students.StudentID = Departments.DeptID
```
---

এখানে unrelated columns compare হচ্ছে।

---

### Mistake 2

JOIN লিখে ON না দেওয়া

❌
```sql
SELECT *
FROM Students
INNER JOIN Departments;

```
---

Error হবে।

---

### Mistake 3

LEFT JOIN এবং RIGHT JOIN confuse করা

---

মনে রাখুন:
```sql
LEFT JOIN = Left Table Priority

RIGHT JOIN = Right Table Priority

```
---

## Common Viva Questions

### Q: JOIN কী?

Multiple table এর related data combine করার technique।

---

### Q: INNER JOIN কী return করে?

শুধুমাত্র matching rows।

---

### Q: LEFT JOIN কী return করে?

Left table এর সব rows + matching right rows।

---

### Q: RIGHT JOIN কী return করে?

Right table এর সব rows + matching left rows।

---

### Q: FULL JOIN কী return করে?

দুই table এর সব rows।

---

### Q: JOIN এর জন্য সবচেয়ে গুরুত্বপূর্ণ clause কোনটি?

---

কারণ ON condition determine করে কীভাবে tables match হবে।

---

## Quick Summary

```sql
INNER JOIN = Only Matches

LEFT JOIN = All Left + Matches

RIGHT JOIN = All Right + Matches

FULL JOIN = Everything

```
---
</details>  



<details>  
  <summary><b>Subqueries</b></summary>

# Subqueries in SQL

Subquery হলো একটি query এর ভিতরে আরেকটি query।

👉 **সহজভাবে:**

Query এর ভিতরে Query = Subquery

---

## Why Subquery is Needed?

অনেক সময় কোনো data বের করার জন্য আগে অন্য একটা data বের করতে হয়।

উদাহরণ:

- Highest CGPA পাওয়া student কে?
- Average salary এর চেয়ে বেশি salary কার?
- CSE department এর students কারা?
- Highest priced product কোনটা?

এখানে আগে একটা value বের করতে হবে, তারপর সেই value ব্যবহার করে main query run করতে হবে।

এই কাজের জন্য Subquery ব্যবহার করা হয়।

---

## Basic Structure
```sql
SELECT column_name
FROM table_name
WHERE column_name OPERATOR (
    SELECT column_name
    FROM another_table
);

```
---

## How SQL Executes a Subquery?

ধরি query:
```sql
SELECT Name
FROM Students
WHERE CGPA = (
    SELECT MAX(CGPA)
    FROM Students
);

```
---

### Execution Steps:

### Step 1

Subquery execute হবে
```sql
SELECT MAX(CGPA)
FROM Students;

```
---

Output:
```sql
3.95
```
---

### Step 2

Main query execute হবে
```sql
SELECT Name
FROM Students
WHERE CGPA = 3.95;

```
---

Output:
```sql
Arafat
```
---

👉 তাই Subquery সাধারণত আগে execute হয়।

---

## Example Table: Students

| StudentID | Name | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.90 |
| 102 | Karim | EEE | 3.75 |
| 103 | Sakib | CSE | 3.85 |
| 104 | Nayeem | BBA | 3.60 |
| 105 | Arafat | CSE | 3.95 |

---
## 1. Single Row Subquery

যখন Subquery মাত্র ১টি value return করে।

---

### Example 1: Highest CGPA Student
```sql
SELECT Name, CGPA
FROM Students
WHERE CGPA = (
    SELECT MAX(CGPA)
    FROM Students
);

```
---

### Subquery Result
```sql
3.95
```
---

### Final Output

| Name | CGPA |
|------|------|
| Arafat | 3.95 |

---

### Example 2: Lowest CGPA Student
```sql
SELECT Name, CGPA
FROM Students
WHERE CGPA = (
    SELECT MIN(CGPA)
    FROM Students
);

```
---

### Output:

| Name | CGPA |
|------|------|
| Nayeem | 3.60 |

---

### Example 3: Above Average Students

---

### Step 1

Average CGPA বের হবে
```sql
SELECT AVG(CGPA)
FROM Students;

```
---

Result:
```sql
3.81
```
---

### Step 2
```sql
SELECT Name, CGPA
FROM Students
WHERE CGPA > (
    SELECT AVG(CGPA)
    FROM Students
);

```
---

### Output:

| Name | CGPA |
|------|------|
| Rahim | 3.90 |
| Sakib | 3.85 |
| Arafat | 3.95 |

---

👉 Viva favourite question।

---
## 2. Multiple Row Subquery

যখন Subquery multiple values return করে।

---

### Example Tables

### Students

| Name | DeptID |
|------|--------|
| Rahim | 1 |
| Karim | 2 |
| Sakib | 1 |

---

### Departments

| DeptID | DeptName |
|--------|----------|
| 1 | CSE |
| 2 | EEE |

---

### Example 4

CSE department এর students বের করো।

---

### Subquery
```sql
SELECT DeptID
FROM Departments
WHERE DeptName = 'CSE';

```
---

Result:
```sql
1
```
---

### Main Query
```sql
SELECT Name
FROM Students
WHERE DeptID IN (
    SELECT DeptID
    FROM Departments
    WHERE DeptName = 'CSE'
);

```
---

### Output:

| Name |
|------|
| Rahim |
| Sakib |

---

## Why IN Used?

কারণ subquery অনেক value return করতে পারে।

---

### Example:
```sql
1
2
3

```
---

তখন:
```sql
WHERE DeptID IN (...)
```
---

ব্যবহার করতে হয়।

---
## 3. Subquery with IN

---

### Example
```sql
SELECT *
FROM Students
WHERE Department IN (
    SELECT Department
    FROM Students
    WHERE CGPA > 3.90
);

```
---

প্রথমে Subquery:
```sql
CSE
```
---

### Main Query:
```sql
SELECT *
FROM Students
WHERE Department = 'CSE';

```
---

### Output:

সব CSE student।

---

## 4. Subquery with NOT IN

---

### Example
```sql
SELECT *
FROM Students
WHERE DeptID NOT IN (
    SELECT DeptID
    FROM Departments
);

```
---

### Output:

Departments table এ না থাকা students।

---

## 5. Subquery with EXISTS

EXISTS check করে Subquery result empty কি না।

---

### Example
```sql
SELECT Name
FROM Students s
WHERE EXISTS (
    SELECT *
    FROM Departments d
    WHERE s.Department = d.DeptName
);

```
---

👉 Matching department থাকলে row return হবে।

---

## 6. Subquery in SELECT

Subquery শুধু WHERE তেই না, SELECT এও ব্যবহার করা যায়।

---

### Example
```sql
SELECT Name,
(
    SELECT AVG(CGPA)
    FROM Students
) AS AverageCGPA
FROM Students;

```
---

### Output:

| Name | AverageCGPA |
|------|------------|
| Rahim | 3.81 |
| Karim | 3.81 |
| Sakib | 3.81 |

---

## 7. Subquery in FROM

---

### Example
```sql
SELECT *
FROM
(
    SELECT Name, CGPA
    FROM Students
) AS StudentData;

```
---

👉 Temporary table তৈরি হয়।

---

## Real-Life Example

### Product Table

| Product | Price |
|----------|-------|
| Laptop | 80000 |
| Mouse | 1000 |
| Keyboard | 3000 |
| Monitor | 15000 |

---

### Products Above Average Price
```sql
SELECT Product, Price
FROM Products
WHERE Price >
(
    SELECT AVG(Price)
    FROM Products
);

```
---

### Average:
```sql
24750
```
---

### Output:

| Product | Price |
|----------|-------|
| Laptop | 80000 |

---

## Subquery vs JOIN

অনেক কাজ Subquery এবং JOIN দুটো দিয়েই করা যায়।

---

### Subquery
```sql
SELECT Name
FROM Students
WHERE DeptID IN (
    SELECT DeptID
    FROM Departments
    WHERE DeptName = 'CSE'
);

```
---

### JOIN
```sql
SELECT s.Name
FROM Students s
INNER JOIN Departments d
ON s.DeptID = d.DeptID
WHERE d.DeptName = 'CSE';

```
---

দুটোর output একই।

---

## Common Mistakes

---

### Mistake 1

Multiple values return হলেও = ব্যবহার করা

❌
```sql
WHERE DeptID =
(
    SELECT DeptID
    FROM Departments
)

```
---

যদি multiple rows return করে error হবে।

---

✔ Use:
```sql
WHERE DeptID IN (...)
```
---

### Mistake 2

Parentheses ভুলে যাওয়া

❌
```sql
WHERE CGPA >
SELECT AVG(CGPA)
FROM Students

```
---

✔ Correct
```sql
WHERE CGPA >
(
    SELECT AVG(CGPA)
    FROM Students
)

```
---

## Common Viva Questions

### Q: Subquery কী?

একটি query এর ভিতরে আরেকটি query।

---

### Q: Subquery আগে execute হয় নাকি Main Query?

সাধারণত Subquery আগে execute হয়।

---

### Q: Single Row Subquery কী?

যেটা মাত্র একটি value return করে।

---

### Q: Multiple Row Subquery কী?

যেটা একাধিক value return করে।

---

### Q: Multiple Row Subquery এর সাথে কোন operator বেশি ব্যবহার হয়?
IN
---

## Quick Summary

```sql
Subquery = Query inside another Query

Single Row Subquery → 1 Value

Multiple Row Subquery → Many Values

IN → Multiple Values

EXISTS → Check Existence

```
---
</details>  



<details>  
  <summary><b>Nested Queries</b></summary>

# Nested Queries in SQL

Nested Query বলতে এমন Query কে বোঝায় যেখানে একটি Query-এর ভিতরে আরেকটি Query থাকে।

👉 **সহজভাবে:**

Query এর ভিতরে Query = Nested Query

---

## Nested Query vs Subquery

এখানে একটা common confusion আছে।

অনেক বই এবং teacher Subquery ও Nested Query কে একই অর্থে ব্যবহার করেন।

কারণ:
```txt
Every Subquery is a Nested Query
Every Nested Query is a Subquery

```
---

অর্থাৎ SQL-এর context এ সাধারণত দুটো একই জিনিস বোঝায়।

---

## Why Nested Queries Are Used?

যখন Main Query execute করার আগে অন্য Query থেকে information বের করতে হয়।

Examples:

- Highest CGPA student খুঁজতে
- Average CGPA এর উপরের students বের করতে
- CSE department এর students খুঁজতে
- Most expensive product খুঁজতে

---

## General Structure
```sql
SELECT column_name
FROM table_name
WHERE condition
(
    SELECT column_name
    FROM another_table
);

```
---

## How Nested Query Works?

ধরি:
```sql
SELECT Name
FROM Students
WHERE CGPA =
(
    SELECT MAX(CGPA)
    FROM Students
);

```
---

### Step 1

Inner Query execute হবে
```sql
SELECT MAX(CGPA)
FROM Students;

```
---

Result:
```sql
3.95
```
---

### Step 2

Outer Query execute হবে
```sql
SELECT Name
FROM Students
WHERE CGPA = 3.95;

```
---

Output:
```sql
Arafat
```
---

## Terminology

Nested Query সাধারণত ২টি অংশে ভাগ করা হয়।

---

### Outer Query
```sql
SELECT Name
FROM Students
WHERE CGPA =

```
---

### Inner Query
```sql
(
    SELECT MAX(CGPA)
    FROM Students
)

```
---

👉 Inner Query আগে execute হয়।

---

## Example Table: Students

| StudentID | Name | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.90 |
| 102 | Karim | EEE | 3.75 |
| 103 | Sakib | CSE | 3.85 |
| 104 | Nayeem | BBA | 3.60 |
| 105 | Arafat | CSE | 3.95 |

---

## Example 1: Highest CGPA Student
```sql
SELECT Name, CGPA
FROM Students
WHERE CGPA =
(
    SELECT MAX(CGPA)
    FROM Students
);

```
---

### Inner Query Result
```sql
3.95
```
---

### Final Output

| Name | CGPA |
|------|------|
| Arafat | 3.95 |

---

## Example 2: Lowest CGPA Student
```sql
SELECT Name, CGPA
FROM Students
WHERE CGPA =
(
    SELECT MIN(CGPA)
    FROM Students
);

```
---

### Output:

| Name | CGPA |
|------|------|
| Nayeem | 3.60 |

---

## Example 3: Above Average Students
```sql
SELECT Name, CGPA
FROM Students
WHERE CGPA >
(
    SELECT AVG(CGPA)
    FROM Students
);

```
---

### Inner Query
```sql
SELECT AVG(CGPA)
FROM Students;

```
---

Result:
```sql
3.81
```
---

### Output

| Name | CGPA |
|------|------|
| Rahim | 3.90 |
| Sakib | 3.85 |
| Arafat | 3.95 |

---

## Example 4: Below Average Students
```sql
SELECT Name, CGPA
FROM Students
WHERE CGPA <
(
    SELECT AVG(CGPA)
    FROM Students
);

```
---

### Output:

| Name | CGPA |
|------|------|
| Karim | 3.75 |
| Nayeem | 3.60 |

---

## Nested Query with Multiple Tables

---

### Departments Table

| DeptID | DeptName |
|--------|----------|
| 1 | CSE |
| 2 | EEE |
| 3 | BBA |

---

### Students Table

| Name | DeptID |
|------|--------|
| Rahim | 1 |
| Karim | 2 |
| Sakib | 1 |

---

## Example 5

CSE students বের করো।
```sql
SELECT Name
FROM Students
WHERE DeptID =
(
    SELECT DeptID
    FROM Departments
    WHERE DeptName = 'CSE'
);

```
---

### Inner Query Result
```sql
1
```
---

### Outer Query
```sql
SELECT Name
FROM Students
WHERE DeptID = 1;

```
---

### Output:

| Name |
|------|
| Rahim |
| Sakib |

---
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


