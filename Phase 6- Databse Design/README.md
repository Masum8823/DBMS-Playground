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

## Viva Ready Questions

________________________________________

## Q: Normalization কেন করা হয়?

Redundancy কমাতে এবং data consistency বাড়াতে।

________________________________________

## Q: 1NF কী?

Atomic values only, no repeating groups।

________________________________________

## Q: 2NF কী?

No partial dependency।

________________________________________

## Q: 3NF কী?

No transitive dependency।

________________________________________

## Q: BCNF কী?

Every determinant must be a candidate key।

________________________________________

## Q: Normalization এর disadvantage কী?

More tables and more JOIN required।

________________________________________
## Quick Summary
```sql
Normalization = Clean database design

1NF → atomic values
2NF → remove partial dependency
3NF → remove transitive dependency
BCNF → strongest rule (key-based design)

```
---
</details>


<details>
    <summary><b>Functional Dependency</b></summary>

# Functional Dependency (FD) in DBMS

Functional Dependency হলো এমন একটি relationship, যেখানে একটি attribute (বা attribute set) অন্য attribute কে uniquely determine করে।

👉 সহজভাবে:
A → B  মানে A জানলে B uniquely জানা যায়

________________________________________

## Real-Life Example

| StudentID | Name  | Dept |
|-----------|------|------|
| 101 | Rahim | CSE |
| 102 | Karim | EEE |

________________________________________

👉 এখানে:
```sql
StudentID → Name
StudentID → Dept

```
কারণ StudentID জানা থাকলে Name এবং Dept uniquely পাওয়া যায়।

________________________________________

## Formal Definition

Functional Dependency বলতে বোঝায়:

যদি X attribute set Y attribute set কে uniquely determine করে, তাহলে বলা হয় X → Y

________________________________________
## Types of Functional Dependency

________________________________________

## 1. Trivial Functional Dependency

👉 যখন RHS (right side) LHS এর subset হয়

Example:

 ```sql
(A, B) → A
(A, B) → B

```

👉 এটা always true

________________________________________

## 2. Non-Trivial Functional Dependency

👉 যখন RHS, LHS এর subset না হয়

Example:

 ```sql
StudentID → Name
```

👉 meaningful dependency

________________________________________

## 3. Completely Non-Trivial FD

👉 যখন RHS এবং LHS completely different

Example:
```sql
StudentID → Dept
```
 ---

 ## Types Based on Dependency Strength

________________________________________

## 4. Full Functional Dependency

👉 যখন attribute পুরো key এর উপর depend করে

Example:

| StudentID | Course | Grade |

```sql
(StudentID, Course) → Grade
```
 

👉 Grade depends on full composite key

________________________________________

## 5. Partial Dependency

👉 যখন attribute composite key এর part এর উপর depend করে

Example:

 ```sql
(StudentID, Course) → StudentName
```

👉 StudentName depends only on StudentID

________________________________________

## Problem:

👉 2NF violation

________________________________________

## 6. Transitive Dependency

👉 indirect dependency

Example:
```sql
StudentID → Dept → DeptHead
```
 

👉 StudentID indirectly determines DeptHead
---

## Functional Dependency Diagram Concept

 ```sql
A → B → C
```

👉 A indirectly determines C

________________________________________

## Key Terms

________________________________________

## 1. Determinant

👉 যেটা অন্য attribute কে determine করে

 
```sql
StudentID → Name
StudentID = Determinant

```
________________________________________

## 2. Dependent Attribute

👉 যেটা depend করে

 ```sql
Name depends on StudentID
```

---
## Importance of Functional Dependency

________________________________________

## 1. Helps in Normalization

👉 1NF, 2NF, 3NF, BCNF FD এর উপর based

________________________________________

## 2. Reduces Redundancy

________________________________________

## 3. Improves Database Design

________________________________________

## 4. Ensures Data Integrity

________________________________________
## Example (Complex Table)

| StudentID | Course | Instructor | Dept | DeptHead |

________________________________________

## Functional Dependencies:

 ```sql
StudentID → Dept
Dept → DeptHead
Course → Instructor
(StudentID, Course) → Grade

```

________________________________________

👉 এই dependencies বুঝলেই normalization করা সহজ

________________________________________

## Closure of Functional Dependency (Important Concept)

👉 attribute set দিয়ে কতগুলো attribute determine করা যায়

Example:
```sql
A → B
B → C

```
 

👉 তাহলে:

 ```sql
A+ = {A, B, C}
```

________________________________________

## Armstrong’s Axioms (Rules of FD)

________________________________________

