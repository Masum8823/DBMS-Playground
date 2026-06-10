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
## Multiple Value Nested Query

যদি Inner Query একাধিক value return করে তাহলে IN ব্যবহার করতে হয়।

---

## Example
```sql
SELECT Name
FROM Students
WHERE DeptID IN
(
    SELECT DeptID
    FROM Departments
);

```
---

### Inner Query Result:
```sql
1
2
3

```
---

### Main Query:
```sql
WHERE DeptID IN (1,2,3)
```
---

## Nested Query with IN

---

## Example
```sql
SELECT *
FROM Students
WHERE Department IN
(
    SELECT Department
    FROM Students
    WHERE CGPA > 3.90
);

```
---

### Inner Query Result:
```sql
CSE
```
---

### Output:

সব CSE students

---
## Nested Query with NOT IN
```sql
SELECT *
FROM Students
WHERE DeptID NOT IN
(
    SELECT DeptID
    FROM Departments
);

```
---

### Output:

Departments table এ নেই এমন students।

---

## Nested Query with EXISTS
```sql
SELECT Name
FROM Students s
WHERE EXISTS
(
    SELECT *
    FROM Departments d
    WHERE s.DeptID = d.DeptID
);

```
---

👉 Matching department থাকলে row return করবে।

---

## Multi-Level Nested Query

একটার ভিতরে আরেকটা, তার ভিতরে আরেকটা Query।

---

## Example
```sql
SELECT Name
FROM Students
WHERE DeptID =
(
    SELECT DeptID
    FROM Departments
    WHERE DeptName =
    (
        SELECT 'CSE'
    )
);

```
---

এখানে:
```sql
Outer Query
   ↓
Inner Query
   ↓
Inner-Inner Query

```
---

👉 এটাকে Multi-Level Nested Query বলে।

---
## Real-Life Example

### Products Table

| Product | Price |
|----------|-------|
| Laptop | 80000 |
| Mouse | 1000 |
| Keyboard | 3000 |
| Monitor | 15000 |

---

## সবচেয়ে expensive product:
```sql
SELECT Product
FROM Products
WHERE Price =
(
    SELECT MAX(Price)
    FROM Products
);

```
---

### Output:
```sql
Laptop
```
---

## Nested Query vs JOIN

---

### Nested Query
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

### JOIN
```sql
SELECT s.Name
FROM Students s
INNER JOIN Departments d
ON s.DeptID = d.DeptID
WHERE d.DeptName = 'CSE';

```
---

দুটোর Output একই।

---

## Nested Query Advantages

### 1. Easy to Read

Complex logic ছোট ছোট অংশে ভাগ করা যায়।

---

### 2. Dynamic Query

Inner Query এর result automatically Main Query তে use হয়।

---

### 3. Powerful Filtering

Complex condition তৈরি করা যায়।

---

## Nested Query Disadvantages

### 1. Large Data এ Slow হতে পারে

বিশেষ করে deeply nested query।

---

### 2. Debugging কঠিন

অনেক level হলে বুঝতে সমস্যা হয়।

---

### 3. JOIN অনেক সময় Faster

Database optimizer JOIN ভালোভাবে handle করতে পারে।

---

## Common Mistakes

---

### Mistake 1

Multiple rows return করলে = ব্যবহার করা

❌
```sql
WHERE DeptID =
(
    SELECT DeptID
    FROM Departments
)

```
---

✔ Correct
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

---

### Q: Nested Query কী?

Query এর ভিতরে Query।

---

### Q: Nested Query এবং Subquery কি একই?

সাধারণ SQL context এ হ্যাঁ, প্রায় একই।

---

### Q: Inner Query আগে execute হয় নাকি Outer Query?

Inner Query আগে execute হয়।

---

### Q: Multiple values return করলে কোন operator ব্যবহার করা হয়?
IN
---

### Q: Nested Query কি SELECT ছাড়া অন্য clause এ ব্যবহার করা যায়?

হ্যাঁ, WHERE, FROM, HAVING ইত্যাদিতেও ব্যবহার করা যায়।

---

## Quick Summary

```sql
Nested Query = Query inside Query

Outer Query = Main Query

Inner Query = Nested Query

Single Value → =

Multiple Values → IN

EXISTS → Check Existence

```
---
</details>  



<details>  
  <summary><b>UNION</b></summary>

# UNION in SQL

UNION ব্যবহার করা হয় দুই বা তার বেশি SELECT query এর result একসাথে combine করার জন্য।

👉 **সহজভাবে:**

Multiple SELECT Results + Merge Together = UNION

---

## Why UNION is Needed?

অনেক সময় data একাধিক table এ থাকে অথবা একই table থেকে ভিন্ন condition এর data একসাথে দেখাতে হয়।

উদাহরণ:

- CSE students + EEE students একসাথে দেখানো
- Current students + Graduated students একসাথে দেখানো
- Dhaka branch + Chittagong branch employees একসাথে দেখানো

এই ধরনের কাজের জন্য UNION ব্যবহার করা হয়।

---

## Basic Syntax
```sql
SELECT column1, column2
FROM Table1

UNION

SELECT column1, column2
FROM Table2;

```
---

## Important Rules of UNION

UNION ব্যবহার করার সময় কিছু নিয়ম অবশ্যই মানতে হবে।

---

### Rule 1: Column সংখ্যা সমান হতে হবে

