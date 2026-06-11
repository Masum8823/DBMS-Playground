<h1 align="center">Database Design</h1>

> ### Explore each topic to understand the core concepts in detail
<p align="center">
  ⬇<b> Click any section below to expand </b> ⬇
</p>

---

<details>
    <summary><b>Normalization</b></summary>

# Normalization in DBMS

Normalization হলো database design করার একটা systematic process, যেখানে বড় এবং messy table কে ছোট ছোট logical table এ ভাগ করা হয় যাতে:
•	redundancy কমে 
•	inconsistency দূর হয় 
•	data integrity improve হয় 

👉 সহজভাবে:
```sql
Normalization = Large messy table → Clean structured tables
```
________________________________________

## Why Normalization is So Important?

Unnormalized database এ নিচের সমস্যা হয়:
________________________________________

## 1. Data Redundancy (Duplicate data)

একই data বারবার store হয়।
________________________________________

## 2. Update Anomaly

এক জায়গায় update করলেও অন্য জায়গায় change না হতে পারে।
________________________________________

## 3. Insert Anomaly

নতুন data insert করতে গেলে unnecessary data দিতে হয়।
________________________________________

## 4. Delete Anomaly

একটা row delete করলে গুরুত্বপূর্ণ info হারিয়ে যেতে পারে।
________________________________________

---
## Example (Before Normalization)

| StudentID | Name  | Dept | DeptHead | Course | Teacher |
|------------|------|------|----------|--------|----------|
| 101 | Rahim | CSE | Mr. X | DBMS | Mr. A |
| 101 | Rahim | CSE | Mr. X | AI | Mr. B |
| 102 | Karim | EEE | Mr. Y | Circuit | Mr. C |
________________________________________

## Problems:

•	Rahim repeated multiple times 
•	DeptHead repeated 
•	Course and Teacher repeated 
•	update difficult 
---
## Normalization Levels

```sql
1NF → 2NF → 3NF → BCNF
```

Each level previous level এর উপর build হয়।
________________________________________

## 1NF (First Normal Form) – Deep
________________________________________

## Rule of 1NF

✔ Each column must contain atomic value  
✔ No repeating groups  
✔ Each row must be unique  
________________________________________

## Problem Table (Not 1NF)

| StudentID | Name  | Subjects |
|------------|------|----------|
| 101 | Rahim | DBMS, AI |
| 102 | Karim | Math, Physics |
________________________________________

## Problem:

👉 multiple values in one cell  
________________________________________

## Convert to 1NF

| StudentID | Name  | Subject |
|------------|------|---------|
| 101 | Rahim | DBMS |
| 101 | Rahim | AI |
| 102 | Karim | Math |
| 102 | Karim | Physics |
________________________________________

## Key Idea:

```sql
1NF = Atomic columns only
```
---

## 2NF (Second Normal Form) – Deep
________________________________________

## Rule of 2NF

✔ Must be in 1NF  
✔ No partial dependency  
________________________________________

## What is Partial Dependency?

👉 যখন composite key এর part এর উপর non-key attribute depend করে  
________________________________________

## Example (1NF but not 2NF)

| StudentID | Course | StudentName |
|------------|--------|-------------|
| 101 | DBMS | Rahim |
| 101 | AI | Rahim |
________________________________________

## Functional Dependency:
```sql
StudentID → StudentName
Course → (nothing)
(StudentID, Course) → record

```
________________________________________

## Problem:

👉 StudentName depends only on StudentID (partial dependency)
________________________________________

## Solution (2NF Decomposition)

## Students Table

| StudentID | StudentName |
|------------|-------------|
| 101 | Rahim |
| 102 | Karim |

## Enrollment Table

| StudentID | Course |
|------------|--------|
| 101 | DBMS |
| 101 | AI |
________________________________________

## Key Idea:
```sql
2NF = Remove partial dependency
```
---
## 3NF (Third Normal Form) – Deep
________________________________________

## Rule of 3NF

✔ Must be in 2NF  
✔ No transitive dependency  
________________________________________

