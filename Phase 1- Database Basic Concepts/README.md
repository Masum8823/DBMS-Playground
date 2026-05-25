<details>
  <summary><b>Data, Information, Database</b></summary>
    
## What is Data, Information & Database

### Data (ডাটা কী?)

Data হলো raw facts and figures, যেগুলোর কোনো meaning থাকে না যতক্ষণ না এগুলো process করা হয়।

📌 Example:
101, 102, Rahim, Karim, 85, 90 — এগুলো আলাদা অবস্থায় কোনো clear meaning দেয় না।

👉 সহজভাবে: Data = Unprocessed facts

---

### Information (ইনফরমেশন কী?)

Information হলো processed data, যেটার একটা meaningful result থাকে এবং decision নেওয়ার কাজে লাগে।

📌 Example:
Rahim got 85 marks in DBMS, Karim got 90 marks in Math

👉 সহজভাবে: Information = Processed + Meaningful Data

---

### Database (ডাটাবেস কী?)

Database হলো organized collection of data, যেখানে data গুলো structured ভাবে store করা হয় যাতে সহজে access, manage এবং update করা যায়।

📌 Example:
University student database, Bank system, Facebook user data

👉 সহজভাবে: Database = Organized data storage



### What is DBMS

DBMS (Database Management System) হলো একটি software system, যা database তৈরি, manage, update এবং control করতে সাহায্য করে।

এটা user আর database এর মধ্যে bridge হিসেবে কাজ করে।

📌 DBMS এর কাজ:

- Data store করা  
- Data retrieve করা  
- Data update করা  
- Data delete করা  
- Data security maintain করা  

📌 Example:
MySQL, Oracle, PostgreSQL, SQL Server, MongoDB

👉 সহজভাবে: DBMS = Database manage করার software


DBMS ব্যবহারের যেমন অনেক সুবিধা আছে, তেমনি কিছু limitations ও আছে।

### Advantages:

- DBMS data security provide করে, unauthorized access control করে।  
- Data redundancy কমায়, অর্থাৎ duplicate data কম থাকে।  
- Data access fast হয়, তাই information দ্রুত পাওয়া যায়।  
- Multi-user support থাকে, একসাথে অনেক user কাজ করতে পারে।  
- Backup & recovery সুবিধা থাকে, system crash হলেও data restore করা যায়।  
- Data consistency maintain করে, সব জায়গায় একই data থাকে।  

### Disadvantages:

- DBMS setup এবং maintenance cost বেশি।  
- System complex হওয়ায় শিখতে time লাগে।  
- Storage এবং hardware requirement বেশি লাগে।  
- Small system এর জন্য কখনো কখনো heavy হয়ে যায়।  
- Admin support লাগে maintain করার জন্য।  
- System fail করলে পুরো database system affect হতে পারে।

---

</details>

<details>
    <summary><b>Database vs File System and Types of Database</b></summary>

## Database vs File System

### File System (ফাইল সিস্টেম কী?)

File System হলো traditional method যেখানে data files আকারে OS (Operating System) এ store করা হয়।

📌 Example:

- .txt file  
- Excel file  
- Manual folder system  

👉 এখানে data manually manage করতে হয়।


### Database System (ডাটাবেস সিস্টেম কী?)

Database System হলো structured way of storing data using DBMS, যেখানে data efficiently store, manage, retrieve করা যায়।

👉 এখানে software (DBMS) সব manage করে।

---

### Difference between Database vs File System

| File System | Database System |
|------------|----------------|
| Data files আকারে store হয় | Structured database আকারে store হয় |
| Data redundancy বেশি | Data redundancy কম |
| Data sharing কঠিন | Easy data sharing |
| Security কম | High security |
| Data inconsistency থাকতে পারে | Data consistency maintain হয় |
| Manual processing লাগে | DBMS automatically manage করে |
| Backup difficult | Easy backup & recovery |

👉 সহজভাবে:
File System = old manual method  
Database System = modern smart method  

---

## Types of Database

Database বিভিন্ন ধরনের হতে পারে, depending on structure and usage।