✔ Correct
```sql
SELECT Name, CGPA
FROM Students

UNION

SELECT Name, CGPA
FROM Graduates;

```
---

❌ Wrong
```sql
SELECT Name, CGPA
FROM Students

UNION

SELECT Name
FROM Graduates;

```
---

কারণ column সংখ্যা match করছে না।

---

### Rule 2: Data Type Compatible হতে হবে

✔ Correct
```sql
Name VARCHAR
UNION
Name VARCHAR

```
---

✔ Also Correct
```sql
INT
UNION
FLOAT

```
---

❌ Wrong
```sql
VARCHAR
UNION
DATE

```
---

(অনেক DBMS এ error দিতে পারে)

---

### Rule 3: Column Names First Query থেকে আসে
```sql
SELECT Name, CGPA
FROM Students

UNION

SELECT StudentName, GPA
FROM Graduates;

```
---

Output Column Names হবে:
```sql
Name
CGPA

```
---

কারণ First SELECT এর column names ব্যবহৃত হয়।

---

## Example Tables

### CurrentStudents

| StudentID | Name |
|------------|------|
| 101 | Rahim |
| 102 | Karim |
| 103 | Sakib |

---

### GraduatedStudents

| StudentID | Name |
|------------|------|
| 104 | Nayeem |
| 105 | Arafat |

---

## Example 1: Basic UNION
```sql
SELECT Name
FROM CurrentStudents

UNION

SELECT Name
FROM GraduatedStudents;

```
---

## Output

| Name |
|------|
| Rahim |
| Karim |
| Sakib |
| Nayeem |
| Arafat |

---

👉 দুই table এর result merge হয়েছে।

---
## Duplicate Handling in UNION

UNION automatically duplicate remove করে।

---

### Example Tables

### Table A

| Name |
|------|
| Rahim |
| Karim |
| Sakib |

---

### Table B

| Name |
|------|
| Sakib |
| Arafat |

---

## Query
```sql
SELECT Name
FROM TableA

UNION

SELECT Name
FROM TableB;

```
---

## Output

| Name |
|------|
| Rahim |
| Karim |
| Sakib |
| Arafat |

---

খেয়াল করুন:
```sql
Sakib
```
---

Sakib একবারই এসেছে।

---
## UNION ALL

UNION ALL duplicate remove করে না।

সব data দেখায়।

---

## Syntax
```sql
SELECT column_name
FROM TableA

UNION ALL

SELECT column_name
FROM TableB;

```
---

## Example
```sql
SELECT Name
FROM TableA

UNION ALL

SELECT Name
FROM TableB;

```
---

## Output

| Name |
|------|
| Rahim |
| Karim |
| Sakib |
| Sakib |
| Arafat |

---

👉 Duplicate রয়ে গেছে।

---

## UNION vs UNION ALL

| Feature | UNION | UNION ALL |
|----------|------|-----------|
| Combine Results | ✅ | ✅ |
| Removes Duplicates | ✅ | ❌ |
| Faster | ❌ | ✅ |
| Keeps All Rows | ❌ | ✅ |

---

## Example 2: Different Conditions

একই table থেকেও UNION ব্যবহার করা যায়।

---

### Students Table

| Name | Department |
|------|------------|
| Rahim | CSE |
| Karim | EEE |
| Sakib | CSE |
| Nayeem | BBA |
```sql
SELECT Name
FROM Students
WHERE Department = 'CSE'

UNION

SELECT Name
FROM Students
WHERE Department = 'EEE';

```
---

---

## Output

| Name |
|------|
| Rahim |
| Sakib |
| Karim |

---

👉 দুই query এর result একসাথে।

---

## Example 3: Multiple Columns
```sql
SELECT Name, Department
FROM Students

UNION

SELECT Name, Department
FROM GraduatedStudents;

```
---

👉 Multiple columns দিয়েও UNION করা যায়।

---
## ORDER BY with UNION

UNION এর শেষে ORDER BY দিতে হয়।

---

### Correct
```sql
SELECT Name
FROM CurrentStudents

UNION

SELECT Name
FROM GraduatedStudents

ORDER BY Name;

```
---

### Wrong
```sql
SELECT Name
FROM CurrentStudents
ORDER BY Name

UNION

SELECT Name
FROM GraduatedStudents;

```
---

❌ Error হবে।

---
## Real-Life Example

### Dhaka Employees

| Name |
|------|
| Rahim |
| Karim |

---

### Chittagong Employees

| Name |
|------|
| Sakib |
| Nayeem |

---

## সব employees একসাথে:
```sql
SELECT Name
FROM DhakaEmployees

UNION

SELECT Name
FROM ChittagongEmployees;

```
---

## Output:
```sql
Rahim
Karim
Sakib
Nayeem

```
---

## UNION with Aggregate Functions
```sql
SELECT COUNT(*) AS Total
FROM CurrentStudents

UNION

SELECT COUNT(*)
FROM GraduatedStudents;

```
---

## Output:

| Total |
|--------|
| 3 |
| 2 |

---

## Common Mistakes

---

### Mistake 1

Column Count Different

❌
```sql
SELECT Name
FROM Students

UNION

SELECT Name, CGPA
FROM Graduates;

```
---

Error হবে।

---

### Mistake 2

Data Type Mismatch

❌
```sql
VARCHAR
UNION
DATE

```
---

সমস্যা হতে পারে।

