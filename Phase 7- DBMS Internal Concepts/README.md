<h1 align="center">DBMS Internal Concepts</h1>

> ### Explore each topic to understand the core concepts in detail
<p align="center">
  ⬇<b> Click any section below to expand </b> ⬇
</p>

<details>
    <summary><b>Concurrency Control</b></summary>

# Concurrency Control

Concurrency Control হলো DBMS-এর এমন একটি mechanism, যা একই database-এ একাধিক user বা transaction একই সময়ে access করলে data consistency এবং correctness বজায় রাখে।

👉 সহজভাবে:
 ```text
Concurrency Control = Multiple Users + Same Data + No Conflict
 ```
________________________________________

## Why Concurrency Control is Needed?

Real-world database এ অনেক user একসাথে কাজ করে।

Example:

একটি ব্যাংকের database-এ:

•	User A টাকা তুলছে  
•	User B একই account-এ টাকা deposit করছে  

যদি proper control না থাকে, তাহলে balance ভুল হতে পারে।

________________________________________
## Real-Life Example

ধরি Account Balance = 10,000 টাকা

### Transaction T1
 ```text
Withdraw 2000
 ```
 
### Transaction T2

  ```text
Deposit 5000
 ```
________________________________________

যদি দুটো transaction একই সময়ে execute হয় এবং control না থাকে:

  ```text
T1 reads 10000
T2 reads 10000

T1 writes 8000
T2 writes 15000

 ```
### Final Balance:
 ```text
15000
 ```
 
কিন্তু হওয়া উচিত:
 ```text
13000
 ```
 
👉 এখানে data inconsistency হয়েছে।

________________________________________
## What Concurrency Control Ensures?

Concurrency Control নিশ্চিত করে:

### 1. Consistency

Database সবসময় correct state এ থাকবে।

### 2. Isolation

এক transaction অন্য transaction-এর কাজ disturb করতে পারবে না।

### 3. Recoverability

Failure হলেও data recover করা যাবে।

### 4. Serializability

Concurrent execution হলেও result serial execution-এর মতো হবে।
---
## Serial vs Concurrent Execution

________________________________________

## Serial Execution

এক transaction শেষ হওয়ার পর আরেকটি শুরু হয়।

  ```text
T1 → Complete
↓
T2 → Complete

 ```
________________________________________

### Example
 ```text
T1 Withdraw
T2 Deposit

 ```
 
Result সবসময় correct।

________________________________________

## Concurrent Execution

একাধিক transaction একই সময়ে execute হয়।

  ```text
T1
   ↕
T2

 ```
________________________________________

### Advantage

•	Faster execution  
•	Better resource utilization  

________________________________________

### Disadvantage

•	Data conflict হতে পারে  

________________________________________
## Problems in Concurrent Transactions

________________________________________

## 1. Lost Update Problem

সবচেয়ে common concurrency issue।

________________________________________

### Example

Initial Balance = 1000

________________________________________

### Transaction T1

  ```text
Read 1000
Add 500
Write 1500

 ```
________________________________________

### Transaction T2
 ```text
Read 1000
Subtract 200
Write 800

 ```
 
________________________________________

### Execution:

  ```text
T1 reads 1000
T2 reads 1000

T1 writes 1500
T2 writes 800

 ```
________________________________________

### Final Balance:
 ```text
800
 ```
 
Correct balance হওয়া উচিত:
 ```text
1300
 ```
 
👉 T1-এর update হারিয়ে গেছে।

এটাকেই Lost Update বলে।

________________________________________
## 2. Dirty Read Problem

Uncommitted data read করা।

________________________________________

### Example

### T1:

  ```text
UPDATE Balance = 5000
 ```
 
কিন্তু এখনো COMMIT দেয়নি।

________________________________________

### T2:
 ```text
SELECT Balance
 ```
 
T2 নতুন balance দেখে ফেললো।

________________________________________

পরে T1:
 ```text
ROLLBACK
 ```
 
________________________________________

এখন T2 ভুল data read করেছে।

এটাই Dirty Read।

________________________________________
## 3. Non-Repeatable Read

একই transaction-এর মধ্যে একই data দুইবার read করলে different result পাওয়া।

________________________________________

### Example

### T1:
 ```text
SELECT Balance
 ```
 
Result:

  ```text
5000
 ```
________________________________________

### T2:
 ```text
UPDATE Balance = 7000
COMMIT

 ```
 
________________________________________

### T1 আবার:
 ```text
SELECT Balance
 ```
 
Result:

  ```text
7000
 ```
________________________________________

একই transaction-এর মধ্যে দুইবার different result।

এটাই Non-Repeatable Read।

________________________________________
## 4. Phantom Read

নতুন rows suddenly appear করা।

________________________________________

### Example

### T1:
 ```text
SELECT *
FROM Students
WHERE Dept='CSE'

 ```
 
Result:

  ```text
20 rows
 ```
________________________________________

### T2:

  ```text
INSERT INTO Students
VALUES(...)

 ```
COMMIT

________________________________________

T1 আবার query চালালো।

Result:

  ```text
21 rows
 ```
________________________________________

Extra row "phantom" এর মতো দেখা দিল।

এটাই Phantom Read।

________________________________________
## 5. Dirty Write

এক transaction-এর uncommitted data অন্য transaction overwrite করে।

________________________________________

### Example

### T1:
 ```text
UPDATE Balance=5000
 ```
 
(Not committed)

________________________________________

### T2:

  ```text
UPDATE Balance=8000
 ```
________________________________________

এখন conflict তৈরি হবে।

________________________________________
## Serializability

Concurrency Control-এর সবচেয়ে গুরুত্বপূর্ণ concept।

________________________________________

### Definition

Concurrent execution এমন হতে হবে যাতে result serial execution-এর মতো হয়।

________________________________________

### Example

#### Serial Order:
 ```text
T1 → T2
 ```
 
or
 ```text
T2 → T1
 ```
 
________________________________________

Concurrent execution-এর result যদি এই দুইটার যেকোনো একটার মতো হয়:

✔ Serializable

________________________________________

না হলে:

❌ Non-Serializable
---
## Types of Serializability

________________________________________

## 1. Conflict Serializability

Most important and exam favourite topic।

________________________________________

যদি transactions swap করে serial schedule বানানো যায়:

✔ Conflict Serializable

________________________________________

## 2. View Serializability

Read-write relationship preserve করতে হবে।

________________________________________

Conflict serializability এর চেয়ে broad concept।
---
---
</details>


<details>
    <summary><b>Deadlock</b></summary>


---
</details>


<details>
    <summary><b>Serializability</b></summary>


---
</details>


<details>
    <summary><b>Locking Protocol</b></summary>


---
</details>


<details>
    <summary><b>Recovery System</b></summary>


---
</details>


<details>
    <summary><b>ACID Properties</b></summary>


---
</details>


<details>
    <summary><b>Backup & Recovery</b></summary>


---
</details>


