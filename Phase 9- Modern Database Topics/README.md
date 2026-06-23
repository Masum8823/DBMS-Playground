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
## BSON Format

MongoDB internally BSON (Binary JSON) ব্যবহার করে।

---

## Why BSON?

• Faster parsing  
• Efficient storage  
• Supports more data types  

---
## Important Data Types in MongoDB

• String  
• Integer  
• Boolean  
• Array  
• Object  
• Date  
• Null  

---

## Example
```json
{
  "name": "Rahim",
  "age": 22,
  "isStudent": true,
  "skills": ["C++", "DBMS"],
  "createdAt": "2026-06-12"
}

```
---
## MongoDB Operations (Basic CRUD)

CRUD মানে:
```json
Create
Read
Update
Delete

```
---

---

## 1. Create (Insert Data)
```json
db.students.insertOne({
  name: "Rahim",
  age: 22,
  dept: "CSE"
});

```
---

Multiple insert:
```json
db.students.insertMany([
  { name: "Karim", age: 21 },
  { name: "Jamal", age: 23 }
]);

```
---
## 2. Read (Find Data)
```json
db.students.find();
```
---

Condition:
```json
db.students.find({ age: 22 });
```
---

Pretty format:
```json
db.students.find().pretty();
```
---
## 3. Update Data
```json
db.students.updateOne(
  { name: "Rahim" },
  { $set: { age: 23 } }
);

```
---

Multiple update:

---
```json
db.students.updateMany(
  { dept: "CSE" },
  { $set: { cgpa: 4.00 } }
);

```
---
## 4. Delete Data

---
```json
db.students.deleteOne({ name: "Rahim" });
```
---

Multiple delete:

---
```json
db.students.deleteMany({ age: 21 });
```
---
## Query Operators

MongoDB-তে powerful operators আছে।

---

## Comparison Operators

| Operator | Meaning |
|---|---|
| $eq | equal |
| $ne | not equal |
| $gt | greater than |
| $lt | less than |
| $gte | greater or equal |
| $lte | less or equal |

---

## Example
```json
db.students.find({ age: { $gt: 20 } });
```
---
## Logical Operators

---

### $and

---
```json
db.students.find({
  $and: [
    { age: { $gt: 20 } },
    { dept: "CSE" }
  ]
});

```
### $or
```json
db.students.find({
  $or: [
    { age: 21 },
    { age: 23 }
  ]
});

```
---
## Embedded Documents

MongoDB nested data support করে।

---

## Example
```json
{
  "name": "Rahim",
  "address": {
    "city": "Khulna",
    "zip": 9100
  }
}

```
---

## Query Nested Field
```json
db.students.find({ "address.city": "Khulna" });
```
---

## Arrays in MongoDB

MongoDB array support করে।

---

## Example
```json
{
  "name": "Karim",
  "skills": ["C++", "Java", "DBMS"]
}

```
---

## Query Array
```json
db.students.find({ skills: "C++" });
```
---
## Indexing in MongoDB

Index query speed increase করে।

---

## Example
```json
db.students.createIndex({ name: 1 });
```
---

👉 1 = Ascending order

---
## Advantages of MongoDB

1. High Performance  
2. Flexible Schema  
3. Easy Scaling  
4. JSON-like structure  
5. Good for Big Data & Real-time apps  

---

## Disadvantages

1. No strong joins  
2. Large storage use  
3. Complex transactions (compared to SQL)  
4. Not ideal for highly structured data  

---
## Use Cases of MongoDB

• Social Media Apps  
• Real-time analytics  
• E-commerce platforms  
• IoT systems  
• Content management systems  

---
## MongoDB vs RDBMS Summary
```json
RDBMS → Structured, strict, relational

MongoDB → Flexible, document-based, scalable

```
---
## Viva Questions

Q: MongoDB কী?  
NoSQL document-based database system।

---

Q: MongoDB data কোথায় store করে?  
Document আকারে (BSON format)।

---

Q: Collection কী?  
Documents-এর group।

---

Q: Document কী?  
Key-value based data structure।

---

Q: MongoDB কি schema-less?  
Yes, flexible schema।

---

Q: MongoDB কেন ব্যবহার করা হয়?  
Fast, scalable, big data support করার জন্য।