### 1. Centralized Database

সব data এক single central location এ store থাকে।

📌 Example:
Bank main server database

👉 সুবিধা: easy control  
👉 সমস্যা: single point failure risk  


### 2. Distributed Database

Data multiple locations/servers এ distribute করা থাকে।

📌 Example:
Multinational company database

👉 সুবিধা: fast access, reliability  
👉 সমস্যা: complex management  


### 3. Relational Database (RDBMS)

Data table (rows & columns) আকারে store করা হয়।

📌 Example:
MySQL, Oracle

👉 most commonly used database type


### 4. NoSQL Database

Non-tabular format (document, key-value, graph) এ data store হয়।

📌 Example:
MongoDB, Cassandra

👉 Big data & flexible structure এর জন্য use হয়


### 5. Object-Oriented Database

Data object আকারে store করা হয় (OOP concept based)।

📌 Example:
Used in programming systems



#### সহজভাবে Summary:

- Centralized = one place  
- Distributed = multiple places  
- Relational = table format  
- NoSQL = flexible structure  
- Object-Oriented = object based  

---

</details>

<details>
    <summary><b>Relational Database and NoSQL Database </b></summary>

## Relational Database (RDBMS)

Relational Database হলো এমন একটি database system যেখানে data টেবিল (table) আকারে store করা হয়। প্রতিটি table এ rows (records) এবং columns (attributes) থাকে।

📌 সহজভাবে:
Relational Database = Table based database system



### Structure:

- Table = relation  
- Row = record / tuple  
- Column = attribute / field  


#### 📌 Example Table (Student):

| ID | Name  | Marks |
|----|------|------|
| 1  | Rahim | 85   |
| 2  | Karim | 90   |



### Key Features:

- Data table আকারে store হয়  
- Primary key ব্যবহার করা হয় unique identification এর জন্য  
- SQL (Structured Query Language) ব্যবহার করা হয়  
- Data relationship maintain করা যায় (tables link করা যায়)  

#### Example DBMS:

- MySQL  
- Oracle  
- PostgreSQL  
- SQL Server  

#### Advantages:

- Easy to understand (table format)  
- Data consistency maintain হয়  
- Strong security support  
- Powerful query system (SQL)  

#### Disadvantages:

- Large scale big data এর জন্য slower হতে পারে  
- Schema fixed থাকে (flexibility কম)  

👉 সহজভাবে:
Relational DB = structured + table based + SQL system  

---

## NoSQL Database

NoSQL Database হলো এমন database system যেখানে data table আকারে না রেখে flexible format এ store করা হয় (document, key-value, graph, column-based)।

📌 সহজভাবে:
NoSQL = Not Only SQL = flexible database system  

### Types of NoSQL:

- Document based (JSON style)  
- Key-Value store  
- Column-based  
- Graph database  


#### Example (Document format):

```json
{
  "name": "Rahim",
  "age": 20,
  "marks": 85
}
```

### Key Features
- Schema flexible (fixed structure lage na)
- Big data handle korte pare
- Horizontal scaling support kore
- Large systems e fast performance dey

#### Example DBMS
- MongoDB
- Cassandra
- Redis
- CouchDB

#### Advantages
- Very fast for large data
- Flexible structure
- Easy scaling (multiple servers use kora jai)
- Best for unstructured data

#### Disadvantages
- SQL support limited
- Data consistency sometimes weak hoy
- Complex querying kichu khetre difficult

NoSQL = flexible + big data + non-table structure


### Relational vs NoSQL (Quick Difference)

| Relational DB | NoSQL DB |
|--------------|----------|
| Table based | Non-table based |
| Fixed schema | Flexible schema |
| Uses SQL | May not use SQL |
| Best for structured data | Best for unstructured / big data |
---

</details>

<details>
    <summary><b>DBMS Architecture</b></summary>

</details>

<details>
    <summary><b>DBMS Users and Roles along with Data Models</b></summary>

</details>

<details>
    <summary><b>Schema vs Instance</b></summary>

</details>

<details>
    <summary><b>DBMS Keys</b></summary>

</details>

