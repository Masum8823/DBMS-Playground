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



<details>
    <summary><b>Constraints</b></summary>
    
# Constraints in DBMS

Constraints হলো rules, যেগুলো database table এর data control করে যাতে wrong বা invalid data insert না হয়।

👉 সহজভাবে:
Constraint = data validity rules  

---

## NOT NULL Constraint

NOT NULL মানে কোনো column এ NULL (empty) value রাখা যাবে না।

📌 Example:
Name column NOT NULL হলে নাম অবশ্যই দিতে হবে  

| ID | Name  |
|----|------|
| 1  | Rahim |

❌ Invalid:
| 2  | NULL |

👉 সহজভাবে:
NOT NULL = value must be present  

---

## UNIQUE Constraint

UNIQUE মানে একই value column এ repeat হতে পারবে না।

📌 Example:
Email column UNIQUE  

| ID | Email        |
|----|-------------|
| 1  | a@gmail.com |
| 2  | b@gmail.com |

❌ Invalid:
Same email দুইবার রাখা যাবে না  

👉 সহজভাবে:
UNIQUE = no duplicate values  

---

## PRIMARY KEY Constraint

PRIMARY KEY হলো NOT NULL + UNIQUE combination, যেটা table এর প্রতিটা row uniquely identify করে।

📌 Example:
StudentID primary key  

| StudentID | Name  |
|----------|------|
| 101      | Rahim |


#### Rules:

- NULL allowed না  
- Duplicate allowed না  
- One table এ only one primary key  

👉 সহজভাবে:
PRIMARY KEY = main unique identifier  

---

## FOREIGN KEY Constraint

FOREIGN KEY হলো এমন key, যেটা অন্য table এর PRIMARY KEY কে reference করে।

📌 Example:

Student Table:
- StudentID (Primary Key)

Result Table:
- StudentID (Foreign Key)

👉 সহজভাবে:
FOREIGN KEY = table linking key  

---

## CHECK Constraint

CHECK মানে কোনো column এ নির্দিষ্ট condition follow করতে হবে।

📌 Example:
Age >= 18  

| ID | Age |
|----|----|
| 1  | 20 |

❌ Invalid:
Age = 15 (if condition is age >= 18)  

👉 সহজভাবে:
CHECK = condition-based rule  

---

## DEFAULT Constraint

DEFAULT মানে যদি কোনো value insert না করা হয়, তাহলে automatic predefined value বসে যাবে।

📌 Example:
City DEFAULT "Dhaka"  

| ID | City  |
|----|------|
| 1  | Dhaka |

👉 সহজভাবে:
DEFAULT = auto value set if empty  

---

### Quick Summary

| Constraint | Meaning |
|------------|--------|
| NOT NULL | value must be given |
| UNIQUE | no duplicate value |
| PRIMARY KEY | main identity (unique + not null) |
| FOREIGN KEY | links two tables |
| CHECK | condition rule |
| DEFAULT | auto value |


👉 সহজভাবে:

- NOT NULL = must fill  
- UNIQUE = no repeat  
- PRIMARY KEY = main identity  
- FOREIGN KEY = relationship  
- CHECK = condition rule  
- DEFAULT = auto value  

---

</details>


<details>
    <summary><b>ER Diagram (Entity Relationship Diagram)</b></summary>
    
# ER Diagram (Entity Relationship Diagram)

ER Diagram (Entity Relationship Diagram) হলো database design করার graphical representation, যেখানে entities, attributes এবং relationships visually দেখানো হয়।

👉 সহজভাবে:
ER Diagram = database এর blueprint/visual design  


### Why ER Diagram is Used?

Database তৈরি করার আগে system planning করার জন্য ER Diagram ব্যবহার করা হয়।

এটার মাধ্যমে সহজে বোঝা যায়:

- কোন entity থাকবে  
- কোন attribute থাকবে  
- কোন entity এর সাথে কোন entity এর relationship আছে  

---

## Main Components of ER Diagram

ER Diagram এর 3টা প্রধান অংশ আছে:

- Entity  
- Attribute  
- Relationship  


## Entity (এনটিটি কী?)

Entity হলো real-world object বা thing, যেটার data database এ store করা হয়।

👉 সহজভাবে:
Entity = object about which data is stored  


#### Examples:

- Student  
- Teacher  
- Course  
- Department  

#### Representation:

Entity rectangle shape দিয়ে দেখানো হয়।

📌 Example:

[ Student ]


### Types of Entity

#### 1. Strong Entity

যে entity নিজের primary key দিয়ে uniquely identify হতে পারে।

📌 Example:
Student(StudentID, Name)

👉 StudentID দিয়ে student identify করা যায়  


#### 2. Weak Entity

যে entity নিজের key ছাড়া uniquely identify হতে পারে না এবং অন্য entity এর উপর depend করে।

📌 Example:
Dependent entity  

---

## Attribute (অ্যাট্রিবিউট কী?)

