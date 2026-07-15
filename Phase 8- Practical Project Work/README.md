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

# 📚 Library Management System (LMS)

A complete **Library Management System** database project built with SQL — designed for **Northern University Bangladesh Central Library**. This project covers all major DBMS concepts including ER Diagram, Normalization, Joins, Views, and Reports.

---
## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Database Schema](#database-schema)
- [ER Diagram](#er-diagram)
- [Relationships](#relationships)
- [Setup & Usage](#setup--usage)
- [Sample Queries](#sample-queries)
- [Normalization](#normalization)
- [Project Modules](#project-modules)
- [Viva Q&A](#viva-qa)

---
## 🔍 Overview

This project simulates a real-world library system where:

- 📖 Books can be catalogued by category
- 👤 Members (students/teachers) can be registered
- 📤 Books can be issued and returned
- 💰 Fines are calculated for late returns
- 🧑‍💼 Librarians are managed separately

---
## ✨ Features

| Feature | Description |
|---|---|
| Book Management | Add, update, and track books by category |
| Member Registration | Register students/teachers as library members |
| Book Issue | Issue books to members with due dates |
| Book Return | Track return dates |
| Fine Calculation | Auto fine for late returns (10 BDT/day) |
| Librarian Management | Manage library admin accounts |
| Reports | Borrowed books, total fines, member history |

---
## 🗄️ Database Schema

### `Category`
```sql
Category(CategoryID PK, CategoryName)
```

### `Book`
```sql
Book(BookID PK, Title, Author, Publisher, CategoryID FK, CopiesAvailable)
```

### `Member`
```sql
Member(MemberID PK, Name, Email, Phone, Department)
```

### `Librarian`
```sql
Librarian(LibrarianID PK, Name, Email, Phone)
```

### `Issue`
```sql
Issue(IssueID PK, BookID FK, MemberID FK, IssueDate, DueDate)
```

### `ReturnBook`
```sql
ReturnBook(ReturnID PK, IssueID FK UNIQUE, ReturnDate)
```

### `Fine`
```sql
Fine(FineID PK, IssueID FK UNIQUE, Amount)
```

---
## 📊 ER Diagram

```
Category (1) ───── (M) Book
Book     (1) ───── (M) Issue
Member   (1) ───── (M) Issue
Issue    (1) ───── (1) ReturnBook
Issue    (1) ───── (1) Fine
```

---

## 🔗 Relationships

| Entities | Relationship | Type |
|---|---|---|
| Category → Book | One Category has Many Books | One-to-Many |
| Member → Issue | One Member has Many Issues | One-to-Many |
| Book → Issue | One Book has Many Issues | One-to-Many |
| Issue → ReturnBook | One Issue has One Return | One-to-One |
| Issue → Fine | One Issue has One Fine | One-to-One |

---
## ⚙️ Setup & Usage

### Step 1 — Create & Use Database
```sql
CREATE DATABASE LibraryManagementDB;
USE LibraryManagementDB;
```

### Step 2 — Create Tables
```sql
CREATE TABLE Category (
    CategoryID INT PRIMARY KEY,
    CategoryName VARCHAR(50)
);

CREATE TABLE Book (
    BookID INT PRIMARY KEY,
    Title VARCHAR(100),
    Author VARCHAR(100),
    Publisher VARCHAR(100),
    CategoryID INT,
    CopiesAvailable INT,
    FOREIGN KEY (CategoryID) REFERENCES Category(CategoryID)
);

CREATE TABLE Member (
    MemberID INT PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100),
    Phone VARCHAR(20),
    Department VARCHAR(50)
);

CREATE TABLE Librarian (
    LibrarianID INT PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100),
    Phone VARCHAR(20)
);

CREATE TABLE Issue (
    IssueID INT PRIMARY KEY,
    BookID INT,
    MemberID INT,
    IssueDate DATE,
    DueDate DATE,
    FOREIGN KEY (BookID) REFERENCES Book(BookID),
    FOREIGN KEY (MemberID) REFERENCES Member(MemberID)
);

CREATE TABLE ReturnBook (
    ReturnID INT PRIMARY KEY,
    IssueID INT UNIQUE,
    ReturnDate DATE,
    FOREIGN KEY (IssueID) REFERENCES Issue(IssueID)
);

CREATE TABLE Fine (
    FineID INT PRIMARY KEY,
    IssueID INT UNIQUE,
    Amount DECIMAL(10,2),
    FOREIGN KEY (IssueID) REFERENCES Issue(IssueID)
);
```

---
### Step 3 — Insert Sample Data
```sql
INSERT INTO Category VALUES
(1, 'Programming'),
(2, 'Database'),
(3, 'Networking');

INSERT INTO Book VALUES
(101, 'Database System Concepts', 'Korth', 'McGraw Hill', 2, 10);

INSERT INTO Member VALUES
(1, 'Rahim', 'rahim@gmail.com', '01711111111', 'CSE');

INSERT INTO Issue VALUES
(1, 101, 1, '2026-01-01', '2026-01-15');

-- Fine Example: Returned 5 days late → 5 × 10 = 50 BDT
INSERT INTO Fine VALUES (1, 1, 50.00);
```

---
## 🔎 Sample Queries

### Show All Books
```sql
SELECT * FROM Book;
```

### Show Available Books
```sql
SELECT * FROM Book WHERE CopiesAvailable > 0;
```

### Books by Category (JOIN)
```sql
SELECT b.Title, c.CategoryName
FROM Book b
INNER JOIN Category c ON b.CategoryID = c.CategoryID;
```

### Issued Books Report
```sql
SELECT m.Name, b.Title, i.IssueDate
FROM Issue i
INNER JOIN Member m ON i.MemberID = m.MemberID
INNER JOIN Book b ON i.BookID = b.BookID;
```

### Members Who Borrowed Books
```sql
SELECT m.Name, b.Title
FROM Issue i
INNER JOIN Member m ON i.MemberID = m.MemberID
INNER JOIN Book b ON i.BookID = b.BookID;
```

### Total Books
```sql
SELECT COUNT(*) AS TotalBooks FROM Book;
```

### Total Members
```sql
SELECT COUNT(*) AS TotalMembers FROM Member;
```

### Total Fine Collected
```sql
SELECT SUM(Amount) AS TotalFine FROM Fine;
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
📦 Library Management System
 ┣ 🔐 Admin Module
 ┃  ┣ Add Books
 ┃  ┣ Add Members
 ┃  ┣ Manage Categories
 ┃  ┗ Manage Librarians
 ┣ 📋 Librarian Module
 ┃  ┣ Issue Books
 ┃  ┣ Return Books
 ┃  ┗ Fine Management
 ┗ 👤 Member Module
    ┣ Search Books
    ┣ View Borrow History
    ┗ View Fine
```

---

## ❓ Viva Q&A

**Q: Main entities of this system?**
> `Book`, `Member`, `Librarian`, `Issue`, `ReturnBook`, `Fine`, `Category`

**Q: Book and Category relationship?**
> One-to-Many — one category contains many books

**Q: Member and Issue relationship?**
> One-to-Many — one member can borrow many books

**Q: Issue and ReturnBook relationship?**
> One-to-One — each issue has exactly one return record

**Q: Why is the Fine table used?**
> To store penalty amounts for late book returns

**Q: Fine calculation formula?**
> `Fine = (ReturnDate - DueDate) × 10 BDT`

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

# 🔐 User Login & Registration System

A complete **Authentication & Authorization Database** project built with SQL — covering user registration, login, password hashing, role-based access control (RBAC), login history, and password reset. Applicable to virtually every modern application.

---
## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Database Schema](#database-schema)
- [ER Diagram](#er-diagram)
- [Relationships](#relationships)
- [Setup & Usage](#setup--usage)
- [Core Flows](#core-flows)
- [Sample Queries](#sample-queries)
- [Role-Based Access Control](#role-based-access-control-rbac)
- [Security Best Practices](#security-best-practices)
- [Normalization](#normalization)
- [Project Modules](#project-modules)
- [Viva Q&A](#viva-qa)

---
## 🔍 Overview

This system handles authentication and authorization for any modern application:

| Use Case | Example |
|---|---|
| 🏫 University Portal | Student, Teacher, Admin login |
| 🛒 E-commerce | Customer accounts |
| 🏦 Banking System | Secure role-based access |
| 📱 Mobile Apps | Session & token management |
| 🏢 ERP Software | Multi-role enterprise access |

---

## ✨ Features

| Feature | Description |
|---|---|
| User Registration | Create account with validation |
| User Login | Verify credentials securely |
| Password Hashing | Never store plain text passwords |
| Role Management | Admin, Teacher, Student, Customer |
| Account Status Control | Active / Inactive / Blocked |
| Forgot Password | Token-based reset via email |
| Login History | Track login/logout with IP address |
| Session Management | Create and destroy sessions |

---
## 🗄️ Database Schema

### `Role`
| Field | Type | Description |
|---|---|---|
| RoleID | INT | Primary Key |
| RoleName | VARCHAR(50) | Admin / Teacher / Student / Customer |

### `Users`
| Field | Type | Description |
|---|---|---|
| UserID | INT | Primary Key (Auto Increment) |
| Username | VARCHAR(50) | Unique, Not Null |
| Email | VARCHAR(100) | Unique, Not Null |
| PasswordHash | VARCHAR(255) | Hashed Password |
| RoleID | INT | Foreign Key → Role |
| Status | VARCHAR(20) | Default: `Active` |
| CreatedAt | DATETIME | Default: `GETDATE()` |

### `LoginHistory`
| Field | Type | Description |
|---|---|---|
| LoginID | INT | Primary Key (Auto Increment) |
| UserID | INT | Foreign Key → Users |
| LoginTime | DATETIME | Default: `GETDATE()` |
| LogoutTime | DATETIME | Updated on logout |
| IPAddress | VARCHAR(50) | Client IP |

### `PasswordReset`
| Field | Type | Description |
|---|---|---|
| ResetID | INT | Primary Key (Auto Increment) |
| UserID | INT | Foreign Key → Users |
| Token | VARCHAR(255) | Unique reset token |
| ExpireTime | DATETIME | Token expiry (1 hour) |

---
## 📊 ER Diagram

```
Role (1) ───────────── (M) Users
                              │
                 ┌────────────┴────────────┐
                 │                         │
              (M) │                      (M) │
                  ▼                         ▼
           LoginHistory             PasswordReset
```

---

## 🔗 Relationships

| Entities | Relationship | Type |
|---|---|---|
| Role → Users | One Role assigned to Many Users | One-to-Many |
| Users → LoginHistory | One User has Many Login Records | One-to-Many |
| Users → PasswordReset | One User can have Many Reset Requests | One-to-Many |

---

## ⚙️ Setup & Usage

### Step 1 — Create & Use Database
```sql
CREATE DATABASE AuthenticationDB;
USE AuthenticationDB;
```

### Step 2 — Create Tables
```sql
CREATE TABLE Role (
    RoleID INT PRIMARY KEY,
    RoleName VARCHAR(50) UNIQUE NOT NULL
);

CREATE TABLE Users (
    UserID INT IDENTITY(1,1) PRIMARY KEY,
    Username VARCHAR(50) UNIQUE NOT NULL,
    Email VARCHAR(100) UNIQUE NOT NULL,
    PasswordHash VARCHAR(255) NOT NULL,
    RoleID INT NOT NULL,
    Status VARCHAR(20) DEFAULT 'Active',
    CreatedAt DATETIME DEFAULT GETDATE(),
    FOREIGN KEY (RoleID) REFERENCES Role(RoleID)
);

CREATE TABLE LoginHistory (
    LoginID INT IDENTITY(1,1) PRIMARY KEY,
    UserID INT NOT NULL,
    LoginTime DATETIME DEFAULT GETDATE(),
    LogoutTime DATETIME,
    IPAddress VARCHAR(50),
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);

CREATE TABLE PasswordReset (
    ResetID INT IDENTITY(1,1) PRIMARY KEY,
    UserID INT NOT NULL,
    Token VARCHAR(255) NOT NULL,
    ExpireTime DATETIME NOT NULL,
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);
```

---
### Step 3 — Insert Sample Roles
```sql
INSERT INTO Role VALUES
(1, 'Admin'),
(2, 'Teacher'),
(3, 'Student'),
(4, 'Customer');
```

---

## 🔄 Core Flows

### 📝 Registration Flow
```
User Fills Form (Username, Email, Password)
           ↓
   Input Validation
           ↓
   Password Hashing
           ↓
   Save to Database
           ↓
  Registration Success
```

```sql
-- Step: Store registered user
INSERT INTO Users (Username, Email, PasswordHash, RoleID)
VALUES ('rahim', 'rahim@gmail.com', 'hashed_password_here', 3);
```

---
### 🔑 Login Flow
```
User Enters Username + Password
           ↓
   Find User in DB
           ↓
   Hash Entered Password
           ↓
   Compare with Stored Hash
           ↓
   Match → Login Success    |    No Match → Login Failed
           ↓
   Record Login History
```

```sql
-- Step 1: Find user
SELECT * FROM Users WHERE Username = 'rahim';

-- Step 2: Record login
INSERT INTO LoginHistory (UserID, IPAddress)
VALUES (1, '192.168.1.100');
```

---

### 🚪 Logout Flow
```sql
-- Update logout time
UPDATE LoginHistory
SET LogoutTime = GETDATE()
WHERE LoginID = 1;
```

---
### 🔁 Forgot Password Flow
```
User Clicks Forgot Password
           ↓
   Email Verification
           ↓
   Generate Reset Token
           ↓
   Store Token (expires in 1 hour)
           ↓
   Send Reset Email
           ↓
   User Resets Password
```

```sql
-- Store reset token
INSERT INTO PasswordReset (UserID, Token, ExpireTime)
VALUES (1, 'ABCD1234TOKEN', DATEADD(HOUR, 1, GETDATE()));
```

---
## 🔎 Sample Queries

### Show All Users
```sql
SELECT * FROM Users;
```

### Active Users Only
```sql
SELECT * FROM Users WHERE Status = 'Active';
```

### Blocked Users
```sql
SELECT * FROM Users WHERE Status = 'Blocked';
```

### Users with Role Name (JOIN)
```sql
SELECT u.Username, u.Email, r.RoleName
FROM Users u
INNER JOIN Role r ON u.RoleID = r.RoleID;
```

### Login History Report
```sql
SELECT u.Username, l.LoginTime, l.LogoutTime, l.IPAddress
FROM LoginHistory l
INNER JOIN Users u ON l.UserID = u.UserID;
```

### Total Users Per Role
```sql
SELECT r.RoleName, COUNT(*) AS TotalUsers
FROM Users u
INNER JOIN Role r ON u.RoleID = r.RoleID
GROUP BY r.RoleName;
```

---
## 🛡️ Role-Based Access Control (RBAC)

| Role | Permissions |
|---|---|
| **Admin** | Manage Users, Manage Roles, View Reports, Block Accounts |
| **Teacher** | View Students, Upload Marks, Manage Courses |
| **Student** | View Profile, View Results, Change Password |
| **Customer** | Browse, Purchase, View Order History |

---
## 🔒 Security Best Practices

### ❌ Never Store Plain Text Passwords
```
Plain Text:   123456          ← WRONG
Hashed:       $2b$10$KJHJK... ← CORRECT (Bcrypt)
```

### ✅ Enforce Unique Constraints
```sql
Email    VARCHAR(100) UNIQUE
Username VARCHAR(50)  UNIQUE
```

### ✅ Strong Password Policy
- Minimum 8 characters
- At least one uppercase letter
- At least one lowercase letter
- At least one number
- At least one special character

### ✅ Account Status Management
| Status | Meaning |
|---|---|
| `Active` | User can login normally |
| `Inactive` | Account not yet verified |
| `Blocked` | Admin has restricted access |

---
## 📐 Normalization

This schema is normalized up to **3rd Normal Form (3NF)**:

| Normal Form | Rule Applied |
|---|---|
| **1NF** | All attributes contain atomic values |
| **2NF** | No partial dependencies on composite keys |
| **3NF** | No transitive dependencies between non-key attributes |

---
## 🧩 Project Modules

```
📦 Authentication System
 ┣ 📝 Registration Module
 ┃  ┣ Register User
 ┃  ┣ Validate Email
 ┃  ┗ Store Hashed Password
 ┣ 🔑 Login Module
 ┃  ┣ Verify User
 ┃  ┣ Verify Password Hash
 ┃  ┗ Create Session
 ┣ 🔁 Password Module
 ┃  ┣ Change Password
 ┃  ┣ Forgot Password
 ┃  ┗ Reset via Token
 ┗ 🔐 Admin Module
    ┣ View All Users
    ┣ Block / Unblock Users
    ┗ Assign Roles
```

---
## ❓ Viva Q&A

**Q: Password database-এ plain text আকারে store করা উচিত?**
> না — সবসময় hash আকারে store করতে হবে (Bcrypt/SHA-256)

**Q: Password hashing কেন প্রয়োজন?**
> Database leak হলেও original password দেখা যাবে না; hash reverse করা computationally impossible

**Q: LoginHistory table-এর কাজ কী?**
> User-এর login/logout time এবং IP address track করা — security audit ও session management-এর জন্য

**Q: Role table কেন আলাদা রাখা হয়?**
> Role-Based Access Control (RBAC) implement করার জন্য; নতুন role add করা সহজ হয়

**Q: Authentication এবং Authorization-এর পার্থক্য?**
> Authentication = User কে verify করা (তুমি কে?) | Authorization = User কী করতে পারবে তা determine করা (তুমি কী করতে পারবে?)

**Q: IDENTITY(1,1) মানে কী?**
> Auto-increment — প্রথম value 1 থেকে শুরু, প্রতিবার 1 করে বাড়বে

**Q: Token-based password reset কীভাবে কাজ করে?**
> Random token generate হয়, DB-তে expiry সহ store হয়, email-এ পাঠানো হয়; user link click করলে token validate করে password reset দেওয়া হয়

---
## 🔄 Complete Authentication Flow

```
Registration
     ↓
Password Hashing
     ↓
Database Storage
     ↓
Login Request
     ↓
Password Verification
     ↓
Authentication Success
     ↓
Session Created
     ↓
Role Check
     ↓
Authorization
     ↓
System Access Granted
```

---
## 🛠️ Tech Stack

![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-Database-orange?style=for-the-badge)
![Security](https://img.shields.io/badge/Security-Password%20Hashing-green?style=for-the-badge)

---

## 📁 Project Structure

```
user-login-registration-db/
 ┣ schema.sql          # All CREATE TABLE statements
 ┣ sample_data.sql     # INSERT statements for testing
 ┣ queries.sql         # Common SELECT, JOIN, GROUP BY queries
 ┣ flows.sql           # Registration, login, logout, reset flows
 ┗ README.md           # Project documentation
```

---

## 📄 License

This project is open-source and available for educational purposes.

---

> **Northern University Bangladesh — Authentication System Database Project**  
> DBMS Course Project | SQL Server | Security | Role-Based Access Control

---
</details>


<details>
    <summary><b>Full CRUD Project</b></summary>


---

</details>


