<h1 align="center">Intermediate SQL</h1>

> ### Explore each topic to understand the core concepts in detail
<p align="center">
  ⬇<b> Click any section below to expand </b> ⬇
</p>

---

<details>
  <summary><b> UPDATE Query</b></summary>

# UPDATE Query in SQL

UPDATE query ব্যবহার করা হয় table এর existing data modify/change করার জন্য।

👉 সহজভাবে:
INSERT = নতুন data add করে  
UPDATE = পুরনো data পরিবর্তন করে  

---

## Why UPDATE is Important?

Real-world database এ data সবসময় change হয়।

Examples:
• Student এর CGPA update করা  
• Employee এর salary increase করা  
• Product এর price পরিবর্তন করা  
• User এর email update করা  

এইসব কাজ UPDATE query দিয়ে করা হয়।

---

## Basic Syntax
```sql
UPDATE table_name
SET column_name = new_value
WHERE condition;

```
---

## Syntax Breakdown

| Part | Meaning |
|------|--------|
| UPDATE | কোন table update হবে |
| SET | কোন column change হবে |
| WHERE | কোন row update হবে |

---

## Example Table: Students

| StudentID | Name  | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.50 |
| 102 | Karim | EEE | 3.70 |
| 103 | Sakib | CSE | 3.80 |

---

## Example 1: Update Single Value

Rahim এর CGPA 3.50 থেকে 3.90 করতে চাই।
```sql
UPDATE Students
SET CGPA = 3.90
WHERE StudentID = 101;

```
---

### Before

| StudentID | Name  | CGPA |
|------------|------|------|
| 101 | Rahim | 3.50 |

---

### After

| StudentID | Name  | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |

---

👉 শুধু StudentID = 101 row update হয়েছে।

---

## Understanding WHERE Clause Importance

অনেক beginner সবচেয়ে বড় mistake এখানে করে।

ধরো তুমি লিখলে:
```sql
UPDATE Students
SET CGPA = 4.00;

```
---

কি হবে?

পুরো table এর সব student এর CGPA 4.00 হয়ে যাবে।

---

### Result

| StudentID | Name  | CGPA |
|------------|------|------|
| 101 | Rahim | 4.00 |
| 102 | Karim | 4.00 |
| 103 | Sakib | 4.00 |

---

⚠️ WARNING:
UPDATE query লেখার সময় WHERE condition double-check করতে হবে।  
Interview, Lab, Viva — সব জায়গায় এই question আসতে পারে।

---

## Example 2: Update Text Value

Karim এর department change করতে চাই।

### Before:
| StudentID | Name  | Department |
|------------|------|------------|
| 102 | Karim | EEE |

---

### Query:
```sql
UPDATE Students
SET Department = 'CSE'
WHERE StudentID = 102;

```
---

### After:

| StudentID | Name  | Department |
|------------|------|------------|
| 102 | Karim | CSE |

---

## Example 3: Update Multiple Columns

এক query তে multiple column update করা যায়।

### Before:

| StudentID | Name  | CGPA | Department |
|------------|------|------|------------|
| 101 | Rahim | 3.50 | CSE |

---

### Query:
```sql
UPDATE Students
SET CGPA = 3.95,
    Department = 'SWE'
WHERE StudentID = 101;

```
---

### After:

| StudentID | Name  | CGPA | Department |
|------------|------|------|------------|
| 101 | Rahim | 3.95 | SWE |

---

👉 একই query তে 2টা column update হয়েছে।

---

## Example 4: Update Using Condition

সব CSE student এর CGPA 0.10 increase করতে চাই।

### Before:

| Name  | Department | CGPA |
|------|------------|------|
| Rahim | CSE | 3.50 |
| Sakib | CSE | 3.80 |

---

### Query:
```sql
UPDATE Students
SET CGPA = CGPA + 0.10
WHERE Department = 'CSE';

```
---

### After:

| Name  | Department | CGPA |
|------|------------|------|
| Rahim | CSE | 3.60 |
| Sakib | CSE | 3.90 |

---

👉 Existing value এর উপর calculation করা যায়।

---

## Example 5: Salary Increase

### Employee Table:

| EmpID | Name  | Salary |
|------|------|--------|
| 1 | Rahim | 30000 |
| 2 | Karim | 35000 |

---

### Query:
```sql
UPDATE Employees
SET Salary = Salary + 5000;

```
---

### After:

| Name  | Salary |
|------|--------|
| Rahim | 35000 |
| Karim | 40000 |

---

👉 সবার salary 5000 increase হয়েছে।

---

## Example 6: Update Using AND

শুধু CSE department এর যাদের CGPA 3.80 এর নিচে তাদের update করবো।
```sql
UPDATE Students
SET CGPA = 3.80
WHERE Department = 'CSE'
AND CGPA < 3.80;

```
---

---

👉 Multiple condition ব্যবহার করা হয়েছে।

---

## Example 7: Update Using OR

---
```sql
UPDATE Students
SET Department = 'CS'
WHERE Department = 'CSE'
OR Department = 'Computer Science';

```
👉 যেকোনো condition true হলে update হবে।

---

## Example 8: Update Using BETWEEN
```sql
UPDATE Students
SET Scholarship = 'Eligible'
WHERE CGPA BETWEEN 3.75 AND 4.00;

```
---

👉 CGPA 3.75–4.00 এর মধ্যে হলে scholarship eligible।

---

## Example 9: Update Using IN
```sql
UPDATE Students
SET Department = 'CSE'
WHERE StudentID IN (101, 103, 105);

```
---

👉 Multiple specific rows update করা হয়েছে।

---

## Example 10: Update NULL Values

### Before:

| Name  | Phone |
|------|------|
| Rahim | NULL |

---

### Query:
```sql
UPDATE Students
SET Phone = '01700000000'
WHERE Phone IS NULL;

```
---

👉 NULL values replace করা হয়েছে।

---

## Real-Life University Example

### Table:

| StudentID | Name  | Semester |
|------------|------|----------|
| 101 | Rahim | 5 |
| 102 | Karim | 5 |
| 103 | Sakib | 5 |

---

New semester শুরু হয়েছে।  
সবাইকে semester 6 এ নিতে হবে।
```sql
UPDATE Students
SET Semester = 6
WHERE Semester = 5;

```
---

---

👉 Real-world bulk update example।

---

## Best Practices

1. আগে SELECT দিয়ে check করো
```sql
SELECT *
FROM Students
WHERE StudentID = 101;

```
---

তারপর UPDATE run করো।

---

2. Important data হলে Backup রাখো  
কারণ UPDATE এর পরে data permanently change হয়ে যায়।

---

3. WHERE ছাড়া UPDATE avoid করো
```sql
UPDATE Students
SET CGPA = 4.00;

```
---

⚠️ Dangerous Query

---

## Common Interview/Viva Questions

### Q: UPDATE এবং INSERT এর মধ্যে পার্থক্য কী?

| INSERT | UPDATE |
|--------|--------|
| New row add করে | Existing row modify করে |

---

### Q: UPDATE query তে SET এর কাজ কী?

SET দিয়ে কোন column এর value change হবে সেটা specify করা হয়।

---

### Q: UPDATE query তে WHERE না দিলে কী হবে?

Table এর সব rows update হয়ে যাবে।

---

## Quick Summary

• UPDATE existing data modify করে  
• SET দিয়ে new value assign করা হয়  
• WHERE দিয়ে target rows select করা হয়  
• Multiple columns update করা যায়  
• Arithmetic calculation করা যায়  
• WHERE ছাড়া UPDATE dangerous  

---

👉 মনে রাখার Shortcut

```sql
UPDATE → কোন table?

SET → কি change হবে?

WHERE → কোন row change হবে?

```
---
</details>


