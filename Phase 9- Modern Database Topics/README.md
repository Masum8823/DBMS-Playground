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
## Example API with Database (Step-by-Step)

---

## Step 1: User Request
```text
POST /register
```
Data:
```text
{
  "name": "Rahim",
  "email": "rahim@gmail.com",
  "password": "1234"
}

```
---

## Step 2: API Receives Data

Backend checks:
• Email valid?  
• Password strong?  
• User exists?  

---

## Step 3: Database Insert
```text
INSERT INTO users (name, email, password)
VALUES ('Rahim', 'rahim@gmail.com', '1234');

```
---

## Step 4: Response
```text
{
  "message": "User created successfully"
}

```
---
## API Response Format

Usually JSON format ব্যবহার করা হয়।

---

## Success Response
```text
{
  "status": 200,
  "message": "Success",
  "data": { "id": 1, "name": "Rahim" }
}

```
---

## Error Response
```text
{
  "status": 400,
  "message": "Invalid input"
}

```
---
## CRUD with API + Database

---

## Create
```text
POST /users
INSERT INTO users VALUES (...);
```
---

## Read
```text
GET /users
SELECT * FROM users;
```
---

## Update
```text
PUT /users/1
UPDATE users SET name='Karim' WHERE id=1;
```
---

## Delete
```text
DELETE /users/1
DELETE FROM users WHERE id=1;
```
---
## Backend Languages Used for API

• Node.js  
• PHP  
• Python (Django/Flask)  
• Java (Spring Boot)  

---
## Example API (Node.js + Express)
```js
app.post("/users", (req, res) => {
  const { name, email } = req.body;

  const sql = "INSERT INTO users (name, email) VALUES (?, ?)";
  db.query(sql, [name, email], (err, result) => {
    if (err) return res.json({ error: err });

    res.json({ message: "User added" });
  });
});

```
---
## API Security with Database

---

## 1. Authentication

User verify করা হয়।

---

## 2. Authorization

User permission check করা হয়।

---

## 3. SQL Injection Protection

Unsafe query prevent করা।

---

## Bad Example
```text
SELECT * FROM users WHERE email = '$email';
```
---

## Safe Example
```text
db.query("SELECT * FROM users WHERE email = ?", [email]);
```
---
## API Authentication Methods

---

## 1. Session-based

Server memory store করে session।

---

## 2. Token-based (JWT)

Most popular method।

---

## Example:
```text
User Login → JWT Token → API Request → Verify Token
```
---

## JWT Flow
```text
Login → Generate Token
      ↓
Frontend stores token
      ↓
Every API request sends token
      ↓
Backend verifies token

```
---
## API Rate Limiting

API abuse prevent করার জন্য ব্যবহার হয়।

---

## Example:
```text
Max 100 requests per minute
```
---
## API with Firebase / MongoDB / SQL

---

## MySQL

Structured queries ব্যবহার করে।

---

## MongoDB

Document-based JSON API response।

---

## Firebase

Direct SDK + API combined system।

---
## Advantages of API with Database

1. Secure system  
2. Scalable architecture  
3. Easy frontend-backend separation  
4. Multi-platform support (web/mobile)  
5. Better control over data  

---

## Disadvantages

1. Extra layer increases complexity  
2. API latency  
3. Server maintenance needed  
4. Security management required  

---
## Real-World Example

Facebook
```text
App → API → Database → Feed Data
```
---

## E-commerce
```text
User → API → Product DB → Cart/Order
```
---

## Banking
```text
ATM → API → Account DB → Balance Update
```
---
## API vs Direct Database

| Feature | API | Direct DB |
|---|---|---|
| Security | High | Low |
| Control | High | Low |
| Scalability | High | Low |
| Risk | Low | High |

---
## Viva Questions

Q: API কী?  
Application communication interface।

---

Q: API কেন ব্যবহার করা হয়?  
Secure and controlled database access-এর জন্য।

---

Q: REST API কী?  
HTTP-based web service architecture।

---

Q: API কোন format ব্যবহার করে?  
Mostly JSON।

---

Q: API এর সাথে database কিভাবে কাজ করে?  
Client → API → Backend → Database → Response।

---
## Quick Summary
```text
API = Bridge between Frontend and Database

Flow:
Client → API → Server → Database → Response

Main Features:
- Secure access
- Structured communication
- CRUD operations support

Most common type:
REST API

Used in:
Web apps, mobile apps, banking, e-commerce

```
---

</details>

<details>
    <summary><b>Database Security</b></summary>

# Database Security

Database Security হলো এমন একটি system বা mechanism, যা database-এর data কে unauthorized access, misuse, theft, corruption এবং attacks থেকে protect করে।