## What is Transitive Dependency?
```sql
A → B → C
A indirectly determines C

```
________________________________________

## Example (Not 3NF)

| StudentID | Dept | DeptHead |
|------------|------|----------|
| 101 | CSE | Mr. X |
| 102 | CSE | Mr. X |
________________________________________

## Dependency:
```sql
StudentID → Dept → DeptHead
```
________________________________________

## Problem:

👉 DeptHead depends on Dept, not StudentID  
________________________________________

## Solution (3NF Decomposition)

## Students Table

| StudentID | Dept |
|------------|------|
| 101 | CSE |
| 102 | CSE |

## Department Table

| Dept | DeptHead |
|------|----------|
| CSE | Mr. X |
________________________________________

## Key Idea:
```sql
3NF = Remove transitive dependency
```
________________________________________

## BCNF (Boyce-Codd Normal Form) – Deep
________________________________________

## Rule of BCNF

✔ Must be in 3NF  
✔ Every determinant must be a candidate key  
________________________________________

## What is Determinant?

👉 যেটা অন্য attribute কে determine করে  
________________________________________

## Example (3NF but NOT BCNF)

| Student | Course | Teacher |
|----------|--------|----------|
| A | DBMS | Mr. X |
| B | DBMS | Mr. X |
| A | AI | Mr. Y |
________________________________________

## Functional Dependency:
```sql
Course → Teacher
Student + Course → Record

```
________________________________________

## Problem:

👉 Course is not a candidate key but determines Teacher  
________________________________________

## Solution (BCNF Decomposition)

## Course Table

| Course | Teacher |
|--------|----------|
| DBMS | Mr. X |
| AI | Mr. Y |

## Enrollment Table

| Student | Course |
|----------|--------|
| A | DBMS |
| B | DBMS |
________________________________________

## Key Idea:
```sql
BCNF = Strongest normalization rule
Every determinant must be a key

```

---

## Full Comparison (Deep View)

| Normal Form | Problem Solved | Rule |
|-------------|---------------|------|
| 1NF | Repeating groups | Atomic values |
| 2NF | Partial dependency | Full dependency on key |
| 3NF | Transitive dependency | No indirect dependency |
| BCNF | Functional anomaly | Determinant must be key |
________________________________________

## Real-Life University Example
________________________________________

## Before Normalization
```sql
Student + Dept + DeptHead + Course + Teacher (all mixed)
```
________________________________________

## After Full Normalization

## Students

| StudentID | Name | Dept |

## Departments

| Dept | DeptHead |

## Courses

| Course | Teacher |

## Enrollment

| StudentID | Course |

👉 clean, scalable design
________________________________________
## Advantages (Deep Understanding)

________________________________________

## 1. No redundancy

👉 storage save  
________________________________________

## 2. No update anomaly

👉 one place update enough  
________________________________________

## 3. Better consistency

👉 no conflicting data  
________________________________________

## 4. Scalable design

👉 large system easy handle  
________________________________________

## Disadvantages (Important Exam Point)

________________________________________

## 1. More tables

👉 complexity increase  
________________________________________

## 2. More JOIN needed

👉 query becomes heavy  
________________________________________

## 3. Slight performance cost

👉 read slow sometimes  
________________________________________

## When NOT to Normalize Fully?

👉 Sometimes denormalization is used when:
• reporting system  
• analytics  
• performance critical read system  
________________________________________

## Denormalization (Opposite Idea)
```sql
Normalization → split tables
Denormalization → merge tables

```
---
## Easy Memory Trick
```sql
1NF → Make atomic
2NF → Remove partial dependency
3NF → Remove indirect dependency
BCNF → Make everything key-based

```
________________________________________

</details>


<details>
    <summary><b>Functional Dependency</b></summary>


---
</details>


<details>
    <summary><b>Decomposition</b></summary>


---
</details>


<details>
    <summary><b>Database Design Process</b></summary>


---
</details>


<details>
    <summary><b>ER to Relational Model Conversion</b></summary>


---
</details>