Attribute হলো entity এর properties বা characteristics।

👉 সহজভাবে:
Attribute = entity এর information/details  


#### Example:

Student entity এর attributes:

- StudentID  
- Name  
- CGPA  
- Department  

#### Representation:

Attribute oval/ellipse shape দিয়ে দেখানো হয়।

📌 Example:

(Student) — Name  


### Types of Attributes

#### 1. Simple Attribute

আর ভাঙা যায় না।

📌 Example:
Age, Gender  

#### 2. Composite Attribute

ছোট ছোট অংশে ভাগ করা যায়।

📌 Example:
Name → First Name + Last Name  

#### 3. Single-valued Attribute

এক entity এর জন্য একটাই value থাকে।

📌 Example:
StudentID  


#### 4. Multi-valued Attribute

এক entity এর multiple values থাকতে পারে।

📌 Example:
Phone Numbers  


#### 5. Derived Attribute

অন্য attribute থেকে calculate করা যায়।

📌 Example:
Age from Date of Birth  

---

## Relationship (রিলেশনশিপ কী?)

Relationship হলো entities এর মধ্যে connection।

👉 সহজভাবে:
Relationship = entity connection  

#### Example:

Student enrolls in Course  

👉 এখানে:
Student ↔ Course connected  

#### Representation:

Diamond shape দিয়ে relationship দেখানো হয়।

📌 Example:

[Student] ◇ Enrolls ◇ [Course]


### Types of Relationship

#### 1. One-to-One (1:1)

One entity ↔ One entity  

📌 Example:
Person ↔ Passport  


#### 2. One-to-Many (1:M)

One entity ↔ Many entities  

📌 Example:
Department ↔ Students  


#### 3. Many-to-Many (M:N)

Many entities ↔ Many entities  

📌 Example:
Students ↔ Courses  

---

### Primary Key in ER Diagram

Primary Key entity কে uniquely identify করে।

ER Diagram এ primary key সাধারণত underline করা হয়।

📌 Example:
StudentID  

---

### Example of Complete ER Concept

Scenario:
A student enrolls in a course  


#### Entities:

- Student  
- Course  

#### Relationship:

- Enrolls  

#### Attributes:

Student:
- StudentID  
- Name  

Course:
- CourseID  
- CourseName  


### Simple Visualization:

(Student)  
   |  
 Enrolls  
   |  
(Course)  

---

### Advantages of ER Diagram

- Database planning easy হয়  
- Relationship clearly বোঝা যায়  
- Developers এবং designers এর communication easy হয়  
- Database errors কমে যায়  


### Disadvantages of ER Diagram

- Large system এ diagram complex হয়ে যায়  
- Time consuming  
- Technical knowledge দরকার হয়  

---

### Quick Summary

| Component | Meaning |
|----------|--------|
| Entity | Real-world object |
| Attribute | Entity information |
| Relationship | Connection between entities |


👉 সহজভাবে:

- Entity = object  
- Attribute = details  
- Relationship = connection  
 
---

</details>



<details>
    <summary><b>Weak Entity & Strong Entity</b></summary>
    
# Strong Entity & Weak Entity

DBMS এ Entity দুই ধরনের হয়: Strong Entity এবং Weak Entity। এগুলো বুঝতে হলে আগে entity identification concept clear হতে হবে।

👉 সহজভাবে:

- Strong Entity = নিজে নিজে identify হতে পারে  
- Weak Entity = অন্য entity ছাড়া identify হতে পারে না  

---

## Strong Entity (স্ট্রং এনটিটি)

Strong Entity হলো এমন entity যেটা নিজের primary key দিয়ে uniquely identify করা যায়।

👉 সহজভাবে:
Strong Entity = independent entity (self-sufficient)


### Features:

- নিজস্ব Primary Key থাকে  
- অন্য entity এর উপর depend করে না  
- Exist করার জন্য অন্য entity দরকার হয় না  
- ER Diagram এ single rectangle দিয়ে দেখানো হয়  

#### Example:

Student Entity

| StudentID | Name  | CGPA |
|----------|------|------|
| 101      | Rahim | 3.90 |

👉 এখানে StudentID নিজেই uniquely identify করে  
👉 তাই Student = Strong Entity  


#### Another Examples:

- Teacher  
- Course  
- Department  

👉 সহজভাবে:
Strong Entity = independent + has primary key  

---

## Weak Entity (উইক এনটিটি)

Weak Entity হলো এমন entity যেটা নিজের কোনো primary key দিয়ে uniquely identify করতে পারে না। এটাকে identify করার জন্য অন্য (Strong Entity) এর primary key লাগে।

👉 সহজভাবে:
Weak Entity = dependent entity  


### Features:

- নিজস্ব primary key থাকে না  
- Partial key থাকতে পারে  
- Strong Entity এর উপর depend করে  
- ER Diagram এ double rectangle দিয়ে দেখানো হয়  
- Identifying relationship থাকে  


#### Example:

### Employee (Strong Entity)