---

### Mistake 3

UNION এবং JOIN গুলিয়ে ফেলা

---
## UNION

Rows combine করে
```sql
Top
+
Bottom

```
---

## JOIN

Columns combine করে
```sql
Side by Side
```
---

## UNION vs JOIN

| UNION | JOIN |
|------|------|
| Rows combine | Columns combine |
| Same structure দরকার | Relationship দরকার |
| Vertical Merge | Horizontal Merge |

---

## Visual Memory Trick

### UNION
```sql
Table A

Rahim
Karim

+

Table B

Sakib
Nayeem

↓

Rahim
Karim
Sakib
Nayeem

```
---

### JOIN
```sql
Students + Departments

Rahim | CSE
Karim | EEE

```
---

## Common Viva Questions

### Q: UNION কী?

Multiple SELECT query এর result combine করার operator।

---

### Q: UNION duplicate remove করে?

হ্যাঁ।

---

### Q: UNION ALL duplicate remove করে?

না।

---

### Q: UNION এর জন্য column সংখ্যা কি same হতে হবে?

হ্যাঁ।

---

### Q: UNION এবং JOIN এর পার্থক্য কী?

UNION rows combine করে, JOIN columns combine করে।

---

## Quick Summary

```sql
UNION = Combine Results + Remove Duplicates

UNION ALL = Combine Results + Keep Duplicates

UNION = Vertical Merge

JOIN = Horizontal Merge

```
---
</details>  



<details>  
  <summary><b>Views</b></summary>

# Views in SQL

View হলো একটি Virtual Table (ভার্চুয়াল টেবিল)।

এটি আসলে database-এ physically data store করে না, বরং একটি SELECT query store করে রাখে।

👉 **সহজভাবে:**
```sql
View = Saved SELECT Query
```
অথবা,
```sql
View = Virtual Table
```
---

## Why Views Are Needed?

ধরি University Database এ Students table আছে:

| StudentID | Name | Email | Phone | CGPA |
|------------|------|--------|--------|------|
| 101 | Rahim | rahim@gmail.com | 017xxxx | 3.90 |
| 102 | Karim | karim@gmail.com | 018xxxx | 3.75 |

---

এখন Teacher শুধু Name এবং CGPA দেখতে পারবে।

কিন্তু Email এবং Phone দেখতে পারবে না।

প্রতিবার এই Query লিখতে হবে:
```sql
SELECT Name, CGPA
FROM Students;

```
---

এর পরিবর্তে একটি View তৈরি করা যায়।
```sql
CREATE VIEW StudentResultView AS
SELECT Name, CGPA
FROM Students;

```
---

এখন শুধু:
```sql
SELECT *
FROM StudentResultView;

```
---

লিখলেই হবে।

---

## Real-Life Meaning

View অনেকটা shortcut এর মতো।

যেমন:
```sql
Desktop Shortcut
        ↓
Actual Software

```
---

তেমনি,
```sql
View
   ↓
Original Table

```
---

View নিজের data রাখে না।

মূল table থেকেই data নিয়ে আসে।

---

## Syntax

### Creating a View
```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;

```
---

## Example 1: Basic View

### Students Table:

| StudentID | Name | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |
| 102 | Karim | 3.75 |
| 103 | Sakib | 3.85 |

---

### Create View:
```sql
CREATE VIEW StudentView AS
SELECT Name, CGPA
FROM Students;

```
---

### Use View:
```sql
SELECT *
FROM StudentView;

```
---

### Output:

| Name | CGPA |
|------|------|
| Rahim | 3.90 |
| Karim | 3.75 |
| Sakib | 3.85 |

---

## What Happens Internally?

Database View এর Query run করে।
```sql
SELECT *
FROM StudentView;

```
---

Internally:
```sql
SELECT Name, CGPA
FROM Students;

```
---

তাই View কোনো আলাদা data store করে না।

---

## Example 2: View with WHERE

শুধু CSE students দেখাতে চাই।
```sql
CREATE VIEW CSEStudents AS
SELECT *
FROM Students
WHERE Department = 'CSE';

```
 

### Use:
```sql
SELECT *
FROM CSEStudents;

```
---

### Output:

| Name | Department |
|------|------------|
| Rahim | CSE |
| Sakib | CSE |

---

## Example 3: View with JOIN

---

### Students

| StudentID | Name | DeptID |
|------------|------|--------|
| 101 | Rahim | 1 |
| 102 | Karim | 2 |

---

### Departments

| DeptID | DeptName |
|--------|----------|
| 1 | CSE |
| 2 | EEE |

---

### Create View:
```sql
CREATE VIEW StudentDepartmentView AS
SELECT s.Name,
       d.DeptName
FROM Students s
INNER JOIN Departments d
ON s.DeptID = d.DeptID;

```
---

### Use:
```sql
SELECT *
FROM StudentDepartmentView;

```
---

### Output:

| Name | DeptName |
|------|----------|
| Rahim | CSE |
| Karim | EEE |

---

👉 Complex JOIN query বারবার লিখতে হয় না।

---
## Viewing Existing Views

### SQL Server:
```sql
SELECT *
FROM sys.views;

```
---

অথবা:
```sql
SELECT name
FROM sys.views;

```
---
## Updating Data Through View

কিছু View updateable হয়।

---

### Example:
```sql
CREATE VIEW StudentBasicInfo AS
SELECT StudentID,
       Name
FROM Students;

```
---