<details>
  <summary><b> DELETE Query</b></summary>

# DELETE Query in SQL

DELETE query ব্যবহার করা হয় table থেকে existing row/record remove করার জন্য।

👉 সহজভাবে:
INSERT = নতুন data add করে  
UPDATE = data modify করে  
DELETE = data remove করে  

---

## Why DELETE is Important?

Real-world database এ অনেক সময় data delete করতে হয়।

Examples:
• Student admission cancel হয়েছে  
• Employee চাকরি ছেড়ে দিয়েছে  
• Duplicate records remove করতে হবে  
• Product database থেকে obsolete product remove করতে হবে  

এইসব ক্ষেত্রে DELETE query ব্যবহার করা হয়।

---

## Basic Syntax
```sql
DELETE FROM table_name
WHERE condition;

```
---

## Syntax Breakdown

| Part | Meaning |
|------|--------|
| DELETE FROM | কোন table থেকে data delete হবে |
| WHERE | কোন row delete হবে |

---

## Example Table: Students

| StudentID | Name  | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.90 |
| 102 | Karim | EEE | 3.75 |
| 103 | Sakib | CSE | 3.85 |
| 104 | Nayeem | BBA | 3.60 |

---

## Example 1: Delete Single Row

Karim এর record delete করতে চাই।
```sql
DELETE FROM Students
WHERE StudentID = 102;

```
---

### Before

| StudentID | Name |
|------------|------|
| 101 | Rahim |
| 102 | Karim |
| 103 | Sakib |
| 104 | Nayeem |

---

### After

| StudentID | Name |
|------------|------|
| 101 | Rahim |
| 103 | Sakib |
| 104 | Nayeem |

---

👉 শুধুমাত্র StudentID = 102 row delete হয়েছে।

---

## Understanding WHERE Clause Importance

DELETE query তে WHERE clause সবচেয়ে গুরুত্বপূর্ণ।

---

## Dangerous Query
```sql
DELETE FROM Students;
```
---

কি হবে?

পুরো table এর সব data delete হয়ে যাবে।

---

## Result

| StudentID | Name |
|------------|------|
| No Records Found |
| No Records Found |

---

⚠️ WARNING:
DELETE query run করার আগে WHERE clause check করা বাধ্যতামূলক।

---

## Example 2: Delete Using Name
```sql
DELETE FROM Students
WHERE Name = 'Rahim';

```
---

👉 Rahim এর record delete হবে।

---

## Example 3: Delete Multiple Rows

সব CSE students delete করতে চাই।
```sql
DELETE FROM Students
WHERE Department = 'CSE';

```
---

### Before

| Name  | Department |
|------|------------|
| Rahim | CSE |
| Karim | EEE |
| Sakib | CSE |
| Nayeem | BBA |

---

### After

| Name  | Department |
|------|------------|
| Karim | EEE |
| Nayeem | BBA |

---

👉 একসাথে multiple rows delete হয়েছে।

---

## Example 4: Delete Using AND
```sql
DELETE FROM Students
WHERE Department = 'CSE'
AND CGPA < 3.90;

```
---

👉 CSE department এর যাদের CGPA 3.90 এর কম তাদের delete করবে।

---

### Deleted:
| Name  | CGPA |
|------|------|
| Sakib | 3.85 |

---

## Example 5: Delete Using OR
```sql
DELETE FROM Students
WHERE Department = 'EEE'
OR Department = 'BBA';

```
---

👉 EEE অথবা BBA department এর students delete হবে।

---

## Example 6: Delete Using IN
```sql
DELETE FROM Students
WHERE StudentID IN (101, 103, 105);

```
---

👉 Multiple specific records delete করা যায়।

---

## Example 7: Delete Using BETWEEN

ধরো CGPA কম যাদের তাদের remove করতে চাই।
```sql
DELETE FROM Students
WHERE CGPA BETWEEN 2.00 AND 3.00;

```
---

👉 CGPA 2.00–3.00 এর মধ্যে হলে delete হবে।

---

## Example 8: Delete NULL Values

ধরো Phone Number missing records remove করতে চাই।
```sql
DELETE FROM Students
WHERE Phone IS NULL;

```
---

👉 যাদের Phone NULL তাদের delete করবে।

---

## Example 9: Delete Top Records (SQL Server)

ধরো প্রথম 2টি row delete করতে চাই।
```sql
DELETE TOP (2)
FROM Students;

```
---

👉 SQL Server specific syntax

---

## Real-Life Example

### Product Table

| ProductID | ProductName | Stock |
|------------|-------------|-------|
| 1 | Laptop | 10 |
| 2 | Mouse | 0 |
| 3 | Keyboard | 5 |
| 4 | Monitor | 0 |

---

Out of stock products remove করতে চাই।
```sql
DELETE FROM Products
WHERE Stock = 0;

```
---

### After

| ProductName | Stock |
|-------------|-------|
| Laptop | 10 |
| Keyboard | 5 |

---

👉 Inventory clean-up এর common example।

---

## DELETE vs DROP vs TRUNCATE

এই তিনটা command নিয়ে viva তে প্রায়ই প্রশ্ন আসে।

---

## DELETE
```sql
DELETE FROM Students
WHERE StudentID = 101;

```
---

👉 Specific rows delete করে  
👉 WHERE ব্যবহার করা যায়  
👉 Structure থাকে  

---

## TRUNCATE
```sql
TRUNCATE TABLE Students;
```
---

👉 সব rows delete করে  
👉 WHERE ব্যবহার করা যায় না  
👉 Structure থাকে  

---

## DROP
```sql
DROP TABLE Students;
```
---

👉 পুরো table delete করে  
👉 Data + Structure দুইটাই remove হয়  

---

## Comparison Table

| Feature | DELETE | TRUNCATE | DROP |
|----------|--------|----------|------|
| Removes Data | ✅ | ✅ | ✅ |
| Removes Structure | ❌ | ❌ | ✅ |
| WHERE Support | ✅ | ❌ | ❌ |
| Specific Rows Delete | ✅ | ❌ | ❌ |
| Table Remains | ✅ | ✅ | ❌ |

---

## Best Practices

1. আগে SELECT দিয়ে check করো
```sql
SELECT *
FROM Students
WHERE StudentID = 102;

```
---

তারপর DELETE run করো।

---

2. Important database হলে backup রাখো  
কারণ DELETE এর পরে data recover করা কঠিন হতে পারে।

---

3. Primary Key দিয়ে delete করা safest
```sql
DELETE FROM Students
WHERE StudentID = 102;

```
---

কারণ Primary Key unique।

---

## Common Mistakes

---

### Mistake 1: WHERE Forgetting

❌ Wrong
```sql
DELETE FROM Students;
```
---

👉 পুরো table খালি হয়ে যাবে।

---

### Mistake 2: Wrong Condition

❌
```sql
DELETE FROM Students
WHERE Department = 'CSEE';

```
---

👉 Typo থাকলে expected row delete হবে না।

---

## Common Viva Questions

### Q: DELETE query কী করে?

Table থেকে existing records remove করে।

---

### Q: DELETE এবং DROP এর মধ্যে পার্থক্য কী?

DELETE শুধু data remove করে, DROP data এবং table structure দুটোই remove করে।

---

### Q: DELETE query তে WHERE না দিলে কী হবে?

Table এর সব rows delete হয়ে যাবে।

---

### Q: DELETE কি specific rows delete করতে পারে?

হ্যাঁ, WHERE clause ব্যবহার করে।

---

## Quick Summary

• DELETE table থেকে rows remove করে  
• WHERE দিয়ে target rows select করা হয়  
• WHERE ছাড়া DELETE dangerous  
• Multiple rows delete করা যায়  
• DELETE structure remove করে না  
• DELETE ≠ DROP ≠ TRUNCATE  