| EmpID | Name  |
|------|------|
| 1    | Rahim |


### Dependent (Weak Entity)

| DependentName | Age |
|--------------|-----|
| Rima         | 10  |

👉 এখানে Dependent নিজে uniquely identify হতে পারে না  
👉 EmpID লাগবে identify করার জন্য  

📌 Final Key:
(Employee EmpID + DependentName)

#### Another Examples:

- Order → Order Items  
- Student → Attendance Record  
- Room → Seat  

---

### Identifying Relationship

Weak Entity এবং Strong Entity এর মধ্যে যে relationship থাকে তাকে identifying relationship বলে।

👉 ER Diagram এ এটা সাধারণত double diamond দিয়ে দেখানো হয়।

📌 Example:
[Employee] ◇◇ Has ◇◇ [Dependent]

---

### Partial Key (Discriminator)

Weak Entity এর মধ্যে যে attribute partial uniqueness দেয় তাকে partial key বলে।

📌 Example:
DependentName  
(same name multiple employees এ থাকতে পারে)

---

### Strong vs Weak Entity Difference

| Strong Entity | Weak Entity |
|--------------|------------|
| Independent entity | Dependent entity |
| Has primary key | No full primary key |
| Can exist alone | Cannot exist alone |
| Single rectangle | Double rectangle |
| Example: Student | Example: Dependent |


#### Real-life Analogy

👉 Strong Entity = Parent (নিজে নিজে exist করতে পারে)  
👉 Weak Entity = Child (Parent ছাড়া identify করা যায় না)  

---

### Quick Summary

- Strong Entity = self-identifiable entity  
- Weak Entity = dependent entity  
- Weak entity needs strong entity’s key  
- Relationship is identifying relationship  

👉 সহজভাবে:

- Strong = independent  
- Weak = dependent  
 
---

</details>



<details>
    <summary><b>Cardinality & Participation</b></summary>
    
# Cardinality & Participation

ER Diagram এ Cardinality এবং Participation খুব important concept, যেগুলো relationship কীভাবে কাজ করবে সেটা define করে।

👉 সহজভাবে:

- Cardinality = “কতগুলো entity related হতে পারে”  
- Participation = “সব entity বাধ্যতামূলকভাবে participate করবে কিনা”  

---

## Cardinality (কার্ডিনালিটি)

Cardinality বলে দেয় একটি entity কতগুলো অন্য entity এর সাথে relate করতে পারে।

👉 সহজভাবে:
Cardinality = relationship quantity rule  


## Types of Cardinality

### 1. One-to-One (1:1)

একটি entity আরেকটি entity এর শুধু একটি entity এর সাথে related থাকে।

📌 Example:
Person ↔ Passport  

| Person | Passport |
|-------|----------|
| 1     | 1        |

👉 একজন person এর একটি passport  

### 2. One-to-Many (1:M)

একটি entity অনেকগুলো entity এর সাথে related হতে পারে।

📌 Example:
Department → Students  

| Department | Students |
|------------|----------|
| 1          | Many     |

👉 এক department এ অনেক student  

### 3. Many-to-Many (M:N)

একাধিক entity একাধিক entity এর সাথে related হতে পারে।

📌 Example:
Students ↔ Courses  

| Students | Courses |
|----------|--------|
| Many     | Many   |

👉 এক student অনেক course নিতে পারে, আবার এক course এ অনেক student থাকতে পারে  

---

## Participation (পার্টিসিপেশন)

Participation বলে দেয় কোনো entity relationship এ বাধ্যতামূলকভাবে অংশ নেবে কিনা।

👉 সহজভাবে:
Participation = mandatory participation rule  


## Types of Participation


### 1. Total Participation (Mandatory)

এখানে প্রতিটি entity অবশ্যই relationship এ অংশ নেবে।

📌 Example:
Every student must be enrolled in at least one course  

👉 এখানে participation বাধ্যতামূলক  

📌 ER Diagram representation:
Double line দিয়ে দেখানো হয়  



### 2. Partial Participation (Optional)

এখানে কিছু entity relationship এ অংশ নাও নিতে পারে।

📌 Example:
Not all employees manage a department  

👉 কিছু employee participate নাও করতে পারে  

📌 ER Diagram representation:
Single line দিয়ে দেখানো হয়  

---

## Cardinality vs Participation Difference

| Cardinality | Participation |
|------------|--------------|
| কতগুলো relation হবে | অংশগ্রহণ বাধ্যতামূলক কিনা |
| Quantity define করে | Existence rule define করে |
| 1:1, 1:M, M:N | Total / Partial |


#### Real-life Example

University System:

- Student → Course (M:N cardinality)  
- Every Student must have ID (Total participation)  
- Employee may or may not manage department (Partial participation)  

---

### Quick Summary

- Cardinality = “how many”  
- Participation = “must or optional”  


👉 সহজভাবে:

- Cardinality = number rule  
- Participation = obligation rule  
 
---

</details>