### Update:
```sql
UPDATE StudentBasicInfo
SET Name = 'Masum'
WHERE StudentID = 101;

```
---

Students table-ও update হয়ে যাবে।

---
## Non-Updatable Views

নিচের ক্ষেত্রে সাধারণত update করা যায় না:

---

### Aggregate Functions
```sql
CREATE VIEW ResultSummary AS
SELECT AVG(CGPA)
FROM Students;

```
---

### GROUP BY
```sql
CREATE VIEW DeptSummary AS
SELECT Department,
       COUNT(*)
FROM Students
GROUP BY Department;

```
---

### DISTINCT
```sql
CREATE VIEW UniqueDepartments AS
SELECT DISTINCT Department
FROM Students;

```
---

### Complex JOINs

অনেক ক্ষেত্রে update করা যায় না।

---
## Altering a View

View modify করার জন্য:
```sql
ALTER VIEW StudentView AS
SELECT Name,
       CGPA,
       Department
FROM Students;

```
---

আগের View overwrite হয়ে যাবে।

---
## Dropping a View

View delete করতে:
```sql
DROP VIEW StudentView;
```
---

👉 শুধু View delete হবে।

মূল table delete হবে না।

---
## View vs Table

| Feature | View | Table |
|----------|------|------|
| Stores Data | ❌ | ✅ |
| Virtual | ✅ | ❌ |
| Physical Storage | ❌ | ✅ |
| Based on Query | ✅ | ❌ |
| Can Be Updated | Sometimes | ✅ |

---
## Advantages of Views

### 1. Security

Sensitive column hide করা যায়।

---

### Example:
```sql
SELECT Name, CGPA
```
---

দেখাবে,

কিন্তু:
```sql
Email
Password
Phone

```
---

দেখাবে না।

---

### 2. Simplicity

Complex query save করা যায়।

---

### 3. Reusability

একবার তৈরি করে বারবার ব্যবহার করা যায়।

---

### 4. Data Abstraction

User কে table structure জানতেই হয় না।

---

## Disadvantages of Views

### 1. Large Query হলে Slow হতে পারে

বিশেষ করে multiple JOIN থাকলে।

---

### 2. Some Views Not Updateable

সব View modify করা যায় না।

---

### 3. Dependency Problem

Original table change হলে View নষ্ট হতে পারে।

---

## Real-Life Example

ধরি University Portal আছে।

---

### Student Table

| StudentID | Name | Email | CGPA |
|------------|------|--------|------|

---

Teacher কে শুধু Result দেখতে দিতে হবে।

---

### Create View:
```sql
CREATE VIEW ResultView AS
SELECT Name, CGPA
FROM Students;

```
---

### Teacher Query:
```sql
SELECT *
FROM ResultView;

```
---

Teacher Email বা Sensitive Info দেখতে পারবে না।

---
## Common Mistakes

### Mistake 1

View কে Table মনে করা

❌
```sql
View stores data
```
---

✔ Correct
```sql
View stores query
```
---

### Mistake 2

DROP VIEW করলে Table delete হবে ভাবা

❌
```sql
Table delete হবে
```
---

✔ Correct
```sql
Only View delete হবে
```
---

### Mistake 3

সব View updateable ভাবা

❌
```sql
All Views can be updated
```
---

✔ অনেক View updateable না।

---
## Common Viva Questions

### Q: View কী?

Virtual Table বা Saved SELECT Query।

---

### Q: View কি data store করে?

না।

---

### Q: View কেন ব্যবহার করা হয়?

Security, simplicity এবং reusability এর জন্য।

---

### Q: View delete করলে Table delete হয়?

না।

---

### Q: View modify করতে কোন command ব্যবহার হয়?
```sql
ALTER VIEW
```
---

### Q: View delete করতে কোন command ব্যবহার হয়?
```sql
DROP VIEW
```
---
## Quick Summary

```sql
View = Virtual Table

View = Saved SELECT Query

CREATE VIEW → Create View

ALTER VIEW → Modify View

DROP VIEW → Delete View

View stores Query
Table stores Data

```
---
</details>  



<details>  
  <summary><b>Indexing</b></summary>

# Indexing in SQL

Index হলো database-এর একটি special data structure, যেটা query execution fast করার জন্য ব্যবহার হয়।

👉 **সহজভাবে:**

Index = Database-এর “Book Index” (সূচিপত্র)

---

## Why Indexing is Important?

Large table এ data খুঁজতে গেলে SQL পুরো table scan করতে পারে (Full Table Scan)।

এটা slow হয়।

Index থাকলে SQL সরাসরি দ্রুত location খুঁজে পায়।

---

### Without Index
```sql
Search → পুরো table scan (slow)
```
---

### With Index
```sql
Search → direct location (fast)
```
---

## Real-Life Example

ধরি একটি Students table আছে:

| StudentID | Name | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |
| 102 | Karim | 3.75 |
| 103 | Sakib | 3.85 |

---

এখন যদি এই query দাও:
```sql
SELECT *
FROM Students
WHERE StudentID = 103;

```
---

👉 Index থাকলে:

Database সরাসরি 103 খুঁজে পাবে

👉 Index না থাকলে:

সব row check করতে হবে

---

## Basic Syntax