## 1. Reflexivity

 ```sql
If Y ⊆ X then X → Y
```

________________________________________

## 2. Augmentation

 ```sql
If X → Y then XZ → YZ
```

________________________________________

## 3. Transitivity

 ```sql
If X → Y and Y → Z then X → Z
```

________________________________________

## Derived Rules

________________________________________

## Union Rule

 ```sql
X → Y and X → Z ⇒ X → YZ
```

________________________________________

## Decomposition Rule

 
```sql
X → YZ ⇒ X → Y and X → Z
```
________________________________________

## Pseudotransitivity

 
```sql
X → Y and WY → Z ⇒ WX → Z
```
________________________________________

## Functional Dependency vs Normalization

| Concept | Role |
|----------|------|
| FD | Relationship between attributes |
| Normalization | Uses FD to design tables |

________________________________________

## Real-Life Analogy

 ```sql
StudentID → Name
Like:
Roll number → Student info

```

👉 Roll number জানলে সব info পাওয়া যায়

________________________________________

## Common Mistakes

________________________________________

## Mistake 1: One-to-one thinking

❌ সব dependency symmetric ভাবে ভাবা

________________________________________

## Mistake 2: Missing composite key dependency

________________________________________

## Mistake 3: Confusing FD with foreign key

________________________________________

## Viva Questions

________________________________________

## Q: Functional Dependency কী?

Attribute relationship where one attribute determines another.

________________________________________

## Q: Determinant কী?

Left side of FD.

________________________________________

## Q: Full FD কী?

Attribute depends on full composite key.

________________________________________

## Q: Partial dependency কী?

Depends on part of composite key.

________________________________________

## Q: Transitive dependency কী?

Indirect dependency (A → B → C).

________________________________________

## Quick Summary

```sql
Functional Dependency = Attribute relationship

A → B = A determines B

Types:
- Trivial
- Non-trivial
- Full
- Partial
- Transitive

Used in normalization

```
---


</details>


<details>
    <summary><b>Decomposition</b></summary>

# Decomposition in DBMS

Decomposition হলো একটি process যেখানে বড় table কে ছোট ছোট related tables এ ভাগ করা হয় যাতে redundancy কমে এবং data consistency maintain থাকে।

👉 সহজভাবে:
 ```sql
Decomposition = Big table → Multiple small tables
```
________________________________________

## Why Decomposition is Needed?

Large table এ অনেক সমস্যা থাকে:

•	Data redundancy (duplicate data)  
•	Update anomaly  
•	Insert anomaly  
•	Delete anomaly  
•	Data inconsistency  

👉 এসব সমস্যা solve করার জন্য table ভাঙা হয়।

________________________________________

## Example (Before Decomposition)

| StudentID | Name  | Dept | DeptHead | Course | Teacher |
|------------|------|------|----------|--------|----------|
| 101 | Rahim | CSE | Mr. X | DBMS | Mr. A |
| 101 | Rahim | CSE | Mr. X | AI | Mr. B |
| 102 | Karim | EEE | Mr. Y | Circuit | Mr. C |

________________________________________

## Problems:

•	Rahim repeat  
•	DeptHead repeat  
•	Course–Teacher repeat  
•	update multiple place required  

________________________________________

## Goal of Decomposition

 ```sql
Reduce redundancy
Remove anomalies
Improve consistency
Better structure

```
________________________________________

## Types of Decomposition

________________________________________

## 1. Lossless Decomposition (VERY IMPORTANT)

👉 Decomposition এমনভাবে করা হয় যাতে আবার tables join করলে original table ফিরে পাওয়া যায়।

 ```sql
Split → Join → Original data must come back
```
________________________________________

## Example:

Original Table → split into:

•	Students(StudentID, Name, Dept)  
•	Departments(Dept, DeptHead)  

👉 JOIN করলে original data ফিরে আসে

________________________________________

## Condition for Lossless Decomposition

 ```sql
Common attribute must be key in at least one table
```
________________________________________
## 2. Lossy Decomposition (BAD CASE)

👉 যখন decomposition করলে original table fully recover করা যায় না

 ```sql
Data loss or extra fake tuples appear
```
________________________________________

## Problem Example:

Wrong split করলে:

•	duplicate rows তৈরি হতে পারে  
•	wrong join result  

________________________________________
## 3. Dependency Preserving Decomposition

👉 যদি original functional dependencies preserve থাকে

 ```sql
All FD should still work after decomposition
```
________________________________________
## Example of Good Decomposition

________________________________________

## Original Table

| StudentID | Name | Dept | DeptHead |

________________________________________

## Functional Dependencies:

 ```sql
StudentID → Name, Dept
Dept → DeptHead

```
________________________________________