---

👉 মনে রাখার Shortcut
```sql
DELETE FROM → কোন table?

WHERE → কোন row delete হবে?

```
---
</details>

<details>
  <summary><b> ALTER Table</b></summary>

# ALTER TABLE in SQL

ALTER TABLE command ব্যবহার করা হয় existing table এর structure modify/change করার জন্য।

👉 সহজভাবে:
CREATE TABLE = নতুন table তৈরি করে  
ALTER TABLE = existing table এর structure পরিবর্তন করে  

---

## Why ALTER TABLE is Needed?

Real-world projects এ database design সবসময় প্রথমবারেই perfect হয় না।

কিছুদিন পরে প্রয়োজন হতে পারে:
• নতুন column add করা  
• Column delete করা  
• Column name change করা  
• Data type change করা  
• Constraint add/remove করা  

এসব কাজ ALTER TABLE দিয়ে করা হয়।

---

## Example Table

ধরি আমাদের Students table আছে:
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50),
    CGPA FLOAT
);

```
---

## Current Table Structure

| StudentID | Name  | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |
| 102 | Karim | 3.75 |

---

## 1. ADD COLUMN

নতুন column যোগ করার জন্য ব্যবহার হয়।

---

## Syntax
```sql
ALTER TABLE table_name
ADD column_name datatype;

```
---

## Example 1

Students table এ Email column add করবো।
```sql
ALTER TABLE Students
ADD Email VARCHAR(100);

```
---

### Before

| StudentID | Name  | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |

---

### After

| StudentID | Name  | CGPA | Email |
|------------|------|------|------|
| 101 | Rahim | 3.90 | NULL |

---

👉 Existing rows এ নতুন column এর value initially NULL হয়।

---

## Example 2: Add Multiple Columns
```sql
ALTER TABLE Students
ADD Phone VARCHAR(15),
    Address VARCHAR(200);

```
---

### After Structure

| StudentID | Name | CGPA | Phone | Address |

---

👉 একসাথে multiple columns add করা যায়।

---

## 2. DROP COLUMN

Column delete করার জন্য ব্যবহার হয়।

---

## Syntax
```sql
ALTER TABLE table_name
DROP COLUMN column_name;

```
---

## Example 3

Phone column remove করতে চাই।
```sql
ALTER TABLE Students
DROP COLUMN Phone;

```
---

### Before

| StudentID | Name  | Phone |
|------------|------|------|
| 101 | Rahim | 017xxxxxxx |

---

### After

| StudentID | Name |
|------------|------|
| 101 | Rahim |

---

⚠️ Warning:
DROP COLUMN করলে ওই column এর সব data permanently delete হয়ে যায়।

---

## 3. MODIFY / ALTER COLUMN (Data Type Change)

Column এর data type change করার জন্য ব্যবহার হয়।

---

## MySQL Syntax
```sql
ALTER TABLE Students
MODIFY CGPA DECIMAL(4,2);

```
---

## SQL Server Syntax
```sql
ALTER TABLE Students
ALTER COLUMN CGPA DECIMAL(4,2);

```
---

### Before
```sql
CGPA FLOAT
```
---

### After
```sql
CGPA DECIMAL(4,2)
```
---

👉 SQL Server এ আমরা সাধারণত ALTER COLUMN ব্যবহার করি।

---

## 4. Increase Column Size

---

## Example 4

আগে Name column ছিল:
```sql
Name VARCHAR(50)
```
---

এখন 100 character করতে চাই:
```sql
ALTER TABLE Students
ALTER COLUMN Name VARCHAR(100);

```
---

👉 Larger names store করা যাবে।

---

## 5. Rename Column

SQL Server এ sp_rename ব্যবহার করা হয়।

---

## Example 5

Name column কে StudentName করতে চাই।
```sql
EXEC sp_rename
'Students.Name',
'StudentName',
'COLUMN';

```
---

### Before

Name

---

### After

StudentName

---

## 6. Add DEFAULT Constraint

ধরো নতুন students এর default city হবে Dhaka।

---

## Example 6
```sql
ALTER TABLE Students
ADD CONSTRAINT DF_City
DEFAULT 'Dhaka' FOR City;

```
---

👉 City না দিলে automatically Dhaka save হবে।

---

## 7. Add CHECK Constraint

CGPA 4.00 এর বেশি হতে পারবে না।

---

## Example 7
```sql
ALTER TABLE Students
ADD CONSTRAINT CHK_CGPA
CHECK (CGPA <= 4.00);

```
---

### Valid
```sql
3.85
```
---

### Invalid
```sql
4.50
```
---

❌ Error দিবে।

---

## 8. Add UNIQUE Constraint

Email duplicate হওয়া যাবে না।

---

## Example 8
```sql
ALTER TABLE Students
ADD CONSTRAINT UQ_Email
UNIQUE (Email);

```
---

### Valid
```sql
rahim@gmail.com
karim@gmail.com

```
---

### Invalid
```sql
rahim@gmail.com
rahim@gmail.com

```
---

❌ Error হবে।

---

## 9. Add PRIMARY KEY

ধরো table create করার সময় primary key দেওয়া হয়নি।

---

## Example 9
```sql
ALTER TABLE Students
ADD CONSTRAINT PK_Student
PRIMARY KEY (StudentID);

```
---

👉 StudentID এখন Primary Key।

---

## 10. Add FOREIGN KEY

Departments table:
```sql
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY,
    DeptName VARCHAR(50)
);

```
---

## Students table এ Foreign Key add করবো
```sql
ALTER TABLE Students
ADD CONSTRAINT FK_Dept
FOREIGN KEY (DeptID)
REFERENCES Departments(DeptID);

```
---

👉 Referential Integrity maintain হবে।

---

## 11. Drop Constraint

আগে add করা constraint remove করতে চাই।

---

## Example 10
```sql
ALTER TABLE Students
DROP CONSTRAINT UQ_Email;

```
---

👉 Email column আর unique থাকবে না।

---

## Real-Life Example

ধরো University Database এ প্রথমে Email column ছিল না।

কিছুদিন পরে university সিদ্ধান্ত নিলো email store করবে।

তখন নতুন table create না করে:
```sql
ALTER TABLE Students
ADD Email VARCHAR(100);

```
---

👉 এটাই ALTER TABLE এর সবচেয়ে common use case।

---

## Common Errors

---

## Error 1: Duplicate Column Name
```sql
ALTER TABLE Students
ADD Name VARCHAR(50);

```
---

যদি Name আগে থেকেই থাকে:

❌ Error হবে

---

## Error 2: Data Type Conflict
```sql
ALTER TABLE Students
ALTER COLUMN Name INT;

```
---

যদি Name column এ text data থাকে:

❌ Error হতে পারে

---

## ALTER TABLE vs UPDATE

| ALTER TABLE | UPDATE |
|-------------|--------|
| Structure change করে | Data change করে |
| Column add/remove করে | Row values modify করে |
| Table design modify করে | Table data modify করে |

---

## Example

### ALTER TABLE
```sql
ALTER TABLE Students
ADD Email VARCHAR(100);

```
---

👉 Structure change

---

### UPDATE
```sql
UPDATE Students
SET Email = 'rahim@gmail.com'
WHERE StudentID = 101;

```
---

👉 Data change

---

## Common Viva Questions

### Q: ALTER TABLE কী?

Existing table এর structure modify করার command।

---

### Q: ALTER TABLE দিয়ে কী কী করা যায়?

• Add column  
• Drop column  
• Change datatype  
• Add constraint  
• Remove constraint  

---

### Q: ALTER TABLE কি data modify করে?

না, structure modify করে।

---

### Q: UPDATE এবং ALTER TABLE এর মধ্যে পার্থক্য কী?

UPDATE data change করে, ALTER TABLE structure change করে।

---

## Quick Summary

• ALTER TABLE = table structure modify  
• ADD = column add  
• DROP COLUMN = column delete  
• ALTER COLUMN = datatype change  
• Constraint add/remove করা যায়  
• Real-world projects এ খুব frequently use হয়  

---

👉 মনে রাখার Shortcut

```sql
ALTER TABLE