### Create Index
```sql
CREATE INDEX index_name
ON table_name (column_name);

```
---
## Example 1: Simple Index
```sql
CREATE INDEX idx_student_name
ON Students(Name);

```
---

👉 এখন Name column search fast হবে।

---

## Example 2: Index on CGPA
```sql
CREATE INDEX idx_cgpa
ON Students(CGPA);

```
---

👉 CGPA based search দ্রুত হবে

---

### Example Query
```sql
SELECT *
FROM Students
WHERE CGPA > 3.80;

```
---

👉 Index থাকলে performance improve হবে

---
## Types of Indexing

---

### 1. Primary Index (Automatically Created)

Primary Key দিলে auto index তৈরি হয়
```sql
StudentID PRIMARY KEY
```
---

👉 Automatically indexed

---

### 2. Unique Index

UNIQUE constraint দিলে index তৈরি হয়
```sql
CREATE UNIQUE INDEX idx_email
ON Students(Email);

```
---

### 3. Clustered Index

👉 Table data physically sorted থাকে index অনুযায়ী

- একটাই clustered index per table
- Usually primary key হয়

---

### 4. Non-Clustered Index

👉 Separate structure তৈরি হয়

👉 Data physically change হয় না

---

## Clustered vs Non-Clustered

| Feature | Clustered | Non-Clustered |
|----------|----------|---------------|
| Data Order | Sorted | Not Sorted |
| Count | 1 per table | Multiple |
| Speed | Faster for range | Fast for lookup |

---

## Example Scenario

### Clustered Index (StudentID)
```sql
101 → 102 → 103 → 104
```
---

### Non-Clustered Index (Name)
```sql
Rahim → pointer → row 101
Karim → pointer → row 102

```
---

### 5. Composite Index

👉 Multiple columns একসাথে index করা

---
```sql
CREATE INDEX idx_name_cgpa
ON Students(Name, CGPA);

```
---

👉 দুই column একসাথে search fast হবে

---

### Example Query
```sql
SELECT *
FROM Students
WHERE Name = 'Rahim'
AND CGPA = 3.90;

```
---

👉 Composite index match করবে

---

### 6. Unique Index

👉 duplicate value allow করে না
```sql
CREATE UNIQUE INDEX idx_student_id
ON Students(StudentID);

```
---

👉 StudentID unique থাকবে

---

### 7. Drop Index

Index delete করতে:
```sql
DROP INDEX idx_student_name;
```
---
👉 Only index delete হবে, table না
---
## How Index Works Internally

Index সাধারণত B-Tree structure ব্যবহার করে।

---

### Without Index
```sql
1 → 2 → 3 → 4 → 5 → full scan
```
---

### With Index
```sql
        3
      /   \
     1     5

```
👉 faster search path

---
## Advantages of Indexing

---

### 1. Fast Search
```sql
SELECT * FROM Students WHERE Name='Rahim';
```
---

### 2. Fast Sorting
```sql
ORDER BY CGPA
```
---

### 3. Faster JOIN
```sql
JOIN on indexed columns
```
---

### 4. Better Performance in Large Data

---

## Disadvantages of Indexing

---

### 1. Extra Storage

Index আলাদা space নেয়

---

### 2. Slow INSERT/UPDATE

কারণ index update করতে হয়
```sql
INSERT → Index update → slower
```
---

### 3. Too Many Index = Bad Performance

---
## When to Use Index?

✔ Large table

✔ Frequently searched column

✔ JOIN column

✔ WHERE condition column

---

## When NOT to Use Index?

❌ Small table

❌ Frequently updated column

❌ Low-selectivity column (e.g. gender)

---
## Real-Life Example

### University System

### Fast Search:
```sql
SELECT *
FROM Students
WHERE StudentID = 101;

```
---

👉 Primary index used

---

### Fast Filter:
```sql
SELECT *
FROM Students
WHERE CGPA > 3.80;

```
---

👉 CGPA index used

---
## Common Mistakes

---

### Mistake 1: Too many indexes

❌ slows down insert/update

---

### Mistake 2: Index on every column

❌ useless

---

### Mistake 3: Small table indexing

❌ no benefit

---
## Viva Questions

---

### Q: Indexing কী?

Database search fast করার technique।

---

### Q: Indexing কেন ব্যবহার করা হয়?

Query performance improve করার জন্য।

---

### Q: Index কি data store করে?

না, শুধু reference রাখে।

---

### Q: Primary key কি automatically indexed?

হ্যাঁ।

---

### Q: Index disadvantage কী?

Storage বেশি লাগে এবং insert/update slow হয়।

---
## Quick Summary

```sql
Index = Speed booster

CREATE INDEX → create index

DROP INDEX → remove index

Clustered → sorted data

Non-clustered → pointer based

Tradeoff = Speed vs Storage

```
---
</details>  



<details>  
  <summary><b>Stored Procedure</b></summary>

# Stored Procedure in SQL

Stored Procedure হলো pre-written SQL code block, যেটা database-এর ভিতরে save করে রাখা হয় এবং পরে বারবার execute করা যায়।

👉 **সহজভাবে:**

Stored Procedure = Saved SQL Program

---

## Why Stored Procedure is Important?

Real-world system এ একই query বারবার ব্যবহার করতে হয়।

উদাহরণ:

- Login check
- Student insert
- Salary update
- Report generate

এইসব বারবার লিখলে time waste হয়। তাই procedure ব্যবহার করা হয়।

---