## Decomposed Tables

## Students Table

| StudentID | Name | Dept |

________________________________________

## Department Table

| Dept | DeptHead |

________________________________________

👉 Now redundancy removed

________________________________________
## Steps of Decomposition

________________________________________

## Step 1: Identify Functional Dependencies
```sql
A → B, B → C etc.
```
 
________________________________________

## Step 2: Find anomalies

•	redundancy  
•	dependency issues  

________________________________________

## Step 3: Split table

Based on FD rules

________________________________________

## Step 4: Check Lossless Join

Ensure no data loss after join

________________________________________

## Step 5: Check Dependency Preservation

Ensure FD still valid

________________________________________
## Lossless Join Condition (Important)

For decomposition R → R1, R2:
```sql
(R1 ∩ R2) → R1 OR (R1 ∩ R2) → R2
```
 
👉 intersection must be a key

________________________________________

## Example (Lossless)

________________________________________

## Table

R(A, B, C)

Functional Dependency:

 ```sql
A → B
```
________________________________________

## Decomposition:

•	R1(A, B)  
•	R2(A, C)  

________________________________________

## Intersection = A

👉 A is key of R1  
✔ Lossless decomposition

________________________________________

## Example (Lossy)

If wrong split:

•	R1(B, C)  
•	R2(A, B)  

👉 No proper key in intersection  
❌ lossy decomposition

________________________________________
## Decomposition vs Normalization

| Feature | Decomposition | Normalization |
|----------|--------------|---------------|
| Process | Splitting tables | Rule-based design |
| Goal | Remove redundancy | Organize database |
| Based on | Functional Dependency | Normal Forms |

________________________________________
## Real-Life Example

________________________________________

## Before

 ```sql
Student + Dept + Course + Teacher (all in one table)
```
________________________________________

## After Decomposition

## Students

| StudentID | Name | Dept |
|-----------|------|-------|
________________________________________

## Departments

| Dept | DeptHead |
|-------|---------|
________________________________________

## Courses

| Course | Teacher |
|---------|------|
________________________________________

## Enrollment

| StudentID | Course |
|-----------|--------|

👉 Clean and scalable design

________________________________________
## Advantages of Decomposition

________________________________________

## 1. Removes redundancy

________________________________________

## 2. Improves consistency

________________________________________

## 3. Easier maintenance

________________________________________

## 4. Better storage efficiency

________________________________________

## 5. Supports normalization

________________________________________

## Disadvantages of Decomposition

________________________________________

## 1. More tables

________________________________________

## 2. Complex joins needed

________________________________________

## 3. Query overhead increases

________________________________________
## Common Mistakes

________________________________________

## Mistake 1: Losing data (lossy decomposition)

________________________________________

## Mistake 2: Ignoring functional dependency

________________________________________

## Mistake 3: Wrong table splitting

________________________________________
## Viva Questions

________________________________________

## Q: Decomposition কী?

Big table কে small tables এ ভাগ করা।

________________________________________

## Q: Lossless decomposition কী?

Original data join করে ফিরে পাওয়া যায়।

________________________________________

## Q: Lossy decomposition কী?

Data loss হয় বা incorrect result আসে।

________________________________________

## Q: Dependency preserving কী?

All functional dependencies preserved থাকে।

________________________________________

## Q: কেন decomposition করা হয়?

Redundancy কমাতে এবং anomalies দূর করতে।

________________________________________
## Quick Summary
```sql
Decomposition = Table splitting

Types:
- Lossless (GOOD)
- Lossy (BAD)
- Dependency Preserving

Goal: Clean & efficient database design

```
---
</details>


<details>
    <summary><b>Database Design Process</b></summary>

# Database Design Process

Database Design Process হলো একটি step-by-step method, যার মাধ্যমে raw requirements থেকে একটি efficient, consistent এবং well-structured database তৈরি করা হয়।

👉 সহজভাবে:
 ```sql
Requirements → Conceptual Design → Logical Design → Physical Design → Database
```
________________________________________

## Why Database Design is Important?

ভালো design না করলে database এ সমস্যা হয়:

•	Data redundancy  
•	Inconsistency  
•	Poor performance  
•	Difficult maintenance  
•	Data anomalies  

👉 তাই proper design খুব গুরুত্বপূর্ণ।

________________________________________
## Main Phases of Database Design

Database design সাধারণত 4টি main phase এ করা হয়:

________________________________________

## 1. Requirement Collection & Analysis

এখানে বোঝা হয়:

•	কি data store করতে হবে  
•	user কীভাবে data ব্যবহার করবে  
•	business rules কী  