ADD → নতুন column

DROP → column remove

ALTER COLUMN → datatype change

ADD CONSTRAINT → rule add

```
---
</details>

<details>
  <summary><b> DROP & TRUNCATE</b></summary>

# DROP & TRUNCATE in SQL

DROP এবং TRUNCATE দুটোই data remove করার জন্য ব্যবহার হয়, কিন্তু এদের কাজ একদম আলাদা।

অনেক student viva, exam এবং interview তে এই দুইটা command নিয়ে confuse হয়ে যায়।  
তাই এই topic খুব ভালোভাবে clear থাকা দরকার।

---

## TRUNCATE TABLE

TRUNCATE command ব্যবহার করা হয় table এর সব rows/data delete করার জন্য।  
কিন্তু table structure (column, datatype, constraints) ঠিক থাকে।

👉 সহজভাবে:
TRUNCATE = Data remove  
Table = Remains  

---

## Syntax
```sql
TRUNCATE TABLE table_name;
```
---

## Example 1

ধরো Students table:

| StudentID | Name  | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |
| 102 | Karim | 3.75 |
| 103 | Sakib | 3.85 |

---

## Query:
```sql
TRUNCATE TABLE Students;
```
---

## Before

| StudentID | Name  | CGPA |
|------------|------|------|
| 101 | Rahim | 3.90 |
| 102 | Karim | 3.75 |
| 103 | Sakib | 3.85 |

---

## After

| StudentID | Name  | CGPA |
|------------|------|------|
| No Data | No Data | No Data |

---

কিন্তু table এখনও exist করছে।

---

## Verify
```sql
SELECT * FROM Students;
```
---

## Output:
```sql
Empty Set
```
---

কিন্তু table delete হয়নি।

---

## Structure Still Exists

নতুন data insert করা যাবে:
```sql
INSERT INTO Students
VALUES (101, 'Rahim', 3.95);

```
---

👉 কারণ table structure এখনও আছে।

---

## Why TRUNCATE is Faster Than DELETE?

ধরো 10 lakh rows আছে।

### DELETE:
```sql
DELETE FROM Students;
```
---

একটা একটা row delete করবে।

### TRUNCATE:
```sql
TRUNCATE TABLE Students;
```
---

Directly entire data pages remove করে।

---

তাই TRUNCATE অনেক faster।

---

## Important Characteristics of TRUNCATE

### Removes All Rows
```sql
TRUNCATE TABLE Students;
```
---

### Cannot Use WHERE

❌ Wrong
```sql
TRUNCATE TABLE Students
WHERE StudentID = 101;

```
---

Error হবে।

কারণ TRUNCATE specific row delete করতে পারে না।

---

### Table Structure Remains

Columns, Constraints, Keys সব থাকে।

---

# DROP TABLE

DROP command ব্যবহার করা হয় পুরো table permanently remove করার জন্য।

👉 সহজভাবে:
DROP = Data + Structure দুটোই remove  

---

## Syntax
```sql
DROP TABLE table_name;
```
---

## Example 2

Students table:

| StudentID | Name |
|------------|------|
| 101 | Rahim |
| 102 | Karim |

---

## Query:
```sql
DROP TABLE Students;
```
---

## What Happens?

Data Deleted ✔️  
Columns Deleted ✔️  
Constraints Deleted ✔️  
Entire Table Deleted ✔️  

---

Table completely disappear হয়ে যাবে।

---

## Verify
```sql
SELECT * FROM Students;
```
---

## Output:
```sql
Invalid object name 'Students'
```
---

কারণ table আর exist করে না।

---

## To Use Again?

আবার create করতে হবে।
```sql
CREATE TABLE Students(
    StudentID INT,
    Name VARCHAR(50)
);

```
---

👉 DROP এর পরে table recreate করতে হয়।

---

## Real-Life Example

ধরো University Database এ একটি test table আছে।
```sql
TestStudents
```
Project শেষ।  
Table আর লাগবে না।

তখন:
```sql
DROP TABLE TestStudents;
```
---

পুরো table remove হয়ে যাবে।

---

## TRUNCATE vs DELETE

ধরো table:

| ID | Name |
|----|------|
| 1 | Rahim |
| 2 | Karim |
| 3 | Sakib |

---

### DELETE:
```sql
DELETE FROM Students
WHERE ID = 1;

```
---

Result:

| ID | Name |
|----|------|
| 2 | Karim |
| 3 | Sakib |

---

Specific row delete হয়েছে।

---

### TRUNCATE:
```sql
TRUNCATE TABLE Students;
```
---

Result:

| ID | Name |
|----|------|
| No Rows |

---

সব rows delete হয়েছে।

---

## DROP vs TRUNCATE

সবচেয়ে important comparison।

---

### Example

TRUNCATE:
```sql
TRUNCATE TABLE Students;
```
---

After:
```sql
INSERT INTO Students
VALUES (1,'Rahim');

```
---

✔️ Works  
কারণ table আছে।

---

DROP:
```sql
DROP TABLE Students;
```
---

After:
```sql
INSERT INTO Students
VALUES (1,'Rahim');

```
---

❌ Error  
কারণ table exist করে না।

---

## Comparison Table

| Feature | DELETE | TRUNCATE | DROP |
|----------|--------|----------|------|
| Removes Data | ✅ | ✅ | ✅ |
| Removes Structure | ❌ | ❌ | ✅ |
| WHERE Support | ✅ | ❌ | ❌ |
| Specific Rows Delete | ✅ | ❌ | ❌ |
| Table Remains | ✅ | ✅ | ❌ |
| Faster | ❌ | ✅ | ✅ |
| Reuse Table Immediately | ✅ | ✅ | ❌ |

---

## University Example

### Students Table
```sql
Students
```
---

## Situation 1

সব student data remove করতে হবে  
কিন্তু table থাকবে
```sql
TRUNCATE TABLE Students;
```
---

## Situation 2

পুরো table আর দরকার নেই
```sql
DROP TABLE Students;
```
---

---

## Common Mistakes

---

### Mistake 1

DROP এর জায়গায় TRUNCATE ব্যবহার করা

---

### Mistake 2

TRUNCATE এর সাথে WHERE ব্যবহার করা

❌
```sql
TRUNCATE TABLE Students
WHERE ID = 1;

```
---

### Mistake 3

DROP করার পরে table আছে মনে করা
```sql
DROP TABLE Students;
```
---

তারপর:
```sql
SELECT * FROM Students;
```
❌ Error

---

## Common Viva Questions

### Q: TRUNCATE কী?

Table এর সব rows delete করে কিন্তু structure রাখে।

---

### Q: DROP কী?

Data + Structure দুটোই permanently delete করে।

---

### Q: TRUNCATE এ WHERE ব্যবহার করা যায়?

না।

---

### Q: DROP করার পরে table থাকে?

না।

---

### Q: DELETE, TRUNCATE, DROP এর মধ্যে সবচেয়ে dangerous কোনটা?

DROP, কারণ পুরো table remove হয়ে যায়।

---

## Quick Summary

• DELETE → Specific rows delete  
• TRUNCATE → All rows delete, structure থাকে  
• DROP → Data + Structure দুটোই delete  

---

👉 মনে রাখার Shortcut

```sql
DELETE = Some Data Remove

TRUNCATE = All Data Remove

DROP = Everything Remove