## Basic Syntax
```sql
CREATE PROCEDURE procedure_name
AS
BEGIN
    SQL statements
END;

```
---

## Example Table: Students

| StudentID | Name | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |
| 102 | Karim | 3.75 |

---
## 1. Simple Stored Procedure

👉 সব students দেখানোর procedure
```sql
CREATE PROCEDURE GetAllStudents
AS
BEGIN
    SELECT * FROM Students;
END;

```
---

### Execute
```sql
EXEC GetAllStudents;
```
---

👉 বারবার SELECT লিখতে হবে না

---
## 2. Stored Procedure with Parameter

👉 specific student খুঁজতে

### Syntax
```sql
CREATE PROCEDURE GetStudentByID
    @StudentID INT
AS
BEGIN
    SELECT *
    FROM Students
    WHERE StudentID = @StudentID;
END;

```
---

### Execute
```sql
EXEC GetStudentByID 101;
```
---

### Output

| StudentID | Name | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |

---
## 3. Multiple Parameters
```sql
CREATE PROCEDURE GetStudentByDeptAndCGPA
    @Dept VARCHAR(20),
    @CGPA FLOAT
AS
BEGIN
    SELECT *
    FROM Students
    WHERE Department = @Dept
    AND CGPA >= @CGPA;
END;

```
---

### Execute
```sql
EXEC GetStudentByDeptAndCGPA 'CSE', 3.80;
```
---
## 4. Insert using Stored Procedure
```sql
CREATE PROCEDURE AddStudent
    @Name VARCHAR(50),
    @CGPA FLOAT
AS
BEGIN
    INSERT INTO Students(Name, CGPA)
    VALUES (@Name, @CGPA);
END;

```
---

### Execute
```sql
EXEC AddStudent 'Sakib', 3.85;
```
---

👉 data automatically insert হবে

---
## 5. Update using Stored Procedure
```sql
CREATE PROCEDURE UpdateCGPA
    @StudentID INT,
    @CGPA FLOAT
AS
BEGIN
    UPDATE Students
    SET CGPA = @CGPA
    WHERE StudentID = @StudentID;
END;

```
---

### Execute
```sql
EXEC UpdateCGPA 101, 4.00;
```
---
## 6. Delete using Stored Procedure
```sql
CREATE PROCEDURE DeleteStudent
    @StudentID INT
AS
BEGIN
    DELETE FROM Students
    WHERE StudentID = @StudentID;
END;

```
---

### Execute
```sql
EXEC DeleteStudent 102;
```
---
## Advantages of Stored Procedure

---

### 1. Faster Execution

👉 compiled code থাকে database এ

---

### 2. Reusability

👉 একবার লিখে বারবার ব্যবহার করা যায়

---

### 3. Security

👉 direct table access না দিয়ে procedure ব্যবহার করা যায়

---

### 4. Less Network Traffic

👉 multiple query একসাথে run হয়

---

### 5. Easy Maintenance

👉 logic এক জায়গায় থাকে

---

## Disadvantages

---

### 1. Debugging Hard

👉 error খুঁজে পাওয়া কঠিন

---

### 2. Database Dependent

👉 এক DBMS থেকে অন্য DBMS এ সহজে move হয় না

---

### 3. Memory Usage

👉 server-side load বাড়ে

---
## Stored Procedure vs Function

| Feature | Stored Procedure | Function |
|----------|------------------|----------|
| Return Value | optional | must return |
| DML allowed | yes | limited |
| Execution | EXEC | SELECT |
| Use | operations | calculations |

---
## Real-Life Example

### University System
```sql
CREATE PROCEDURE GetTopStudents
AS
BEGIN
    SELECT Name, CGPA
    FROM Students
    WHERE CGPA > 3.80;
END;

```
---

### Execute
```sql
EXEC GetTopStudents;
```
---

👉 এক ক্লিকে report তৈরি

---
## Common Mistakes

---

### Mistake 1: EXEC ছাড়া call করা

❌
```sql
GetAllStudents
```
---

✔ Correct:
```sql
EXEC GetAllStudents;
```
---

### Mistake 2: Parameter ভুল order

❌
```sql
EXEC GetStudentByID 'Rahim';
```
---

✔ Correct:
```sql
EXEC GetStudentByID 101;
```
---

### Mistake 3: BEGIN END ভুল

❌ missing block

---
## Viva Questions

---

### Q: Stored Procedure কী?

Pre-written SQL code block যা database এ save থাকে।

---

### Q: কেন ব্যবহার করা হয়?

Reusability এবং performance এর জন্য।

---

### Q: Procedure কিভাবে execute করা হয়?
```sql
EXEC procedure_name;
```
---

### Q: Stored Procedure কি return value দেয়?

Optional।

---

### Q: Function vs Procedure পার্থক্য?

Function must return value, procedure optional।

---## Quick Summary

```sql
Stored Procedure = Saved SQL Code

EXEC → run procedure

Supports parameters

Used for reuse, speed, security

```
---
</details>  



<details>  
  <summary><b>Trigger</b></summary>

# Trigger in SQL

Trigger হলো এমন এক special type of stored program, যেটা automatically execute হয় যখন কোনো event ঘটে (INSERT, UPDATE, DELETE)।

👉 **সহজভাবে:**

Trigger = Automatic Action on Database Event

---

## When Trigger Works?

Trigger automatically run হয় যখন:

