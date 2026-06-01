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