```
---
</details>


<details>
  <summary><b> Aggregate Functions</b></summary>

# Aggregate Functions in SQL

Aggregate Functions হলো এমন special SQL functions যেগুলো multiple rows এর data নিয়ে একটি single result return করে।

👉 সহজভাবে:
অনেক data → Process → 1টা result  

---

## Why Aggregate Functions are Used?

Database এ হাজার হাজার records থাকতে পারে।  
সব data manually analyse করা সম্ভব না।

তখন Aggregate Functions ব্যবহার করে:
• মোট কত records আছে  
• Total কত  
• Average কত  
• Highest value কত  
• Lowest value কত  

খুব সহজে বের করা যায়।

---

## Example Table: Students

| StudentID | Name  | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.90 |
| 102 | Karim | EEE | 3.75 |
| 103 | Sakib | CSE | 3.85 |
| 104 | Nayeem | BBA | 3.60 |
| 105 | Arafat | CSE | 3.95 |

---

## Aggregate Functions List

| Function | Purpose |
|----------|--------|
| COUNT() | Records count করে |
| SUM() | Total বের করে |
| AVG() | Average বের করে |
| MAX() | Highest value বের করে |
| MIN() | Lowest value বের করে |

---

## 1. COUNT()

COUNT() ব্যবহার করা হয় মোট কত rows/records আছে তা বের করার জন্য।

---

## Syntax
```sql
SELECT COUNT(column_name)
FROM table_name;

```
---

## Example 1
```sql
SELECT COUNT(*)
FROM Students;

```
---

## Output
```sql
5
```
👉 Table এ মোট 5 জন student আছে।

---

## COUNT(*)

সব rows count করে।
```sql
SELECT COUNT(*)
FROM Students;

```
---

COUNT(*) সবচেয়ে বেশি ব্যবহার করা হয়।

---

## COUNT(Column)
```sql
SELECT COUNT(CGPA)
FROM Students;

```
---

👉 CGPA যেসব row তে NULL না, সেগুলো count করবে।

---

## Example with NULL

| Name  | CGPA |
|------|------|
| Rahim | 3.90 |
| Karim | NULL |
| Sakib | 3.85 |

---
```sql
SELECT COUNT(CGPA)
FROM Students;

```
## Output:
```sql
2
```
---

কারণ NULL count হয় না।

---

## COUNT(DISTINCT)

Unique values count করতে।

---

## Example
```sql
SELECT COUNT(DISTINCT Department)
FROM Students;

```
---

## Departments:
```sql
CSE
EEE
CSE
BBA
CSE

```
---

## Output:
```sql
3
```
---

কারণ Unique Departments:

---
```sql
CSE
EEE
BBA

```
---

## 2. SUM()

SUM() ব্যবহার করা হয় numeric values এর total বের করার জন্য।

---

## Syntax
```sql
SELECT SUM(column_name)
FROM table_name;

```
---

## Example Table

| Product | Price |
|----------|------|
| Laptop | 85000 |
| Monitor | 15000 |
| Mouse | 1000 |

---

## Example
```sql
SELECT SUM(Price)
FROM Products;

```
---

## Output:
```sql
101000
```
---

## Calculation:
```sql
85000 + 15000 + 1000
= 101000

```
---

👉 Total Price বের হয়েছে।

---

## SUM with WHERE
```sql
SELECT SUM(Price)
FROM Products
WHERE Price > 5000;

```
---

Only Laptop + Monitor
```sql
100000
```
---

## 3. AVG()

AVG() ব্যবহার করা হয় average value বের করার জন্য।

---

## Syntax
```sql
SELECT AVG(column_name)
FROM table_name;

```
---

## Example

Students Table:

| Name  | CGPA |
|------|------|
| Rahim | 3.90 |
| Karim | 3.75 |
| Sakib | 3.85 |
| Nayeem | 3.60 |
| Arafat | 3.95 |

---

## Query:
```sql
SELECT AVG(CGPA)
FROM Students;

```
---

## Calculation:
```sql
3.90 + 3.75 + 3.85 + 3.60 + 3.95
= 19.05

19.05 ÷ 5
= 3.81

```
---

## Output:
```sql
3.81
```
---

👉 Average CGPA বের হয়েছে।

---

## AVG with WHERE
```sql
SELECT AVG(CGPA)
FROM Students
WHERE Department = 'CSE';

```
---

Only CSE students এর average বের হবে।

---

## 4. MAX()

MAX() ব্যবহার করা হয় highest value বের করার জন্য।

---

## Syntax
```sql
SELECT MAX(column_name)
FROM table_name;

```
---

## Example
```sql
SELECT MAX(CGPA)
FROM Students;

```
---

## Output:
```sql
3.95
```
---

👉 Highest CGPA

---

## Another Example
```sql
SELECT MAX(Price)
FROM Products;

```
---

## Output:
```sql
85000
```
---

👉 Most expensive product price

---

## MAX() with Text
```sql
SELECT MAX(Name)
FROM Students;

```
---

## Output:
```sql
Sakib
```
---

কারণ alphabetically সবচেয়ে বড় value।

---

## 5. MIN()

MIN() ব্যবহার করা হয় lowest value বের করার জন্য।

---

## Syntax
```sql
SELECT MIN(column_name)
FROM table_name;

```
---

## Example
```sql
SELECT MIN(CGPA)
FROM Students;

```
---

## Output:
```sql
3.60
```
---

👉 Lowest CGPA

---

## Another Example
```sql
SELECT MIN(Price)
FROM Products;

```
---

## Output:
```sql
1000
```
---

👉 Cheapest product

---

## Using Multiple Aggregate Functions Together

---

## Example
```sql
SELECT
COUNT(*) AS TotalStudents,
AVG(CGPA) AS AverageCGPA,
MAX(CGPA) AS HighestCGPA,
MIN(CGPA) AS LowestCGPA
FROM Students;

```
---

## Output

| TotalStudents | AverageCGPA | HighestCGPA | LowestCGPA |
|----------------|------------|-------------|------------|
| 5 | 3.81 | 3.95 | 3.60 |

---

👉 এক query তেই অনেক information পাওয়া যায়।

---

## Real-Life Example (University System)

---

## Total Students
```sql
SELECT COUNT(*)
FROM Students;

```
---

## Average CGPA
```sql
SELECT AVG(CGPA)
FROM Students;

```
---

## Highest CGPA
```sql
SELECT MAX(CGPA)
FROM Students;

```
---

## Lowest CGPA
```sql
SELECT MIN(CGPA)
FROM Students;

```
---

## Total Scholarship Amount
```sql
SELECT SUM(ScholarshipAmount)
FROM Students;

```
---

---

## Common Mistakes

---

## Mistake 1

SUM() text column এ ব্যবহার করা

❌
```sql
SELECT SUM(Name)
FROM Students;

```
---

Error হবে।

---

## Mistake 2

COUNT() এবং COUNT(column) কে একই মনে করা
```sql
COUNT(*)
```
 

সব rows count করে

---
```sql
COUNT(CGPA)
```
 

NULL ছাড়া rows count করে

---

---

## Aggregate Functions + WHERE

এটা খুব common interview question।
```sql
SELECT AVG(CGPA)
FROM Students
WHERE Department = 'CSE';

```
 

👉 Aggregate function এর আগে WHERE apply হয়।

---

## Common Viva Questions

### Q: Aggregate Function কী?

Multiple rows process করে single result return করে।

---

### Q: COUNT(*) কী করে?

সব rows count করে।

---

### Q: AVG() কী করে?

Average বের করে।

---

### Q: MAX() কী return করে?

Highest value।

---

### Q: MIN() কী return করে?

Lowest value।

---

### Q: SUM() কী return করে?

Total value।

---

### Q: COUNT(column) কি NULL count করে?

না।

---

## Quick Summary

| Function | Returns |
|----------|--------|
| COUNT() | Total records |
| SUM() | Total value |
| AVG() | Average value |
| MAX() | Highest value |
| MIN() | Lowest value |

---

👉 মনে রাখার Shortcut
```sql
COUNT = How Many?