- INSERT → নতুন data insert হলে
- UPDATE → data modify হলে
- DELETE → data delete হলে

---

## Basic Idea
```sql
User Action → Trigger Automatically Runs → Extra Work Done
```
---

## Why Trigger is Important?

Real-world system এ অনেক automatic কাজ লাগে:

- Log maintain করা
- Audit system তৈরি করা
- Salary auto update করা
- Stock update করা
- Data validation করা

---

## Basic Syntax
```sql
CREATE TRIGGER trigger_name
ON table_name
AFTER INSERT | UPDATE | DELETE
AS
BEGIN
    SQL statements
END;

```
---

## Example Table: Students

| StudentID | Name | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |
| 102 | Karim | 3.75 |

---
## 1. INSERT Trigger

👉 নতুন student insert হলে log তৈরি হবে

---

### Log Table

| LogID | Message |
|--------|---------|
| 1 | Student added |

---

### Trigger
```sql
CREATE TRIGGER trg_student_insert
ON Students
AFTER INSERT
AS
BEGIN
    INSERT INTO Logs(Message)
    VALUES ('New student inserted');
END;

```
---

### Now Insert Data
```sql
INSERT INTO Students(StudentID, Name, CGPA)
VALUES (103, 'Sakib', 3.85);

```
---

👉 Trigger automatically run হবে

---
## 2. UPDATE Trigger

👉 CGPA change হলে log হবে
```sql
CREATE TRIGGER trg_student_update
ON Students
AFTER UPDATE
AS
BEGIN
    INSERT INTO Logs(Message)
    VALUES ('Student data updated');
END;

```
---

---

### Example
```sql
UPDATE Students
SET CGPA = 4.00
WHERE StudentID = 101;

```
---

👉 Update হলে trigger run হবে automatically

---
## 3. DELETE Trigger

👉 student delete হলে log হবে

---
```sql
CREATE TRIGGER trg_student_delete
ON Students
AFTER DELETE
AS
BEGIN
    INSERT INTO Logs(Message)
    VALUES ('Student deleted');
END;

```
---

### Example
```sql
DELETE FROM Students
WHERE StudentID = 102;

```
---

👉 delete হলে trigger execute হবে

---

## Types of Triggers

---

### 1. AFTER Trigger

👉 event হওয়ার পরে execute হয়
```sql
INSERT → then Trigger runs
```
---

### 2. BEFORE Trigger (MySQL)

👉 event হওয়ার আগে execute হয়
```sql
Trigger → then INSERT/UPDATE/DELETE
```
---

### 3. INSTEAD OF Trigger

👉 event কে replace করে নিজের logic চালায়
```sql
Instead of INSERT → custom logic runs
```
---
## BEFORE Trigger Example (MySQL)
```sql
CREATE TRIGGER trg_before_insert
BEFORE INSERT
ON Students
FOR EACH ROW
BEGIN
    SET NEW.CGPA = 3.00;
END;

```
---

👉 insert হলেও CGPA automatically set হবে

---

## INSTEAD OF Trigger Example
```sql
CREATE TRIGGER trg_instead_of_delete
ON Students
INSTEAD OF DELETE
AS
BEGIN
    INSERT INTO Logs(Message)
    VALUES ('Delete blocked');
END;

```
---

👉 delete হবে না, শুধু log হবে

---
## Trigger with OLD and NEW Values

---

### UPDATE Trigger Example
```sql
CREATE TRIGGER trg_update_log
ON Students
AFTER UPDATE
AS
BEGIN
    INSERT INTO Logs(Message)
    VALUES ('CGPA changed from OLD to NEW');
END;

```
---

👉 advanced tracking করা যায়

---
## Real-Life Example

---

### Banking System
```sql
Withdraw → Balance automatically update
```
---

### Trigger Example
```sql
CREATE TRIGGER trg_balance_update
AFTER UPDATE
ON Accounts
AS
BEGIN
    INSERT INTO Logs(Message)
    VALUES ('Account updated after transaction');
END;

```
---

---

### Stock Management Example
```sql
Product sold → stock automatically decrease
```
---
## Advantages of Trigger

---

### 1. Automatic Execution

👉 manual query লাগেনা

---

### 2. Data Integrity

👉 rules automatically enforce হয়

---

### 3. Audit System

👉 কে কী change করলো track করা যায়

---

### 4. Business Logic Automation

👉 complex logic automatic

---

## Disadvantages of Trigger

---

### 1. Performance Issue

👉 অনেক trigger থাকলে slow হতে পারে

---

### 2. Debugging Hard

👉 hidden execution হয়

---

### 3. Complexity

👉 system বুঝতে কঠিন

---

### 4. Unexpected Behavior

👉 user না জানলেও trigger run হয়

---
## Trigger vs Stored Procedure

| Feature | Trigger | Stored Procedure |
|----------|----------|------------------|
| Execution | Automatic | Manual (EXEC) |
| Called By | Event | User |
| Return Value | No | Optional |
| Use | Auto actions | Manual operations |

---
## Common Mistakes

---

### Mistake 1: Trigger manually run করার চেষ্টা

❌
```sql
EXEC trigger_name;
```
---

✔ Trigger run হয় automatically

---

### Mistake 2: Wrong event type

❌ AFTER INSERT on UPDATE logic

---

### Mistake 3: Infinite loop trigger

❌ Trigger নিজেই আবার trigger call করলে loop হয়