👉 সহজভাবে:
```text
Database Security = Data protect করা
                    (Unauthorized access থেকে)

```
---

## Why Database Security is Important?

Database এ sensitive data থাকে:
• Student records  
• Bank account info  
• Passwords  
• Medical records  
• Business data  

---

## যদি security না থাকে:
```text
Data leak + hacking + corruption
```
---

## Real impact:
```text
Bank balance change
Personal data leak
System crash abuse

```
---
## Goals of Database Security

Database security-এর main goals:

---

## 1. Confidentiality

Data শুধু authorized user access করতে পারবে।

---

## 2. Integrity

Data correct এবং unchanged থাকবে unauthorized modification ছাড়া।

---

## 3. Availability

Authorized user যখন দরকার তখন data access করতে পারবে।

---

👉 এগুলো একসাথে বলা হয়:
```text
CIA Triad
```
---

## Types of Database Threats

---

## 1. Unauthorized Access

Permission ছাড়া database access করা।

---

## Example:
```text
Hacker login without password
```
---
## 2. SQL Injection

SQL Injection হলো একটি attack যেখানে malicious SQL code input field দিয়ে inject করা হয়।

---

## Example
```text
SELECT * FROM users
WHERE email = '' OR '1'='1';

```
---

👉 Result:
```text
All users data exposed
```
---
## 3. Data Breach

Sensitive data leak হয়ে যাওয়া।

---

## Example:
```text
Hacked database dump online
```
---
## 4. Insider Threat

System admin বা employee malicious activity করে।

---

## Example:
```text
Employee copies customer data
```
---
## 5. Malware / Ransomware

System attack করে data encrypt করে ফেলে।

---

## Example:
```text
Database locked → ransom demand
```
---
## Authentication in Database Security

Authentication means:
```text
User identity verify করা
```
---

## Methods:

### 1. Username & Password
Basic method

---

### 2. Multi-Factor Authentication (MFA)

• Password  
• OTP  
• Email verification  

---

### 3. Biometric

• Fingerprint  
• Face recognition  

---
## Authorization

Authorization means:  
User কী করতে পারবে তা control করা

---

## Example:

| User Type | Permission |
|---|---|
| Admin | Full access |
| Student | Read only |
| Guest | Limited access |

---
## SQL-Based Security Control

---

## GRANT Command

Permission দেওয়া হয়।
```text
GRANT SELECT, INSERT ON Students TO user1;
```
---

## REVOKE Command

Permission remove করা হয়।
```text
REVOKE INSERT ON Students FROM user1;
```
---
## Roles in Database Security

Role = predefined set of permissions
```text
Role = predefined set of permissions
```
---

## Example
```text
Admin Role → Full access
Editor Role → Modify data
Viewer Role → Read only

```
---
## Encryption in Database

Encryption মানে data কে unreadable format এ convert করা।

---

## Types:

### 1. Symmetric Encryption
Same key used for encrypt & decrypt

---

### 2. Asymmetric Encryption
Public key + Private key

---

## Example:
```text
Plain text → Encrypted text → Stored in DB

```
---
## Hashing (Very Important)

Hashing is used for passwords।

---

## Example:
```text
Password: 1234
Hash: 81dc9bdb52d04dc20036dbd8313ed055

```
---

👉 Hashing is:
```text
One-way function (cannot be reversed)
```
---
## Access Control Models

---

## 1. Discretionary Access Control (DAC)

Owner decides permissions.

---

## 2. Mandatory Access Control (MAC)

System rules control access.

---

## 3. Role-Based Access Control (RBAC)

Access based on role.

---

## Example:
```text
Student → Read only
Teacher → Update marks
Admin → Full control

```
---
## SQL Injection Prevention

---

## 1. Parameterized Query
```sql
db.query("SELECT * FROM users WHERE email = ?", [email]);
```
---

## 2. Input Validation

Invalid input reject করা।

---

## 3. Escaping Input

Special characters block করা।

---

## 4. ORM Usage

Object Relational Mapping (safe abstraction)

---
## Backup & Security Relation

Backup security provide করে:
```text
Attack → Data loss → Restore from backup
```
---
## Logging & Auditing

---

## Logging

System actions record করা।

---

## Auditing

User activity track করা।

---

## Example:
```text
User X deleted record at 10:00 AM
```
---
## Database Security Layers

---

## 1. Physical Security

Server room protection

---

## 2. Network Security

Firewall, VPN

---

## 3. OS Security

User permissions

---

## 4. DBMS Security

Authentication, authorization, encryption

---
## Real-World Example

Banking System
```text
User Login → Authentication
      ↓
Check Role → Authorization
      ↓
Encrypt data → Store in DB

```
---
---


</details>