SUM = Total?

AVG = Average?

MAX = Highest?

MIN = Lowest?

```
---
</details>


<details>
  <summary><b>GROUP BY </b></summary>

# GROUP BY in SQL

GROUP BY ব্যবহার করা হয় একই ধরনের data গুলোকে group করে তাদের উপর aggregate function (COUNT, SUM, AVG, MAX, MIN) apply করার জন্য।

👉 সহজভাবে:
GROUP BY = একই category অনুযায়ী data group করা + তারপর calculation করা  

---

## Why GROUP BY is Important?

Real-world database এ আমরা শুধু full table analysis করি না, বরং category-wise analysis করি।

Examples:
• প্রতি department এ কত student আছে  
• প্রতি department এর average CGPA  
• প্রতি product category এর total sales  
• প্রতি city তে কত customer  

এই সব কিছু GROUP BY ছাড়া সম্ভব না।

---

## Basic Syntax
```sql
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name;

```
---

## Example Table: Students

| StudentID | Name  | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.90 |
| 102 | Karim | EEE | 3.75 |
| 103 | Sakib | CSE | 3.85 |
| 104 | Nayeem | BBA | 3.60 |
| 105 | Arafat | CSE | 3.95 |

---

## 1. GROUP BY with COUNT()

👉 প্রতি department এ কত student আছে

---

## Query
```sql
SELECT Department, COUNT(*) AS TotalStudents
FROM Students
GROUP BY Department;

```
---

## Output

| Department | TotalStudents |
|------------|--------------|
| CSE | 3 |
| EEE | 1 |
| BBA | 1 |

---

👉 একই department একসাথে group হয়ে গেছে

---

## 2. GROUP BY with AVG()

👉 প্রতি department এর average CGPA

---

## Query
```sql
SELECT Department, AVG(CGPA) AS AverageCGPA
FROM Students
GROUP BY Department;

```
---

## Output

| Department | AverageCGPA |
|------------|------------|
| CSE | 3.90 |
| EEE | 3.75 |
| BBA | 3.60 |

---

CSE calculation:
```sql
(3.90 + 3.85 + 3.95) / 3 = 3.90
```
---

## 3. GROUP BY with SUM()

👉 department wise total CGPA

---

## Query
```sql
SELECT Department, SUM(CGPA) AS TotalCGPA
FROM Students
GROUP BY Department;

```
---

## Output

| Department | TotalCGPA |
|------------|----------|
| CSE | 11.70 |
| EEE | 3.75 |
| BBA | 3.60 |

---

## 4. GROUP BY with MAX()

👉 প্রতি department এর highest CGPA

---

## Query
```sql
SELECT Department, MAX(CGPA) AS HighestCGPA
FROM Students
GROUP BY Department;

```
---

## Output

| Department | HighestCGPA |
|------------|------------|
| CSE | 3.95 |
| EEE | 3.75 |
| BBA | 3.60 |

---

## 5. GROUP BY with MIN()

👉 প্রতি department এর lowest CGPA

---

## Query
```sql
SELECT Department, MIN(CGPA) AS LowestCGPA
FROM Students
GROUP BY Department;

```
---

## Output

| Department | LowestCGPA |
|------------|------------|
| CSE | 3.85 |
| EEE | 3.75 |
| BBA | 3.60 |

---

## 6. GROUP BY with WHERE

👉 আগে filter হবে, তারপর group হবে

---

## Query
```sql
SELECT Department, AVG(CGPA) AS AvgCGPA
FROM Students
WHERE CGPA > 3.80
GROUP BY Department;

```
---

👉 শুধু 3.80 এর বেশি CGPA student নিয়ে group হবে

---

## 7. GROUP BY with HAVING (Very Important)

👉 GROUP BY এর পরে condition apply করতে HAVING ব্যবহার হয়

---

## Difference:

| WHERE | HAVING |
|------|--------|
| Row level filter | Group level filter |
| GROUP BY এর আগে | GROUP BY এর পরে |

---

## Example 1

👉 শুধু সেই department দেখাবে যাদের student সংখ্যা 2 এর বেশি

---

## Query
```sql
SELECT Department, COUNT(*) AS TotalStudents
FROM Students
GROUP BY Department
HAVING COUNT(*) > 2;

```
---

## Output

| Department | TotalStudents |
|------------|--------------|
| CSE | 3 |

---

👉 শুধু CSE show হবে

---

## Example 2

👉 average CGPA 3.80 এর বেশি department

---

## Query
```sql
SELECT Department, AVG(CGPA) AS AvgCGPA
FROM Students
GROUP BY Department
HAVING AVG(CGPA) > 3.80;

```
---

## Output

| Department | AvgCGPA |
|------------|--------|
| CSE | 3.90 |

---

## 8. GROUP BY with Multiple Columns

👉 একাধিক column দিয়ে grouping করা যায়

---

## Example Table: Sales

| City | Product | Sales |
|------|--------|------|
| Dhaka | Laptop | 10 |
| Dhaka | Mouse | 20 |
| Chittagong | Laptop | 5 |

---

## Query
```sql
SELECT City, Product, SUM(Sales) AS TotalSales
FROM Sales
GROUP BY City, Product;

```
---

## Output

| City | Product | TotalSales |
|------|--------|-----------|
| Dhaka | Laptop | 10 |
| Dhaka | Mouse | 20 |
| Chittagong | Laptop | 5 |

---

👉 City + Product combination group হয়েছে

---

## 9. GROUP BY with ORDER BY

---

## Query
```sql
SELECT Department, COUNT(*) AS TotalStudents
FROM Students
GROUP BY Department
ORDER BY TotalStudents DESC;

```
---

👉 highest student department first

---

## Real-Life Example (University System)

---

## Example 1: Department wise students
```sql
SELECT Department, COUNT(*) AS Total
FROM Students
GROUP BY Department;

```
---

## Example 2: Scholarship analysis
```sql
SELECT Department, AVG(CGPA) AS AvgCGPA
FROM Students
GROUP BY Department
HAVING AVG(CGPA) >= 3.75;

```
---

## Example 3: Highest achiever department
```sql
SELECT Department, MAX(CGPA)
FROM Students
GROUP BY Department;

```
---

## Common Mistakes

---

## Mistake 1: SELECT column not in GROUP BY

❌ Wrong:
```sql
SELECT Name, Department, COUNT(*)
FROM Students
GROUP BY Department;

```
---

👉 Name group করা হয়নি → error বা wrong result

---

## Mistake 2: HAVING vs WHERE confusion

❌ Wrong:
```sql
SELECT Department, COUNT(*)
FROM Students
WHERE COUNT(*) > 2
GROUP BY Department;

```
---

👉 Aggregate function WHERE এ use করা যায় না

---

## Common Viva Questions

### Q: GROUP BY কী?

Same values কে group করে aggregate function apply করে।

---

### Q: WHERE এবং HAVING এর পার্থক্য?

| WHERE | HAVING |
|------|--------|
| Row filter | Group filter |

---

### Q: GROUP BY ছাড়া COUNT ব্যবহার করা যায়?

হ্যাঁ, কিন্তু group analysis হবে না।

---

### Q: HAVING কেন ব্যবহার করা হয়?

Aggregate result filter করার জন্য।

---

## Quick Summary

• GROUP BY = category-wise grouping  
• Aggregate function এর সাথে ব্যবহার হয়  
• WHERE = row filter  
• HAVING = group filter  
• Multiple column grouping possible  

---

👉 মনে রাখার Shortcut
```sql
GROUP BY → Group data