________________________________________

## Example (University System)

Requirements:

•	Students info store করতে হবে  
•	Courses and teachers track করতে হবে  
•	Enrollment system দরকার  

________________________________________

## Output:
```sql
List of requirements + constraints
```
 
________________________________________
## 2. Conceptual Design (ER Modeling)

এই phase এ high-level design করা হয় using ER Diagram।

________________________________________

## ER Diagram includes:

•	Entities (Student, Course)  
•	Attributes (Name, ID)  
•	Relationships (Enrolls)  

________________________________________

## Example:

 ```sql
Student → enrolls → Course
```
________________________________________

## Output:

👉 ER Diagram (database blueprint)

________________________________________
## 3. Logical Design (Relational Model)

এই stage এ ER Diagram কে table structure এ convert করা হয়।

________________________________________

## Example:

## Student Table

| StudentID | Name | Dept |

________________________________________

## Course Table

| CourseID | CourseName |

________________________________________

## Enrollment Table

| StudentID | CourseID |

________________________________________

👉 এখন database relational form এ চলে আসে

________________________________________

## Important Step: Normalization (Inside Logical Design)

Logical design এর সময় normalization করা হয়:

 ```sql
1NF → 2NF → 3NF → BCNF
```
👉 redundancy remove করা হয়

________________________________________
## 4. Physical Design

এখানে actual database storage structure তৈরি করা হয়।

________________________________________

## Includes:

•	File organization  
•	Indexing  
•	Storage method  
•	Performance optimization  

________________________________________

## Example:

 ```sql
CREATE INDEX idx_student ON Student(StudentID);
```
________________________________________

👉 database fast কাজ করে

________________________________________
## Full Database Design Flow
```sql
Requirements
     ↓
Conceptual Design (ER Diagram)
     ↓
Logical Design (Tables + Normalization)
     ↓
Physical Design (Indexes + Storage)
     ↓
Final Database

```
 
________________________________________
## Real-Life Example (University System)

________________________________________

## Step 1: Requirement

•	Students register for courses  
•	Teachers teach courses  
•	Departments manage students  

________________________________________

## Step 2: Conceptual Design
```sql
Student → Enrolls → Course → Taught by → Teacher
```
 
________________________________________

## Step 3: Logical Design

Tables:

•	Students(StudentID, Name, Dept)  
•	Courses(CourseID, Title)  
•	Teachers(TeacherID, Name)  
•	Enrollment(StudentID, CourseID)  

________________________________________

## Step 4: Physical Design

•	Index on StudentID  
•	Index on CourseID  
•	Optimized queries  

________________________________________
## Schema Design Types

________________________________________

## 1. Star Schema (Data Warehouse)

•	Central fact table  
•	Dimension tables around it  

________________________________________

## 2. Snowflake Schema

•	Normalized star schema  
•	More tables  

________________________________________
## Database Design Approaches

________________________________________

## 1. Top-Down Approach

👉 Start from ER diagram → tables

 ```sql
Conceptual → Logical → Physical
```
________________________________________

## 2. Bottom-Up Approach

👉 Start from existing tables → structure design

________________________________________
## Keys in Design Process

•	Primary Key → uniqueness  
•	Foreign Key → relationships  
•	Candidate Key → possible keys  

________________________________________

## Importance of Normalization in Design

👉 Logical design এর সময় normalization না করলে:

•	duplicate data  
•	update anomaly  
•	inconsistency  

________________________________________
## Advantages of Good Database Design

________________________________________

## 1. Efficient storage

________________________________________

## 2. Fast query performance

________________________________________

## 3. Easy maintenance

________________________________________

## 4. Data consistency

________________________________________

## 5. Scalability

________________________________________

## Disadvantages of Poor Design

________________________________________

## 1. Data redundancy

________________________________________

## 2. Slow queries

________________________________________

## 3. Hard to maintain

________________________________________

## 4. Data anomalies

________________________________________
## Common Mistakes

________________________________________

## Mistake 1: Skipping requirement analysis

________________________________________

## Mistake 2: No ER diagram

________________________________________

## Mistake 3: No normalization

________________________________________

## Mistake 4: Direct table creation without planning

________________________________________
## Viva Questions

________________________________________

## Q: Database design process কী?

Step-by-step method to design a database from requirements.

________________________________________

## Q: Phases of database design?

Requirement → Conceptual → Logical → Physical

________________________________________

## Q: ER diagram কোন phase এ আসে?

Conceptual design phase

________________________________________

## Q: Normalization কোন phase এ হয়?

Logical design phase

