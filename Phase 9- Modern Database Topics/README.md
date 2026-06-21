<h1 align="center">Modern Database Topics</h1>

> ### Explore each topic to understand the core concepts in detail
<p align="center">
  ⬇<b> Click any section below to expand </b> ⬇
</p>

<details>
    <summary><b>MongoDB Basics</b></summary>

# MongoDB Basics

MongoDB হলো একটি NoSQL database system, যা traditional relational database (table-based) না হয়ে document-based structure follow করে।

👉 সহজভাবে:
```text
MongoDB = Table না
          → Collection + Document based Database

```
---

## What is MongoDB?

MongoDB হলো একটি NoSQL database যেখানে data JSON-like format (BSON) এ store হয়।

---
## Traditional DB vs MongoDB

| Relational DB | MongoDB |
|---|---|
| Table | Collection |
| Row | Document |
| Column | Field |
| Fixed Schema | Flexible Schema |

---
## Core Idea of MongoDB

MongoDB data store করে document আকারে।

---

## Example
```json
{
  "name": "Rahim",
  "age": 22,
  "department": "CSE"
}

```
---
## Database Structure in MongoDB

MongoDB structure:
```json
Database
   ↓
Collection
   ↓
Document

```
---

## Example
```json
UniversityDB
   ↓
Students Collection
   ↓
Student Document

```
---
## What is a Document?

Document হলো MongoDB-এর basic data unit।  
It is similar to JSON.

---

## Example Document
```json
{
  "student_id": 101,
  "name": "Karim",
  "cgpa": 3.85
}

```
---

## Document Features

✔ Key-value format  
✔ Nested structure possible  
✔ No fixed schema required  
✔ Each document can be different  

---
## What is a Collection?

Collection হলো documents-এর group।

---

## Example
```json
Students Collection:
{ "name": "Rahim" }
{ "name": "Karim", "age": 22 }
{ "name": "Jamal", "cgpa": 3.90 }

```
---
## Key Feature: Schema Flexibility

MongoDB-তে সব document একই structure follow করতে বাধ্য না।

---

## Example
```json
{ "name": "A" }
{ "name": "B", "age": 20 }
{ "name": "C", "department": "CSE" }

```
---

👉 এটাকে বলে:
```json
Schema-less / Flexible Schema
```
---
## Why MongoDB is Used?

### 1. Big Data Support
Huge data handle করতে পারে।

---

### 2. Fast Performance
No complex joins like SQL।

---

### 3. Flexible Structure
Different type of data store করা যায়।

---

### 4. Scalable
Horizontal scaling support করে।

---
## SQL vs MongoDB

| Feature | SQL | MongoDB |
|---|---|---|
| Structure | Fixed | Flexible |
| Schema | Strict | Dynamic |
| Scaling | Vertical | Horizontal |
| Join | Yes | Limited |
| Format | Table | JSON Document |

---
---
</details>