HAVING → Group filter

WHERE → Row filter

```
---
</details>

<details>
  <summary><b>HAVING Clause </b></summary>

# HAVING Clause in SQL

HAVING clause ব্যবহার করা হয় GROUP BY এর পরে তৈরি হওয়া groups এর উপর condition apply করার জন্য।

👉 সহজভাবে:
WHERE = row filter  
HAVING = group filter  

---

## Why HAVING is Needed?

GROUP BY দিয়ে যখন data group করা হয়, তখন সেই group গুলোর উপর condition দিতে হয়।

কিন্তু সমস্যা হলো:
👉 WHERE aggregate function (COUNT, SUM, AVG) এর সাথে কাজ করে না  
👉 তাই GROUP level filter করার জন্য HAVING লাগে  

---

## Basic Syntax
```sql
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;

```
---

## Example Table: Students

| StudentID | Name  | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.90 |
| 102 | Karim | EEE | 3.75 |
| 103 | Sakib | CSE | 3.85 |
| 104 | Nayeem | BBA | 3.60 |
| 105 | Arafat | CSE | 3.95 |

---

## 1. HAVING with COUNT()

👉 যেসব department এ 2 জনের বেশি student আছে

---

## Query
```sql
SELECT Department, COUNT(*) AS TotalStudents
FROM Students
GROUP BY Department
HAVING COUNT(*) > 2;

```
---

## Step Breakdown

First GROUP BY result:

| Department | Count |
|------------|------|
| CSE | 3 |
| EEE | 1 |
| BBA | 1 |

---

Then HAVING apply:
👉 COUNT > 2  
✔ Only CSE remains  

---

## Final Output:

| Department | TotalStudents |
|------------|--------------|
| CSE | 3 |

---

## 2. HAVING with AVG()

👉 যেসব department এর average CGPA 3.80 এর বেশি

---

## Query
```sql
SELECT Department, AVG(CGPA) AS AvgCGPA
FROM Students
GROUP BY Department
HAVING AVG(CGPA) > 3.80;

```
---

## Calculation:

CSE:
```sql
(3.90 + 3.85 + 3.95) / 3 = 3.90
```
---

EEE:
```sql
3.75
```
---

BBA:
```sql
3.60
```
---

## Final Output:

| Department | AvgCGPA |
|------------|--------|
| CSE | 3.90 |

---

## 3. HAVING with SUM()

👉 যেসব department এর total CGPA 10 এর বেশি

---

## Query
```sql
SELECT Department, SUM(CGPA) AS TotalCGPA
FROM Students
GROUP BY Department
HAVING SUM(CGPA) > 10;

```
---

## Output:

| Department | TotalCGPA |
|------------|----------|
| CSE | 11.70 |

---

## 4. HAVING with MAX()

👉 যেসব department এর highest CGPA 3.90 এর বেশি

---

## Query
```sql
SELECT Department, MAX(CGPA) AS HighestCGPA
FROM Students
GROUP BY Department
HAVING MAX(CGPA) > 3.90;

```
---

## Output:

| Department | HighestCGPA |
|------------|------------|
| CSE | 3.95 |

---

## 5. HAVING with MIN()

👉 যেসব department এর lowest CGPA 3.70 এর নিচে

---

## Query
```sql
SELECT Department, MIN(CGPA) AS LowestCGPA
FROM Students
GROUP BY Department
HAVING MIN(CGPA) < 3.70;

```
---

## Output:

| Department | LowestCGPA |
|------------|------------|
| BBA | 3.60 |

---

## 6. WHERE vs HAVING (Very Important)

## WHERE (Row Level Filter)
```sql
SELECT *
FROM Students
WHERE CGPA > 3.80;

```
---

👉 row filter (grouping এর আগে)

---

## HAVING (Group Level Filter)
```sql
SELECT Department, AVG(CGPA)
FROM Students
GROUP BY Department
HAVING AVG(CGPA) > 3.80;

```
---

👉 group filter (grouping এর পরে)

---

## Key Difference

| WHERE | HAVING |
|------|--------|
| Row filter | Group filter |
| Before GROUP BY | After GROUP BY |
| No aggregate support | Aggregate support |

---

## 7. WHERE + HAVING Together

👉 real-world queries এ দুটো একসাথে ব্যবহার হয়

---

## Example

👉 CGPA > 3.70 students নিয়ে group করে average বের করা, তারপর filter করা
```sql
SELECT Department, AVG(CGPA) AS AvgCGPA
FROM Students
WHERE CGPA > 3.70
GROUP BY Department
HAVING AVG(CGPA) > 3.80;

```
---

---

## Step-by-step:

### Step 1: WHERE
Only CGPA > 3.70:
• Rahim (3.90)  
• Karim (3.75)  
• Sakib (3.85)  
• Arafat (3.95)  

---

### Step 2: GROUP BY Department

---

### Step 3: HAVING AVG > 3.80

✔ Only CSE remains

---

## 8. HAVING with ORDER BY
```sql
SELECT Department, COUNT(*) AS TotalStudents
FROM Students
GROUP BY Department
HAVING COUNT(*) >= 1
ORDER BY TotalStudents DESC;

```
---

👉 result sorted

---

## Real-Life Example

---

University Analysis  
👉 যেসব department এ scholarship eligible students বেশি
```sql
SELECT Department, COUNT(*) AS EligibleStudents
FROM Students
WHERE CGPA >= 3.75
GROUP BY Department
HAVING COUNT(*) >= 2;

```
---

## Common Mistakes

---

## Mistake 1: Using HAVING without GROUP BY

❌ Wrong:
```sql
SELECT *
FROM Students
HAVING CGPA > 3.80;

```
---

---

## Mistake 2: Using WHERE with aggregate

❌ Wrong:
```sql
SELECT Department, AVG(CGPA)
FROM Students
WHERE AVG(CGPA) > 3.80
GROUP BY Department;

```
---

---

## Correct Rule
```sql
Aggregate function → HAVING

Normal column → WHERE

```
---

---

## Common Viva Questions

### Q: HAVING কী?

GROUP BY এর পরে group filter করার clause।

---

### Q: WHERE এবং HAVING এর পার্থক্য?

| WHERE | HAVING |
|------|--------|
| Row filter | Group filter |

---

### Q: HAVING ছাড়া GROUP BY use করা যায়?

হ্যাঁ।

---

### Q: HAVING এ aggregate function use করা যায়?

হ্যাঁ।

---

## Quick Summary

• HAVING = group filter  
• GROUP BY এর পরে কাজ করে  
• Aggregate function support করে  
• WHERE = row filter  
• WHERE আগে, HAVING পরে  

---

👉 মনে রাখার Shortcut

```sql
WHERE → Before grouping

HAVING → After grouping

```
---
</details>

<details>
  <summary><b> LIKE Operator</b></summary>

# LIKE Operator in SQL

LIKE operator ব্যবহার করা হয় pattern matching এর জন্য। অর্থাৎ কোনো column এর ভিতরে নির্দিষ্ট pattern অনুযায়ী data search করতে।

👉 সহজভাবে:
LIKE = text search / pattern match system  

---

## Why LIKE is Important?

Real database এ আমরা exact value সবসময় জানি না।

Examples:
• নামের শুরুতে “A” আছে এমন student  
• email এ “gmail” আছে এমন user  
• যাদের নামের শেষে “m” আছে  
• কোনো word এর মধ্যে নির্দিষ্ট letter আছে  

এইসব কাজ LIKE দিয়ে করা হয়।

---

## Basic Syntax
```sql
SELECT column_name
FROM table_name
WHERE column_name LIKE 'pattern';

