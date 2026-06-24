<h1 align="center">Practical Project Work</h1>

> ### Explore each topic to understand the core concepts in detail
<p align="center">
  ⬇<b> Click any section below to expand </b> ⬇
</p>

<details>
    <summary><b>Student Management System DB</b></summary>


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

</details>


<details>
    <summary><b>CGPA Calculator Database</b></summary>


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