---
## Quick Summary
```text
MongoDB = NoSQL Database

Structure:
Database → Collection → Document

Key Features:
- Schema-less
- JSON-like documents
- High scalability
- Fast performance

CRUD:
Create, Read, Update, Delete

Best for:
Big data + modern web apps

```
---
</details>

<details>
    <summary><b>Firebase Basics</b></summary>

# Firebase Basics

Firebase হলো Google-এর একটি Backend-as-a-Service (BaaS) platform, যেখানে backend server setup না করেও mobile ও web application বানানো যায়।

👉 সহজভাবে:
```text
Firebase = Ready-made Backend
          (No server setup needed)

```
---

## Firebase কীভাবে কাজ করে?

Firebase cloud-based system ব্যবহার করে।
```text
App (Frontend)
     ↓
Firebase (Cloud Backend)
     ↓
Database + Auth + Storage + Hosting

```
---

## Firebase কেন ব্যবহার করা হয়?

Traditional backend এ:
• Server বানাতে হয়  
• API লিখতে হয়  
• Database manage করতে হয়  

Firebase এ:
সব ready-made service

---
## Core Features of Firebase

Firebase অনেক services দেয়:

---

## 1. Firebase Authentication

User login system handle করে।

---

## Features

✔ Email/Password login  
✔ Google login  
✔ Facebook login  
✔ Phone number login  

---

## Example Flow
```text
User → Sign Up → Firebase Auth → Login Success
```
---

## Example Use

• Facebook login button  
• Google login system  

---## 2. Firestore Database

Cloud Firestore হলো Firebase-এর NoSQL document database।

---

## Structure
```text
Database
   ↓
Collections
   ↓
Documents

```
---

## Example
```text
Users Collection:
{
  "name": "Rahim",
  "age": 22,
  "dept": "CSE"
}

```
---

## Features

✔ Real-time data update  
✔ NoSQL structure  
✔ Offline support  
✔ Fast query  

---

## Firestore vs MongoDB

| Feature | Firestore | MongoDB |
|---|---|---|
| Type | BaaS NoSQL | Standalone NoSQL |
| Hosting | Cloud | Self/Cloud |
| Real-time | Built-in | Limited |
| Setup | Easy | Moderate |

---
## 3. Realtime Database

Firebase-এর older NoSQL database।

---

## Features

✔ JSON tree structure  
✔ Real-time sync  
✔ Mobile friendly  

---

## Example
```text
{
  "users": {
    "user1": {
      "name": "Karim"
    }
  }
}

```
---

## Use Case

• Chat apps  
• Live updates  
• Game score tracking  

---
## 4. Firebase Storage

Large files store করার জন্য ব্যবহার করা হয়।

---

## Store Types

✔ Images  
✔ Videos  
✔ PDFs  
✔ Audio files  

---

## Example
```text
Upload Profile Picture
     ↓
Firebase Storage
     ↓
URL generated

```
---
## 5. Firebase Hosting

Static website deploy করার জন্য ব্যবহার হয়।

---

## Features

✔ Free hosting  
✔ HTTPS support  
✔ Fast CDN  

---

## Example
```text
HTML + CSS + JS
        ↓
Firebase Hosting
        ↓
Live Website

```
---
## Firebase Project Structure
```text
Firebase Project
   ├── Authentication
   ├── Firestore Database
   ├── Storage
   ├── Hosting
   └── Functions

```
---
## How Firebase Works (Simple Flow)
```text
Frontend App
     ↓
Firebase SDK
     ↓
Cloud Services
     ↓
Auth / DB / Storage

```
---
## Firebase SDK

Firebase ব্যবহার করতে SDK লাগে।
```text
SDK = Software Development Kit
```
---

## Example (Web)
```text
import { initializeApp } from "firebase/app";

const firebaseConfig = {
  apiKey: "...",
  authDomain: "...",
  projectId: "..."
};

const app = initializeApp(firebaseConfig);
```
---
## Firebase Authentication Example
```text
import { getAuth, signInWithEmailAndPassword } from "firebase/auth";

const auth = getAuth();

signInWithEmailAndPassword(auth, email, password)
  .then(user => {
    console.log("Login Successful");
  })
  .catch(error => {
    console.log(error.message);
  });

```
---
## Firestore CRUD Example

---

