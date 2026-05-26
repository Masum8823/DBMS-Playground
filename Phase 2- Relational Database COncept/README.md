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
