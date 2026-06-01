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