## Create Data
```text
import { getFirestore, setDoc, doc } from "firebase/firestore";

const db = getFirestore();

await setDoc(doc(db, "users", "user1"), {
  name: "Rahim",
  age: 22
});

```
---
## Read Data
```text
import { getDoc, doc } from "firebase/firestore";

const docSnap = await getDoc(doc(db, "users", "user1"));

console.log(docSnap.data());

```
---
## Update Data
```text
import { updateDoc, doc } from "firebase/firestore";

await updateDoc(doc(db, "users", "user1"), {
  age: 23
});

```
---
## Delete Data
```text
import { deleteDoc, doc } from "firebase/firestore";

await deleteDoc(doc(db, "users", "user1"));

```
---
## Firebase Rules (Security Rules)

Firebase data protect করার জন্য rules ব্যবহার করে।

---

## Example Rule
```text
Allow read/write if user is authenticated
```
---

## Code Example
```text
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null;
    }
  }
}

```
---
## Advantages of Firebase

1. No Backend Setup  
2. Fast Development  
3. Real-time Database  
4. Scalable  
5. Google Infrastructure  

---

## Disadvantages of Firebase

1. Expensive at scale  
2. Limited SQL support  
3. Vendor lock-in (Google dependency)  
4. Complex queries limited  

---
## Firebase Use Cases

• Chat applications  
• E-commerce apps  
• Social media apps  
• Real-time dashboards  
• Mobile apps backend  

---
## Firebase vs Traditional Backend

| Feature | Firebase | Traditional Backend |
|---|---|---|
| Setup | Easy | Hard |
| Server | Not needed | Required |
| Speed | Fast development | Slower |
| Control | Limited | Full control |
| Scaling | Automatic | Manual |

---
## Viva Questions

Q: Firebase কী?  
Google-এর Backend-as-a-Service platform।

---

Q: Firebase কি NoSQL?  
Yes, Firestore & Realtime DB NoSQL।

---

Q: Firebase Authentication কী?  
User login system handle করে।

---

Q: Firestore কী?  
Cloud-based NoSQL document database।

---

Q: Firebase Hosting কী?  
Static website deploy করার service।

---
## Quick Summary
```text
Firebase = Backend-as-a-Service (BaaS)

Main Services:
- Authentication
- Firestore Database
- Realtime Database
- Storage
- Hosting

Key Feature:
No server needed + Real-time + Fast development

```
---

</details>


<details>
    <summary><b>API with Database</b></summary>

# API with Database

API (Application Programming Interface) হলো এমন একটি medium, যার মাধ্যমে frontend (client) এবং backend/database এর মধ্যে data exchange করা হয়।

👉 সহজভাবে:
```text
Frontend → API → Backend → Database
```
---

## API কী?

API হলো একটি set of rules এবং endpoints, যা ব্যবহার করে একটি application অন্য application-এর সাথে communicate করে।

---

## Example (Simple)

তুমি mobile app থেকে login করছো:
```text
App → Send login request → API → Database check → Response
```
---
## API কেন লাগে?

Direct database access করা নিরাপদ না।  
তাই API ব্যবহার করা হয়।

---

## Without API (Bad Practice)
```text
Frontend → Direct Database ❌
```
---

Problems:
• Security risk  
• Data leak  
• No control  
• No validation  

---

## With API (Good Practice)
```text
Frontend → API → Database ✔
```
---

Benefits:
• Secure  
• Controlled access  
• Validation possible  
• Scalable system  

---
## Real-Life Example

ধরো একটি e-commerce app:
```text
User → Order Product
```
---

Flow:
```text
Frontend (Website)
     ↓
API Server
     ↓
Database (Orders, Users, Products)

```
---
## API Types

---

## 1. REST API

REST API হলো most common API style।

---

## REST Principles

✔ Stateless  
✔ Uses HTTP methods  
✔ JSON data format  
✔ Client-server architecture  

---

## HTTP Methods

| Method | Use |
|---|---|
| GET | Data read |
| POST | New data create |
| PUT | Update full data |
| PATCH | Partial update |
| DELETE | Data remove |

---

## Example REST Flow
```text
GET /users → Get all users

POST /users → Create user

PUT /users/1 → Update user

DELETE /users/1 → Delete user

```
---
## 2. API + Database Architecture
```text
Client (Browser / Mobile)
        ↓
API Server (Node/PHP/Python)
        ↓
Database (MySQL / MongoDB)

```
---

## Example
```text
Frontend form
   ↓
API: /register
   ↓
Backend validation
   ↓
Database insert

```
User registration system:

---
---

</details>