________________________________________

## Q: Physical design কী?

Storage and performance optimization stage

________________________________________
## Quick Summary
```sql
Database Design Process:

Requirements
→ ER Diagram
→ Tables + Normalization
→ Index + Storage

Goal: Efficient, scalable database

```
---
</details>


<details>
    <summary><b>ER to Relational Model Conversion</b></summary>

# ER to Relational Model Conversion

ER to Relational mapping হলো এমন একটা process যেখানে ER Diagram এর conceptual structure কে relational database (tables) এ convert করা হয়।

👉 সহজভাবে:
 ```sql
ER Diagram (Conceptual) → Relational Schema (Tables)
```
________________________________________

## Why This Step is Important?

ER diagram বাস্তবে database না, এটা শুধু design।

Database engine কাজ করে table-based structure এ, তাই conversion দরকার।

________________________________________

## Complete Mapping Strategy

ER model এর সব parts আলাদা rules দিয়ে convert হয়:

•	Entity → Table  
•	Attribute → Column  
•	Relationship → FK / New Table  
•	Constraints → Keys / Rules  

________________________________________

## 1. Strong Entity Set → Table (DETAILED)

Strong entity হলো যার নিজস্ব primary key আছে।

________________________________________

## Example ER:

Student(StudentID, Name, Age, Dept)

________________________________________

## Relational Table:

| StudentID (PK) | Name | Age | Dept |

________________________________________

## Rule:

 ```sql
Each strong entity → separate table
Primary key → 그대로 primary key
Simple attributes → columns

```
________________________________________

## Important Notes:

•	Composite attributes (Name = First + Last) → split columns  
•	Derived attributes → NOT stored  

________________________________________

## 2. Weak Entity Set → Table (DETAILED)

Weak entity নিজে uniquely identified হতে পারে না।

________________________________________

## Example ER:

Employee(EmpID)  
Dependent(Name, Age)

________________________________________

## Dependency:

Dependent depends on Employee

________________________________________

## Relational Table:

## Employee

| EmpID (PK) | Name |

________________________________________

## Dependent

| EmpID (FK) | DependentName | Age |

________________________________________

## Primary Key:

 ```sql
PK = (EmpID + DependentName)
```
________________________________________

## Rule:
```sql
Weak entity → PK = Partial Key + Owner PK
Owner key → foreign key

```
 
________________________________________
## 3. 1:1 Relationship (DETAILED)

________________________________________

## Example:

Person ↔ Passport

________________________________________

## Rule Options:

### Option 1: Merge Tables (Best choice)

| PersonID | Name | PassportNo |

________________________________________

### Option 2: Foreign Key in one table

## Person:

| PersonID | Name | PassportNo (FK) |

________________________________________

## Decision Rule:

 ```sql
FK goes to either side OR merge if total participation
```
________________________________________
## 4. 1:M Relationship (DETAILED)

________________________________________

## Example:

Department → Students  
(one department, many students)

________________________________________

## Rule:

👉 FK always goes to MANY side

________________________________________

## Tables:

## Department

| DeptID (PK) | DeptName |

________________________________________

## Student

| StudentID (PK) | Name | DeptID (FK) |

________________________________________

## Explanation:

 ```sql
One Dept → Many Students
So Students table stores DeptID

```
________________________________________

## Important Constraint:

•	DeptID in Student must exist in Department (referential integrity)

________________________________________
## 5. M:N Relationship (VERY IMPORTANT)

________________________________________

## Example:

Student ↔ Course

________________________________________

## Problem:

•	One student takes many courses  
•	One course has many students  

👉 direct mapping possible না

________________________________________

## Solution: Junction Table

## Student

| StudentID | Name |

________________________________________

## Course

| CourseID | Title |

________________________________________

## Enrollment (Bridge Table)

| StudentID (FK) | CourseID (FK) |

________________________________________

## Composite Key:
```sql
PK = (StudentID, CourseID)
```
 
________________________________________

## Extra Attributes Example:

If relationship has attributes:

Enrollment(Date, Grade)

________________________________________

Then:

| StudentID | CourseID | Date | Grade |

________________________________________

## 6. Multi-Valued Attribute (DETAILED)

________________________________________

## Example:

Student has multiple phone numbers

________________________________________

## ER Problem:

Phone = {017..., 018...}

________________________________________

## Rule:

👉 Create separate table

________________________________________

## Tables:

## Student

| StudentID | Name |

________________________________________

## StudentPhone

| StudentID (FK) | Phone |

________________________________________

## Why?
```sql
Avoid repeating group → 1NF requirement
```
 
________________________________________

---
</details>



