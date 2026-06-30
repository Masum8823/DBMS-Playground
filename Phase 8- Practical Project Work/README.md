<h1 align="center">Practical Project Work</h1>

> ### Explore each topic to understand the core concepts in detail
<p align="center">
  ⬇<b> Click any section below to expand </b> ⬇
</p>

<details>
    <summary><b>Student Management System DB</b></summary>

# 🎓 Student Management System (SMS)

A complete **Database Management System** project for managing student records, courses, teachers, attendance, and results — built using core DBMS concepts including ER Diagrams, Relational Schema, Normalization, Joins, and SQL Queries.

> **University:** Northern University Bangladesh (NUB)

---
## 📌 Table of Contents

- [Project Overview](#project-overview)
- [System Modules](#system-modules)
- [Requirements Analysis](#requirements-analysis)
- [ER Diagram (Conceptual)](#er-diagram-conceptual)
- [Relational Schema](#relational-schema)
- [Database Implementation](#database-implementation)
- [Sample Data](#sample-data)
- [Useful Queries](#useful-queries)
- [Normalization](#normalization)
- [Viva Q&A](#viva-qa)

---
## 📖 Project Overview

The **Student Management System** is one of the most popular academic DBMS projects, covering nearly every core database concept. It handles:

| Module | Description |
|---|---|
| Student Registration | Student records with department assignment |
| Teacher Management | Faculty info linked to departments |
| Department Management | Academic department structure |
| Course Management | Course details with assigned teacher |
| Enrollment Management | Student-course registration per semester |
| Attendance Management | Daily attendance per course |
| Result Management | Grade recording and reporting |

---
## 🗂️ System Modules

### 🔐 Admin Module
- Add, Update, Delete Students
- Manage Courses

### 👨‍🏫 Teacher Module
- Take Attendance
- Submit Marks
- View Students

### 🎓 Student Module
- View Profile
- View Attendance
- View Results

---
## 📋 Requirements Analysis

### Entities & Attributes

<details>
<summary><strong>Student</strong></summary>

- `StudentID` (PK)
- `Name`
- `Email`
- `Phone`
- `Address`
- `DepartmentID` (FK)

</details>

<details>
<summary><strong>Department</strong></summary>

- `DepartmentID` (PK)
- `DepartmentName`

</details>

<details>
<summary><strong>Teacher</strong></summary>

- `TeacherID` (PK)
- `Name`
- `Email`
- `Designation`
- `DepartmentID` (FK)

</details>

<details>
<summary><strong>Course</strong></summary>

- `CourseID` (PK)
- `CourseName`
- `Credit`
- `TeacherID` (FK)

</details>

<details>
<summary><strong>Enrollment</strong></summary>

- `EnrollmentID` (PK)
- `StudentID` (FK)
- `CourseID` (FK)
- `Semester`

</details>

<details>
<summary><strong>Attendance</strong></summary>

- `AttendanceID` (PK)
- `StudentID` (FK)
- `CourseID` (FK)
- `Date`
- `Status`

</details>

<details>
<summary><strong>Result</strong></summary>

- `ResultID` (PK)
- `StudentID` (FK)
- `CourseID` (FK)
- `Grade`

</details>

---
## 🔗 Relationship Analysis

| Relationship | Type | Notes |
|---|---|---|
| Department → Student | One-to-Many | A department has many students |
| Department → Teacher | One-to-Many | A department has many teachers |
| Teacher → Course | One-to-Many | A teacher teaches many courses |
| Student ↔ Course | Many-to-Many | Resolved via `Enrollment` table |

---
## 📊 ER Diagram (Conceptual)

```
Department ──1────M── Student
Department ──1────M── Teacher
Teacher    ──1────M── Course

Student ──M──┐
             ├── Enrollment ──M── Course

Student ──1────M── Attendance
Student ──1────M── Result
```

---
## 🗃️ Relational Schema

```
Department  ( DepartmentID, DepartmentName )

Student     ( StudentID, Name, Email, Phone, Address, DepartmentID* )

Teacher     ( TeacherID, Name, Email, Designation, DepartmentID* )

Course      ( CourseID, CourseName, Credit, TeacherID* )

Enrollment  ( EnrollmentID, StudentID*, CourseID*, Semester )

Attendance  ( AttendanceID, StudentID*, CourseID*, Date, Status )

Result      ( ResultID, StudentID*, CourseID*, Grade )
```
> `*` = Foreign Key

---
## 💻 Database Implementation

### Create & Use Database

```sql
CREATE DATABASE StudentManagementDB;

USE StudentManagementDB;
```

### Department Table

```sql
CREATE TABLE Department (
    DepartmentID   INT PRIMARY KEY,
    DepartmentName VARCHAR(50)
);
```

### Student Table

```sql
CREATE TABLE Student (
    StudentID    INT PRIMARY KEY,
    Name         VARCHAR(100),
    Email        VARCHAR(100),
    Phone        VARCHAR(20),
    Address      VARCHAR(200),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID)
);
```

### Teacher Table

```sql
CREATE TABLE Teacher (
    TeacherID    INT PRIMARY KEY,
    Name         VARCHAR(100),
    Email        VARCHAR(100),
    Designation  VARCHAR(50),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID)
);
```

### Course Table

```sql
CREATE TABLE Course (
    CourseID   INT PRIMARY KEY,
    CourseName VARCHAR(100),
    Credit     INT,
    TeacherID  INT,
    FOREIGN KEY (TeacherID) REFERENCES Teacher(TeacherID)
);
```

### Enrollment Table

```sql
CREATE TABLE Enrollment (
    EnrollmentID INT PRIMARY KEY,
    StudentID    INT,
    CourseID     INT,
    Semester     VARCHAR(20),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (CourseID)  REFERENCES Course(CourseID)
);
```

### Attendance Table

```sql
CREATE TABLE Attendance (
    AttendanceID INT PRIMARY KEY,
    StudentID    INT,
    CourseID     INT,
    Date         DATE,
    Status       VARCHAR(10),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (CourseID)  REFERENCES Course(CourseID)
);
```

### Result Table

```sql
CREATE TABLE Result (
    ResultID  INT PRIMARY KEY,
    StudentID INT,
    CourseID  INT,
    Grade     VARCHAR(5),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (CourseID)  REFERENCES Course(CourseID)
);
```

---
## 🧪 Sample Data

```sql
-- Departments
INSERT INTO Department VALUES
(1, 'CSE'),
(2, 'EEE'),
(3, 'BBA');

-- Students
INSERT INTO Student VALUES
(101, 'Rahim', 'rahim@gmail.com', '01711111111', 'Dhaka',  1),
(102, 'Karim', 'karim@gmail.com', '01822222222', 'Khulna', 1);

-- Teacher
INSERT INTO Teacher VALUES
(1, 'Dr. Hasan', 'hasan@gmail.com', 'Professor', 1);

-- Course
INSERT INTO Course VALUES
(101, 'Database Systems', 3, 1);
```

---
## 🔍 Useful Queries

### Show All Students
```sql
SELECT * FROM Student;
```

### Show CSE Students
```sql
SELECT * FROM Student
WHERE DepartmentID = 1;
```

### Students with Department Name
```sql
SELECT s.Name, d.DepartmentName
FROM Student s
INNER JOIN Department d ON s.DepartmentID = d.DepartmentID;
```

### Course with Teacher Name
```sql
SELECT c.CourseName, t.Name AS TeacherName
FROM Course c
INNER JOIN Teacher t ON c.TeacherID = t.TeacherID;
```

### Enrollment Report
```sql
SELECT s.Name, c.CourseName
FROM Enrollment e
INNER JOIN Student s ON e.StudentID = s.StudentID
INNER JOIN Course  c ON e.CourseID  = c.CourseID;
```

### Result Report
```sql
SELECT s.Name, c.CourseName, r.Grade
FROM Result r
INNER JOIN Student s ON r.StudentID = s.StudentID
INNER JOIN Course  c ON r.CourseID  = c.CourseID;
```

### Attendance Report
```sql
SELECT StudentID, CourseID, Date, Status
FROM Attendance;
```

---
## 📐 Normalization

| Normal Form | Condition Met |
|---|---|
| **1NF** | ✅ No repeating groups — all attributes are atomic |
| **2NF** | ✅ No partial dependencies |
| **3NF** | ✅ No transitive dependencies |

> This database design is normalized up to **3NF**.

---
## ❓ Viva Q&A

**Q: Student Management System-এর main entities কী?**  
→ `Student`, `Teacher`, `Department`, `Course`, `Enrollment`, `Attendance`, `Result`

**Q: Student এবং Course-এর relationship কী?**  
→ Many-to-Many

**Q: Many-to-Many relationship কীভাবে solve করা হয়েছে?**  
→ `Enrollment` table ব্যবহার করে bridge/junction table হিসেবে

**Q: Department এবং Student relationship কী?**  
→ One-to-Many — একটি Department-এ অনেক Student থাকতে পারে

**Q: Enrollment table কেন প্রয়োজন?**  
→ Student এবং Course-এর Many-to-Many relationship manage করার জন্য

---

## 🛠️ Tech Stack

![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-025E8C?style=for-the-badge&logo=databricks&logoColor=white)

---

## 👤 Author

**Masum** — [@Masum8823](https://github.com/Masum8823)
---

</details>


<details>
    <summary><b>Library Management System DB</b></summary>


---

</details>


<details>
    <summary><b>University Management System DB (UMS)</b></summary>

# 🎓 University Management System (UMS)
 
A complete **Database Management System** project for managing all academic and administrative operations of a university — designed using core DBMS concepts including ER Diagrams, Relational Schema, Normalization, Joins, Views, and more.
 
> **University:** Northern University Bangladesh (NUB)
 
---
## 📌 Table of Contents
 
- [Project Overview](#project-overview)
- [System Modules](#system-modules)
- [Requirements Analysis](#requirements-analysis)
- [ER Diagram (Conceptual)](#er-diagram-conceptual)
- [Relational Schema](#relational-schema)
- [Database Implementation](#database-implementation)
- [Sample Data](#sample-data)
- [Useful Queries](#useful-queries)
- [Normalization](#normalization)
- [Viva Q&A](#viva-qa)
---

## 📖 Project Overview
 
The **University Management System** is one of the most complete academic DBMS projects, covering nearly every core database concept. It handles:
 
| Module | Description |
|---|---|
| Student Management | Student records, department assignment |
| Teacher Management | Faculty info and course assignment |
| Department Management | Academic departments |
| Course Management | Course details with credit and instructor |
| Semester Management | Semester-wise tracking |
| Enrollment Management | Student-course registration per semester |
| Result Management | Grade recording and reporting |
| Attendance Management | Daily attendance per course |
| Fee Management | Semester fee tracking and status |
 
---
## 🗂️ System Modules
 
### 🔐 Admin Module
- Manage Students, Teachers, Courses, Departments, Fees
### 👨‍🏫 Teacher Module
- Attendance Entry
- Marks/Grade Submission
- Student Information View
### 🎓 Student Module
- Course Registration
- View Attendance
- View Results
- View Fee Status
---

## 📋 Requirements Analysis
 
### Entities & Attributes
 
<details>
<summary><strong>Department</strong></summary>

- `DepartmentID` (PK)
- `DepartmentName`

</details>
<details>
<summary><strong>Student</strong></summary>

- `StudentID` (PK)
- `Name`
- `Email`
- `Phone`
- `Address`
- `DepartmentID` (FK)
</details>
<details>
<summary><strong>Teacher</strong></summary>

- `TeacherID` (PK)
- `Name`
- `Email`
- `Designation`
- `DepartmentID` (FK)
</details>
<details>
<summary><strong>Course</strong></summary>

- `CourseID` (PK)
- `CourseName`
- `Credit`
- `DepartmentID` (FK)
- `TeacherID` (FK)
</details>
<details>
<summary><strong>Semester</strong></summary>

- `SemesterID` (PK)
- `SemesterName`
</details>
<details>
<summary><strong>Enrollment</strong></summary>

- `EnrollmentID` (PK)
- `StudentID` (FK)
- `CourseID` (FK)
- `SemesterID` (FK)
</details>
<details>
<summary><strong>Attendance</strong></summary>

- `AttendanceID` (PK)
- `StudentID` (FK)
- `CourseID` (FK)
- `Date`
- `Status`
</details>
<details>
<summary><strong>Result</strong></summary>

- `ResultID` (PK)
- `StudentID` (FK)
- `CourseID` (FK)
- `Grade`
</details>
<details>
<summary><strong>Fees</strong></summary>

- `FeeID` (PK)
- `StudentID` (FK)
- `SemesterID` (FK)
- `Amount`
- `Status`
</details>

---

## 🔗 Relationship Analysis
 
| Relationship | Type | Notes |
|---|---|---|
| Department → Student | One-to-Many | A department has many students |
| Department → Teacher | One-to-Many | A department has many teachers |
| Department → Course | One-to-Many | A department offers many courses |
| Teacher → Course | One-to-Many | A teacher teaches many courses |
| Student ↔ Course | Many-to-Many | Resolved via `Enrollment` table |
| Student → Fees | One-to-Many | A student has many fee records |
| Semester → Enrollment | One-to-Many | A semester has many enrollments |
 
---
## 📊 ER Diagram (Conceptual)
 
```
Department ──1────M── Student
Department ──1────M── Teacher
Department ──1────M── Course
Teacher    ──1────M── Course
 
Student ──M──┐
             ├── Enrollment ──M── Course
Semester──1──┘
 
Student ──1────M── Attendance
Student ──1────M── Result
Student ──1────M── Fees
```
 
---

## 🗃️ Relational Schema
 
```
Department  ( DepartmentID, DepartmentName )
 
Student     ( StudentID, Name, Email, Phone, Address, DepartmentID* )
 
Teacher     ( TeacherID, Name, Email, Designation, DepartmentID* )
 
Course      ( CourseID, CourseName, Credit, DepartmentID*, TeacherID* )
 
Semester    ( SemesterID, SemesterName )
 
Enrollment  ( EnrollmentID, StudentID*, CourseID*, SemesterID* )
 
Attendance  ( AttendanceID, StudentID*, CourseID*, Date, Status )
 
Result      ( ResultID, StudentID*, CourseID*, Grade )
 
Fees        ( FeeID, StudentID*, SemesterID*, Amount, Status )
```
> `*` = Foreign Key
 
---

## 💻 Database Implementation
 
### Create & Use Database
 
```sql
CREATE DATABASE UniversityManagementDB;
 
USE UniversityManagementDB;
```
 
### Department Table
 
```sql
CREATE TABLE Department (
    DepartmentID   INT PRIMARY KEY,
    DepartmentName VARCHAR(100)
);
```
 
### Student Table
 
```sql
CREATE TABLE Student (
    StudentID    INT PRIMARY KEY,
    Name         VARCHAR(100),
    Email        VARCHAR(100),
    Phone        VARCHAR(20),
    Address      VARCHAR(200),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID)
);
```
 
### Teacher Table
 
```sql
CREATE TABLE Teacher (
    TeacherID    INT PRIMARY KEY,
    Name         VARCHAR(100),
    Email        VARCHAR(100),
    Designation  VARCHAR(50),
    DepartmentID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID)
);
```
 
### Course Table
 
```sql
CREATE TABLE Course (
    CourseID     INT PRIMARY KEY,
    CourseName   VARCHAR(100),
    Credit       INT,
    DepartmentID INT,
    TeacherID    INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID),
    FOREIGN KEY (TeacherID)    REFERENCES Teacher(TeacherID)
);
```
 
### Semester Table
 
```sql
CREATE TABLE Semester (
    SemesterID   INT PRIMARY KEY,
    SemesterName VARCHAR(50)
);
```
 
### Enrollment Table
 
```sql
CREATE TABLE Enrollment (
    EnrollmentID INT PRIMARY KEY,
    StudentID    INT,
    CourseID     INT,
    SemesterID   INT,
    FOREIGN KEY (StudentID)   REFERENCES Student(StudentID),
    FOREIGN KEY (CourseID)    REFERENCES Course(CourseID),
    FOREIGN KEY (SemesterID)  REFERENCES Semester(SemesterID)
);
```
 
### Attendance Table
 
```sql
CREATE TABLE Attendance (
    AttendanceID INT PRIMARY KEY,
    StudentID    INT,
    CourseID     INT,
    Date         DATE,
    Status       VARCHAR(10),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (CourseID)  REFERENCES Course(CourseID)
);
```
 
### Result Table
 
```sql
CREATE TABLE Result (
    ResultID  INT PRIMARY KEY,
    StudentID INT,
    CourseID  INT,
    Grade     VARCHAR(5),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (CourseID)  REFERENCES Course(CourseID)
);
```
 
### Fees Table
 
```sql
CREATE TABLE Fees (
    FeeID      INT PRIMARY KEY,
    StudentID  INT,
    SemesterID INT,
    Amount     DECIMAL(10,2),
    Status     VARCHAR(20),
    FOREIGN KEY (StudentID)  REFERENCES Student(StudentID),
    FOREIGN KEY (SemesterID) REFERENCES Semester(SemesterID)
);
```
 
---
 
## 🧪 Sample Data
 
```sql
-- Departments
INSERT INTO Department VALUES
(1, 'CSE'),
(2, 'EEE'),
(3, 'BBA');
 
-- Student
INSERT INTO Student VALUES
(2210001, 'Rahim', 'rahim@gmail.com', '01711111111', 'Dhaka', 1);
 
-- Teacher
INSERT INTO Teacher VALUES
(101, 'Dr. Hasan', 'hasan@gmail.com', 'Professor', 1);
 
-- Course
INSERT INTO Course VALUES
(401, 'Database Systems', 3, 1, 101);
 
-- Semester
INSERT INTO Semester VALUES
(1, 'Spring 2026');
```
 
---

## 🔍 Useful Queries
 
### Show All Students
```sql
SELECT * FROM Student;
```
 
### Students with Department Name
```sql
SELECT s.Name, d.DepartmentName
FROM Student s
INNER JOIN Department d ON s.DepartmentID = d.DepartmentID;
```
 
### Course with Teacher Name
```sql
SELECT c.CourseName, t.Name AS TeacherName
FROM Course c
INNER JOIN Teacher t ON c.TeacherID = t.TeacherID;
```
 
### Enrollment Report
```sql
SELECT s.Name, c.CourseName, sem.SemesterName
FROM Enrollment e
INNER JOIN Student  s   ON e.StudentID  = s.StudentID
INNER JOIN Course   c   ON e.CourseID   = c.CourseID
INNER JOIN Semester sem ON e.SemesterID = sem.SemesterID;
```
 
### Result Report
```sql
SELECT s.Name, c.CourseName, r.Grade
FROM Result r
INNER JOIN Student s ON r.StudentID = s.StudentID
INNER JOIN Course  c ON r.CourseID  = c.CourseID;
```
 
### Fee Report
```sql
SELECT s.Name, f.Amount, f.Status
FROM Fees f
INNER JOIN Student s ON f.StudentID = s.StudentID;
```
 
---

## 📐 Normalization
 
| Normal Form | Condition Met |
|---|---|
| **1NF** | ✅ All attributes contain atomic values |
| **2NF** | ✅ No partial dependencies |
| **3NF** | ✅ No transitive dependencies |
 
> This database design is normalized up to **3NF**.
 
---

## ❓ Viva Q&A
 
**Q: University Management System-এর main entities কী?**  
→ `Department`, `Student`, `Teacher`, `Course`, `Semester`, `Enrollment`, `Attendance`, `Result`, `Fees`
 
**Q: Student এবং Course-এর relationship কী?**  
→ Many-to-Many
 
**Q: Many-to-Many relationship কীভাবে solve করা হয়েছে?**  
→ `Enrollment` table ব্যবহার করে bridge/junction table হিসেবে
 
**Q: Fees table কেন ব্যবহার করা হয়?**  
→ Semester-wise fee tracking এবং payment status manage করার জন্য
 
**Q: Department এবং Course relationship কী?**  
→ One-to-Many — একটি Department অনেক Course offer করতে পারে
 
---

## 🛠️ Tech Stack
 
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-025E8C?style=for-the-badge&logo=databricks&logoColor=white)
 
---
 
## 👤 Author
 
**Masum** — [@Masum8823](https://github.com/Masum8823)

</details>


<details>
    <summary><b>CGPA Calculator Database</b></summary>

# 🎓 CGPA Calculator Database

A practical **CGPA Calculator System** database project built with SQL — designed for **Northern University Bangladesh**. This project demonstrates database design, relationships, aggregate functions, views, and academic report generation.

---
## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Grading System](#grading-system)
- [Database Schema](#database-schema)
- [ER Diagram](#er-diagram)
- [Relationships](#relationships)
- [Setup & Usage](#setup--usage)
- [GPA & CGPA Calculation](#gpa--cgpa-calculation)
- [Sample Queries](#sample-queries)
- [Views](#views)
- [Normalization](#normalization)
- [Project Modules](#project-modules)
- [Viva Q&A](#viva-qa)

---
## 🔍 Overview

This system manages complete academic records for university students:

- 👤 Student registration with department and batch info
- 📚 Course and credit hour management
- 📅 Semester-wise grade tracking
- 📊 Automatic GPA calculation per semester
- 🏆 CGPA calculation across all semesters
- 📄 Full academic transcript generation

---

## ✨ Features

| Feature | Description |
|---|---|
| Student Registration | Register students with department & batch |
| Course Management | Manage courses with credit hours |
| Semester Management | Track results semester-wise |
| Grade Entry | Store letter grades and grade points |
| GPA Calculation | Weighted average GPA per semester |
| CGPA Calculation | Overall CGPA across all semesters |
| Transcript Generation | Complete academic result report |

---
## 📊 Grading System

| Letter Grade | Grade Point |
|:---:|:---:|
| A+ | 4.00 |
| A | 3.75 |
| A- | 3.50 |
| B+ | 3.25 |
| B | 3.00 |
| C+ | 2.50 |
| C | 2.25 |
| D | 2.00 |
| F | 0.00 |

---

## 🗄️ Database Schema

### `Student`
```sql
Student(StudentID PK, Name, Department, Batch)
```

### `Semester`
```sql
Semester(SemesterID PK, SemesterName)
```

### `Course`
```sql
Course(CourseID PK, CourseName, Credit)
```

### `Result`
```sql
Result(ResultID PK, StudentID FK, CourseID FK, SemesterID FK, LetterGrade, GradePoint)
```

---
## 📊 ER Diagram

```
Student  (1) ───── (M) Result
Course   (1) ───── (M) Result
Semester (1) ───── (M) Result
```

```
Student
   |
   | 1
   |
   | M
Result ────── M ────── Course
   |
   | M
   |
   | 1
Semester
```

---

## 🔗 Relationships

| Entities | Relationship | Type |
|---|---|---|
| Student → Result | One Student has Many Results | One-to-Many |
| Course → Result | One Course has Many Results | One-to-Many |
| Semester → Result | One Semester has Many Results | One-to-Many |

---
## ⚙️ Setup & Usage

### Step 1 — Create & Use Database
```sql
CREATE DATABASE CGPACalculatorDB;
USE CGPACalculatorDB;
```

### Step 2 — Create Tables
```sql
CREATE TABLE Student (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(100),
    Department VARCHAR(50),
    Batch VARCHAR(20)
);

CREATE TABLE Semester (
    SemesterID INT PRIMARY KEY,
    SemesterName VARCHAR(50)
);

CREATE TABLE Course (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(100),
    Credit DECIMAL(3,1)
);

CREATE TABLE Result (
    ResultID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    SemesterID INT,
    LetterGrade VARCHAR(5),
    GradePoint DECIMAL(3,2),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Course(CourseID),
    FOREIGN KEY (SemesterID) REFERENCES Semester(SemesterID)
);
```

### Step 3 — Insert Sample Data
```sql
INSERT INTO Student VALUES
(2210001, 'Rahim', 'CSE', '57th');

INSERT INTO Semester VALUES
(1, 'Spring 2026');

INSERT INTO Course VALUES
(401, 'Database Systems', 3.0),
(402, 'Operating Systems', 3.0),
(403, 'Computer Networks', 3.0);

INSERT INTO Result VALUES
(1, 2210001, 401, 1, 'A+', 4.00),
(2, 2210001, 402, 1, 'A',  3.75),
(3, 2210001, 403, 1, 'A-', 3.50);
```

---
## 🧮 GPA & CGPA Calculation

### GPA Formula

$$GPA = \frac{\sum(GradePoint \times Credit)}{\sum Credit}$$

### GPA Example

| Course | Credit | Grade Point | Credit × GP |
|---|:---:|:---:|:---:|
| Database Systems | 3 | 4.00 | 12.00 |
| Operating Systems | 3 | 3.75 | 11.25 |
| Computer Networks | 3 | 3.50 | 10.50 |
| **Total** | **9** | — | **33.75** |

```
GPA = 33.75 / 9 = 3.75
```

### Difference: GPA vs CGPA

| | GPA | CGPA |
|---|---|---|
| Scope | One semester | All semesters combined |
| Formula | Same weighted average | Same, but across all results |

---
## 🔎 Sample Queries

### GPA for One Semester
```sql
SELECT
    SUM(r.GradePoint * c.Credit) / SUM(c.Credit) AS GPA
FROM Result r
INNER JOIN Course c ON r.CourseID = c.CourseID
WHERE r.StudentID = 2210001
AND r.SemesterID = 1;
```

### CGPA (All Semesters)
```sql
SELECT
    SUM(r.GradePoint * c.Credit) / SUM(c.Credit) AS CGPA
FROM Result r
INNER JOIN Course c ON r.CourseID = c.CourseID
WHERE r.StudentID = 2210001;
```

### Full Academic Transcript
```sql
SELECT
    s.Name,
    sem.SemesterName,
    c.CourseName,
    c.Credit,
    r.LetterGrade,
    r.GradePoint
FROM Result r
INNER JOIN Student s   ON r.StudentID  = s.StudentID
INNER JOIN Course c    ON r.CourseID   = c.CourseID
INNER JOIN Semester sem ON r.SemesterID = sem.SemesterID;
```

### Student Result Report
```sql
SELECT
    s.Name,
    c.CourseName,
    r.LetterGrade
FROM Result r
INNER JOIN Student s ON r.StudentID = s.StudentID
INNER JOIN Course c  ON r.CourseID  = c.CourseID;
```

### Total Courses Completed
```sql
SELECT COUNT(*) AS TotalCourses
FROM Result
WHERE StudentID = 2210001;
```

### Students with CGPA Above 3.50
```sql
SELECT *
FROM StudentCGPA
WHERE CGPA > 3.50;
```

### Highest CGPA
```sql
SELECT TOP 1 *
FROM StudentCGPA
ORDER BY CGPA DESC;
```

---
## 👁️ Views

### CGPA Report View
```sql
CREATE VIEW StudentCGPA AS
SELECT
    r.StudentID,
    SUM(r.GradePoint * c.Credit) / SUM(c.Credit) AS CGPA
FROM Result r
INNER JOIN Course c ON r.CourseID = c.CourseID
GROUP BY r.StudentID;
```

Usage:
```sql
SELECT * FROM StudentCGPA;
```

---
## 📐 Normalization

This schema is normalized up to **3rd Normal Form (3NF)**:

| Normal Form | Rule Applied |
|---|---|
| **1NF** | All attributes contain atomic (indivisible) values |
| **2NF** | No partial dependencies on composite keys |
| **3NF** | No transitive dependencies between non-key attributes |

---
## 🧩 Project Modules

```
📦 CGPA Calculator System
 ┣ 🔐 Admin Module
 ┃  ┣ Add Students
 ┃  ┣ Add Courses
 ┃  ┗ Manage Semesters
 ┣ 👨‍🏫 Teacher Module
 ┃  ┣ Enter Grades
 ┃  ┗ Update Results
 ┗ 👤 Student Module
    ┣ View GPA
    ┣ View CGPA
    ┗ Download Transcript
```

---
## ❓ Viva Q&A

**Q: GPA এবং CGPA-এর মধ্যে পার্থক্য কী?**
> GPA = One Semester Result | CGPA = Overall Academic Result across all semesters

**Q: GPA কীভাবে calculate করা হয়?**
> `(Grade Point × Credit)` এর weighted average — `SUM(GP × Credit) / SUM(Credit)`

**Q: Result table-এর purpose কী?**
> Student-এর semester-wise grade information store করা; এটি Student, Course এবং Semester-এর junction table

**Q: Course credit কেন দরকার?**
> Weighted GPA/CGPA calculation-এর জন্য — বেশি credit-এর course বেশি impact রাখে

**Q: Transcript কী?**
> Student-এর complete academic result report — সব semester, course, grade একসাথে

**Q: Result table-এ কতটি Foreign Key আছে?**
> তিনটি — StudentID, CourseID, SemesterID

---
## 🚀 Project Flow Summary

```
Student ──┐
          ├──► Result ──► GPA (one semester)
Course ───┤                    │
          │                    ▼
Semester ─┘              All Semesters ──► CGPA
```

---

## 🛠️ Tech Stack

![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-Database-orange?style=for-the-badge)

---

## 📁 Project Structure

```
cgpa-calculator-db/
 ┣ schema.sql          # All CREATE TABLE statements
 ┣ sample_data.sql     # INSERT statements for testing
 ┣ queries.sql         # GPA, CGPA, transcript queries
 ┣ views.sql           # StudentCGPA view
 ┗ README.md           # Project documentation
```

---

## 📄 License

This project is open-source and available for educational purposes.

---
---

</details>


<details>
    <summary><b>Authentication System</b></summary>


---

</details>


<details>
    <summary><b>Full CRUD Project</b></summary>


---

</details>