```
---

## Wildcards in LIKE

LIKE operator এর সাথে কিছু special symbol ব্যবহার করা হয়:

| Symbol | Meaning |
|--------|--------|
| % | যেকোনো number of characters |
| _ | single character |

---

## Example Table: Students

| StudentID | Name  | Department | Email |
|------------|------|------------|------|
| 101 | Rahim | CSE | rahim@gmail.com |
| 102 | Karim | EEE | karim@yahoo.com |
| 103 | Sakib | CSE | sakib@gmail.com |
| 104 | Nayeem | BBA | nayeem@gmail.com |
| 105 | Arafat | CSE | arafat@yahoo.com |

---

## 1. Starts With Pattern (%)

👉 কোনো value নির্দিষ্ট letter/word দিয়ে শুরু হলে

---

## Example 1: Name starts with 'R'
```sql
SELECT *
FROM Students
WHERE Name LIKE 'R%';

```
---

## Output:

| Name |
|------|
| Rahim |

---

👉 R দিয়ে শুরু হওয়া সব name

---

## 2. Ends With Pattern (%)

👉 কোনো value নির্দিষ্ট letter/word দিয়ে শেষ হলে

---

## Example 2: Name ends with 'm'
```sql
SELECT *
FROM Students
WHERE Name LIKE '%m';

```
---

## Output:

| Name |
|------|
| Rahim |
| Karim |

---

👉 m দিয়ে শেষ হওয়া names

---

## 3. Contains Pattern (%)

👉 কোনো value এর মধ্যে কোথাও নির্দিষ্ট text থাকলে

---

## Example 3: Name contains 'ai'
```sql
SELECT *
FROM Students
WHERE Name LIKE '%ai%';

```
---

## Output:

| Name |
|------|
| Rahim |

---

👉 “ai” নামের মধ্যে আছে

---

## 4. Email Search Example

👉 gmail users বের করা

---

## Example 4
```sql
SELECT *
FROM Students
WHERE Email LIKE '%gmail%';

```
---

## Output:

| Email |
|------|
| rahim@gmail.com |
| sakib@gmail.com |
| nayeem@gmail.com |

---

👉 gmail থাকা সব email

---

## 5. Specific Starting Pattern (Department)

---

## Example 5
```sql
SELECT *
FROM Students
WHERE Department LIKE 'C%';

```
---

👉 C দিয়ে শুরু হওয়া department (CSE)

---

## 6. Single Character Match (_)

👉 ঠিক 1টা character match করে

---

## Example 6
```sql
SELECT *
FROM Students
WHERE Name LIKE '_a%';

```
---

👉 দ্বিতীয় letter “a” এমন name

---

## Possible Match:

| Name |
|------|
| Karim |
| Sakib |

---

## 7. Fixed Length Pattern

---

## Example 7
```sql
SELECT *
FROM Students
WHERE Name LIKE '_____';

```
---

👉 ঠিক 5 character এর নাম

---

## 8. LIKE with NOT

👉 pattern ছাড়া data বের করতে

---

## Example 8
```sql
SELECT *
FROM Students
WHERE Name NOT LIKE 'R%';

```
---

👉 R দিয়ে শুরু না হওয়া names

---

## 9. Case Sensitivity Note

| DBMS | Case Sensitive |
|------|----------------|
| MySQL | Usually NO |
| PostgreSQL | YES |
| SQL Server | Depends |

---

👉 তাই “rahim” এবং “Rahim” আলাদা হতে পারে (DB অনুযায়ী)

---

## 10. Real-Life Example

---

## University Email Filter
```sql
SELECT *
FROM Students
WHERE Email LIKE '%@gmail.com';

```
---

👉 শুধুমাত্র Gmail users

---

## Result:

| Email |
|------|
| rahim@gmail.com |
| sakib@gmail.com |
| nayeem@gmail.com |

---

## 11. Product Search Example

| ProductID | ProductName |
|------------|-------------|
| 1 | Laptop HP |
| 2 | Dell Mouse |
| 3 | HP Monitor |

---

## Query
```sql
SELECT *
FROM Products
WHERE ProductName LIKE '%HP%';

```
---

👉 HP related products

---

## 12. LIKE with ORDER BY
```sql
SELECT *
FROM Students
WHERE Name LIKE 'A%'
ORDER BY Name ASC;

```
---

---

👉 A দিয়ে শুরু হওয়া names sorted order এ

---

## Common Mistakes

---

## Mistake 1: Wrong wildcard usage

❌
```sql
WHERE Name LIKE 'R'
```
---

👉 শুধু exact “R” খুঁজবে

---

## Mistake 2: Forgetting %

❌
```sql
WHERE Name LIKE 'Rah'
```
---

👉 partial match হবে না

---

## Correct:
```sql
WHERE Name LIKE 'Rah%'
```
---

---

## Viva Questions

### Q: LIKE operator কী?

Pattern matching এর জন্য ব্যবহার হয়।

---

### Q: % এবং _ এর পার্থক্য?

| Symbol | Meaning |
|--------|--------|
| % | multiple characters |
| _ | single character |

---

### Q: LIKE case sensitive?

DBMS অনুযায়ী vary করে।

---

### Q: LIKE কেন ব্যবহার করা হয়?

Partial search করার জন্য।

---

## Quick Summary

• LIKE = pattern matching  
• % = many characters  
• _ = single character  
• Starts, ends, contains search করা যায়  
• Text filtering এর জন্য খুব important  

---

👉 মনে রাখার Shortcut
```sql
LIKE 'A%' → starts with A

LIKE '%A' → ends with A

LIKE '%A%' → contains A

LIKE '_' → one character

```
---
</details>


<details>
  <summary><b>IN </b></summary>

# IN Operator in SQL

IN operator ব্যবহার করা হয় multiple possible values এর মধ্যে match করার জন্য।

👉 সহজভাবে:
IN = একাধিক value একসাথে check করা (OR এর shortcut)  

---

## Basic Syntax
```sql
SELECT column_name
FROM table_name
WHERE column_name IN (value1, value2, value3);

```
---

## Example Table: Students

| StudentID | Name  | Department | CGPA |
|------------|------|------------|------|
| 101 | Rahim | CSE | 3.90 |
| 102 | Karim | EEE | 3.75 |
| 103 | Sakib | CSE | 3.85 |
| 104 | Nayeem | BBA | 3.60 |
| 105 | Arafat | CSE | 3.95 |

---

## 1. IN Operator Basic Example

👉 CSE এবং EEE students দরকার
```sql
SELECT *
FROM Students
WHERE Department IN ('CSE', 'EEE');

```
---

## Query

---

## Output:

| Name  | Department |
|------|------------|
| Rahim | CSE |
| Karim | EEE |
| Sakib | CSE |
| Arafat | CSE |

---

👉 একই কাজ OR দিয়ে করলে অনেক বড় query হতো

---

## IN vs OR
```sql
WHERE Department = 'CSE'
OR Department = 'EEE'

```
---

👉 IN সহজ এবং clean

---

## 2. IN with Numbers
```sql
SELECT *
FROM Students
WHERE StudentID IN (101, 103, 105);

```
---

👉 specific students select করা

---

## 3. IN with NOT
```sql
SELECT *
FROM Students
WHERE Department NOT IN ('CSE', 'EEE');

```
---

## Output:

| Name  | Department |
|------|------------|
| Nayeem | BBA |

---

👉 CSE এবং EEE বাদ

---

## 4. IN with Subquery (Important Concept)

👉 অন্য table থেকে value নিয়ে match করা

---

## Example:
```sql
SELECT *
FROM Students
WHERE Department IN (
    SELECT Department
    FROM Departments
);

```
---

👉 dynamic matching (advanced use)

---

## Real-Life Example (IN)

👉 scholarship eligible departments

```sql
SELECT *
FROM Students
WHERE Department IN ('CSE', 'SWE', 'EEE');

```
---
</details>
