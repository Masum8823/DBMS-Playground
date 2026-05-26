<details>
    <summary><b>Table, Row, Column</b></summary>
    
# Table, Row, Column in DBMS

Relational Database এ data মূলত table আকারে store করা হয়। এই table এর ভিতরে row এবং column থাকে।

👉 সহজভাবে:

- Table = full data container  
- Row = single record  
- Column = single attribute/type of data  

---

## Table (টেবিল কী?)

Table হলো related data এর collection, যেখানে data rows এবং columns আকারে organized থাকে।

👉 সহজভাবে:
Table = database এর একটা organized sheet  

#### Example:

Student Table

| ID  | Name  | Department | CGPA |
|-----|------|------------|------|
| 101 | Rahim | CSE        | 3.90 |
| 102 | Karim | EEE        | 3.75 |

👉 এই পুরো structure টা হলো table  


### Features of Table:

- প্রতিটা table এর একটা unique name থাকে  
- Related data store করে  
- Rows এবং columns নিয়ে তৈরি  
- Database এ multiple tables থাকতে পারে  


#### Real-life Example:

Excel sheet এর মতো ভাবতে পারো  

👉 যেমন:

- Student Table  
- Teacher Table  
- Course Table  

---

## Row (Tuple / Record)

Row হলো table এর horizontal part, যেখানে একটি complete record থাকে।

👉 সহজভাবে:
One row = one full entity information  


#### Example:

| ID  | Name  | Department | CGPA |
|-----|------|------------|------|
| 101 | Rahim | CSE        | 3.90 |

👉 এই পুরো line টা একটি row  

### Features of Row:

- One row represents one record  
- Horizontal ভাবে থাকে  
- Table এ multiple rows থাকতে পারে  
- প্রতিটা row usually unique হয়  


#### Real-life Example:

একজন student এর সব information = one row  

---

## Column (Attribute / Field)

Column হলো table এর vertical part, যেটা specific type of information store করে।

👉 সহজভাবে:
Column = category/type of data  

#### Example Columns:

- ID  
- Name  
- Department  
- CGPA  


### Features of Column:

- Similar type data store করে  
- প্রতিটা column এর একটা name থাকে  
- Data type define করা থাকে  

📌 Example:

- ID → Integer  
- Name → VARCHAR  
- CGPA → FLOAT  


#### Real-life Example:

“Name” column এ সব students এর নাম থাকবে  

---

## Relationship Between Table, Row & Column

একটা table rows এবং columns নিয়ে তৈরি হয়।

📌 Formula:
Table = Rows + Columns  

### Visualization:

| ID  | Name  | CGPA |
|-----|------|------|
| 101 | Rahim | 3.90 |
| 102 | Karim | 3.75 |

👉 এখানে:

- পুরো structure = Table  
- Horizontal line = Row  
- Vertical category = Column  


### Important Terms

| Term  | Another Name |
|------|-------------|
| Row   | Tuple / Record |
| Column | Attribute / Field |
| Table | Relation |

---

### Quick Summary

| Concept | Meaning |
|--------|--------|
| Table | Collection of related data |
| Row | Single record |
| Column | Single attribute/category |


👉 সহজভাবে:

- Table = পুরো sheet  
- Row = একজনের data  
- Column = এক ধরনের information  

---

</details>


<details>
    <summary><b>Relationship Types</b></summary>

# Relationship Types in DBMS

Database এ relationship ব্যবহার করা হয় এক table এর data এর সাথে অন্য table এর data connect করার জন্য।

👉 সহজভাবে:
Relationship = tables এর মধ্যে connection  


### Why Relationship is Important?

Real-world system এ সব data এক table এ রাখা possible না। তাই multiple tables তৈরি করা হয় এবং relationship দিয়ে connect করা হয়।

📌 Example:

- Student table  
- Course table  
- Teacher table  

👉 এগুলোর মধ্যে relation তৈরি করতে হয়  

---

## One-to-One Relationship (1:1)

এখানে একটি record শুধুমাত্র অন্য table এর একটি record এর সাথে related থাকে।

👉 সহজভাবে:
One record ↔ One record  


#### Example:

##### Person Table

| PersonID | Name  |
|----------|------|
| 1        | Rahim |

##### Passport Table

| PassportID | PersonID |
|-----------|----------|
| P101      | 1        |

👉 একজন person এর একটি passport  
👉 একটি passport শুধুমাত্র একজন person এর  

#### Features:

- Rarely used  
- High security data আলাদা রাখতে use হয়  

#### Real-life Example:

- Person ↔ Passport  
- Student ↔ Student ID Card  

---

## One-to-Many Relationship (1:M)

এখানে একটি record অন্য table এর multiple records এর সাথে related থাকে।

👉 সহজভাবে:
One parent → many children  


#### Example:

##### Department Table

| DeptID | Department |
|--------|-----------|
| 1      | CSE       |

##### Student Table

| StudentID | Name  | DeptID |
|----------|------|--------|
| 101      | Rahim | 1      |
| 102      | Karim | 1      |

👉 একটি department এ অনেক student থাকতে পারে  
👉 কিন্তু একজন student শুধুমাত্র একটি department এ belongs করে  


#### Features:

- Most common relationship  
- Foreign key ব্যবহার হয়  


#### Real-life Example:

- One teacher → many students  
- One customer → many orders  

---

## Many-to-Many Relationship (M:N)

এখানে multiple records অন্য table এর multiple records এর সাথে related থাকে।

👉 সহজভাবে:
Many ↔ Many  

#### Example:

##### Student Table

| StudentID | Name  |
|----------|------|
| 101      | Rahim |

##### Course Table

| CourseID | Course |
|----------|-------|
| CSE101   | DBMS  |

👉 একজন student অনেক course নিতে পারে  
👉 একটি course অনেক student নিতে পারে  

#### Important Note:

Many-to-Many relationship directly implement করা যায় না।  
এটার জন্য extra junction table/use table তৈরি করতে হয়।

📌 Example:
Enrollment Table(StudentID, CourseID)


#### Real-life Example:

- Students ↔ Courses  
- Actors ↔ Movies  

---

## Quick Comparison

| Relationship | Meaning |
|-------------|--------|
| One-to-One | One record ↔ One record |
| One-to-Many | One record ↔ Many records |
| Many-to-Many | Many records ↔ Many records |


### Visualization

#### One-to-One
Person → Passport  

#### One-to-Many
Department → Students  

#### Many-to-Many
Students ↔ Courses  


👉 সহজভাবে:

- 1:1 = one ↔ one  
- 1:M = one ↔ many  
- M:N = many ↔ many  

---

</details>