---
## Viva Questions

---

### Q: Trigger কী?

Database event ঘটলে automatically execute হওয়া SQL block।

---

### Q: Trigger কখন execute হয়?

INSERT, UPDATE, DELETE এর পরে বা আগে।

---

### Q: Trigger manually run করা যায়?

না।

---

### Q: Trigger কেন ব্যবহার করা হয়?

Automation, audit, validation এর জন্য।

---

### Q: Trigger vs Procedure?

Trigger automatic, procedure manual।

---
## Quick Summary

```sql
Trigger = Automatic SQL Action

INSERT/UPDATE/DELETE → Trigger runs

Types:
AFTER, BEFORE, INSTEAD OF

Used for automation & auditing

```
---
</details>  



<details>  
  <summary><b>Functions</b></summary>

# Functions in SQL

SQL Function হলো এমন একটি reusable block of code, যেটা input নিয়ে process করে output return করে।

👉 **সহজভাবে:**

Function = Input → Process → Output

---

## Why SQL Functions Are Used?

Real database এ বারবার একই ধরনের কাজ করতে হয়:

- CGPA calculation
- Age calculation
- Salary calculation
- Text formatting
- Data aggregation

👉 এগুলো বারবার লিখলে time waste হয়, তাই function ব্যবহার করা হয়।

---
## Types of SQL Functions

SQL Functions সাধারণত 2 ভাগে ভাগ করা হয়:

---

# 1. Built-in Functions (Predefined)

DBMS আগে থেকেই দেয়।

---

## (A) Aggregate Functions

Multiple rows নিয়ে single result দেয়।

---

### 1. COUNT()
```sql
SELECT COUNT(*) FROM Students;
```
---

👉 total students count করবে

---

### 2. SUM()
```sql
SELECT SUM(CGPA) FROM Students;
```
---

👉 সব CGPA যোগ করবে

---

### 3. AVG()
```sql
SELECT AVG(CGPA) FROM Students;
```
---

👉 average CGPA দিবে

---

### 4. MAX()
```sql
SELECT MAX(CGPA) FROM Students;
```
---

👉 highest CGPA

---

### 5. MIN()
```sql
SELECT MIN(CGPA) FROM Students;
```
---

👉 lowest CGPA

---

## Example Table

| Name | CGPA |
|------|------|
| Rahim | 3.90 |
| Karim | 3.75 |
| Sakib | 3.85 |

---

## Output Example
```sql
AVG(CGPA) = 3.83
MAX(CGPA) = 3.90
MIN(CGPA) = 3.75

```
---
## (B) Scalar Functions

Single value নিয়ে কাজ করে।

---

### 1. UPPER()
```sql
SELECT UPPER(Name)
FROM Students;

```
---

👉 সব name capital letter এ convert করবে

---

### 2. LOWER()
```sql
SELECT LOWER(Name)
FROM Students;

```
---

👉 সব name small letter

---

### 3. LENGTH()
```sql
SELECT LENGTH(Name)
FROM Students;

```
---

👉 name এর length বের করবে

---

### 4. ROUND()
```sql
SELECT ROUND(3.678, 2);
```
---

👉 output = 3.68

---

### 5. NOW()
```sql
SELECT NOW();
```
---

👉 current date & time দিবে

---

### 6. CONCAT()
```sql
SELECT CONCAT(Name, ' - CSE')
FROM Students;

```
---

👉 text join করবে

---
# 2. User-Defined Functions (UDF)

👉 Programmer নিজে function তৈরি করে

---

## Syntax (MySQL style)
```sql
CREATE FUNCTION function_name(parameters)
RETURNS datatype
DETERMINISTIC
BEGIN
    RETURN value;
END;

```
---

## Example 1: Age Calculation Function
```sql
CREATE FUNCTION GetAge(birth_year INT)
RETURNS INT
DETERMINISTIC
BEGIN
    RETURN 2026 - birth_year;
END;

```
---

### Use:
```sql
SELECT GetAge(2003);
```
---

### Output:
```sql
23
```
---

---

## Example 2: CGPA Status Function
```sql
CREATE FUNCTION GetStatus(cgpa FLOAT)
RETURNS VARCHAR(20)
DETERMINISTIC
BEGIN
    IF cgpa >= 3.80 THEN
        RETURN 'Excellent';
    ELSEIF cgpa >= 3.50 THEN
        RETURN 'Good';
    ELSE
        RETURN 'Average';
    END IF;
END;

```
---

### Use:
```sql
SELECT Name, CGPA, GetStatus(CGPA)
FROM Students;

```
---

### Output:

| Name | CGPA | Status |
|------|------|--------|
| Rahim | 3.90 | Excellent |
| Karim | 3.75 | Good |

---

## Example 3: Salary Bonus Function
```sql
CREATE FUNCTION GetBonus(salary INT)
RETURNS INT
DETERMINISTIC
BEGIN
    RETURN salary * 0.10;
END;

```
---

### Use:
```sql
SELECT GetBonus(50000);
```
---

### Output:
```sql
5000
```
---
## Aggregate vs Scalar vs User Function

| Type | Input | Output | Example |
|------|------|--------|---------|
| Aggregate | Multiple rows | Single value | AVG(), SUM() |
| Scalar | Single row | Single value | UPPER(), ROUND() |
| User-defined | Custom input | Custom output | GetAge() |

---

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


