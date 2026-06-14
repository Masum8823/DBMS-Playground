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
## Lock-Based Concurrency Control

সবচেয়ে popular technique।

________________________________________

## Lock কী?

Lock = Permission

________________________________________

### Example

T1 row lock করেছে।

তাহলে:

  ```text
Other transactions wait
 ```
________________________________________
## Types of Locks

________________________________________

## Shared Lock (S)

Read করার জন্য।

  ```text
Multiple users can read
 ```
________________________________________

### Example:

  ```text
SELECT *
FROM Students

 ```
________________________________________
## Exclusive Lock (X)

Write করার জন্য।

  ```text
Only one transaction allowed
 ```
________________________________________

### Example:

  ```text
UPDATE Students
SET CGPA = 4.00

 ```
________________________________________
## Shared vs Exclusive Lock

| Lock Type | Read | Write |
|------------|------|--------|
| Shared | Yes | No |
| Exclusive | No | Yes |

________________________________________
## Two Phase Locking (2PL)

Most important protocol।

________________________________________

## Rule

Transaction দুই phase এ কাজ করে:

________________________________________

## Growing Phase

Lock acquire করা যায়।

  ```text
Acquire Lock
Acquire Lock
Acquire Lock

 ```
________________________________________

## Shrinking Phase

Lock release করা যায়।

  ```text
Release Lock
Release Lock

 ```
________________________________________

Lock release করার পরে নতুন lock নেওয়া যাবে না।

________________________________________
## Deadlock

Concurrency control-এর সবচেয়ে dangerous problem।

________________________________________

### Example

### T1:
 ```text
Has Lock A
Waiting for Lock B

 ```
 
________________________________________

### T2:

  ```text
Has Lock B
Waiting for Lock A

 ```
________________________________________

### Result:
 ```text
Both waiting forever
 ```
 
________________________________________

এটাকেই Deadlock বলে।

________________________________________
## Deadlock Prevention

### 1. Timeout

অনেকক্ষণ wait করলে transaction abort।

________________________________________

### 2. Resource Ordering

সব transaction same order-এ lock নেবে।

________________________________________

### 3. Wait-Die Protocol

Older transaction wait করতে পারে।

________________________________________

### 4. Wound-Wait Protocol

Older transaction younger transaction কে abort করাতে পারে।

________________________________________
## Timestamp-Based Concurrency Control

Lock ব্যবহার না করে timestamp ব্যবহার করে।

________________________________________

প্রত্যেক transaction unique timestamp পায়।

  ```text
T1 = 100
T2 = 101

 ```
________________________________________

Older transaction priority পায়।

________________________________________
## Optimistic Concurrency Control

### Assumption:

  ```text
Conflict rarely happens
 ```
________________________________________

### Phase:

  ```text
Read
↓
Validate
↓
Write

 ```
________________________________________

Validation fail করলে rollback।

________________________________________
## Concurrency Control Techniques Summary

| Technique | Idea |
|------------|------|
| Locking | Lock data |
| 2PL | Two-phase locking |
| Timestamp | Time-based ordering |
| Optimistic | Validate before commit |

________________________________________
## Advantages of Concurrency Control

### 1. Data Consistency

### 2. Data Integrity

### 3. Better Multi-user Support

### 4. Correct Transaction Execution

### 5. Prevents Data Corruption

________________________________________

## Disadvantages

### 1. Lock Overhead

### 2. Deadlock Risk

### 3. Increased Complexity

### 4. Waiting Time

________________________________________
## Viva Questions

### Q: Concurrency Control কী?

Multiple transactions simultaneously execute হলেও consistency maintain করার technique।

________________________________________

### Q: Lost Update কী?

এক transaction-এর update অন্য transaction overwrite করলে।

________________________________________

### Q: Dirty Read কী?

Uncommitted data read করা।

________________________________________

### Q: Deadlock কী?

দুই transaction একে অপরের resource-এর জন্য indefinitely wait করলে।

________________________________________

### Q: Shared Lock কী?

Read lock।

________________________________________

### Q: Exclusive Lock কী?

Write lock।

________________________________________

### Q: 2PL কী?

Two Phase Locking protocol যেখানে growing phase ও shrinking phase থাকে।

________________________________________

### Q: Serializability কী?

Concurrent execution-এর result serial execution-এর মতো হওয়া।

________________________________________
## Quick Summary
 ```text
Concurrency Control = Multi-user data protection

Main Problems:
- Lost Update
- Dirty Read
- Non-Repeatable Read
- Phantom Read
- Deadlock

Techniques:
- Locking
- Two Phase Locking (2PL)
- Timestamp Ordering
- Optimistic Concurrency Control

Goal:
Consistency + Isolation + Correctness

 ```
---
</details>


<details>
    <summary><b>Deadlock</b></summary>

# Deadlock in DBMS

Deadlock হলো এমন একটি situation যেখানে দুই বা তার বেশি transaction একে অপরের কাছে থাকা resource-এর জন্য অপেক্ষা করতে থাকে, কিন্তু কেউই resource release করতে পারে না।

ফলে:

 
  ```text
All Transactions Wait Forever
 ```
👉 সহজভাবে:

  ```text
T1 waits for T2
T2 waits for T1

Nobody can continue

 ```
এটাকেই Deadlock বলে।

________________________________________

## Real-Life Example (Easy Analogy)

ধরুন দুইজন মানুষ একটি সরু সেতুর দুই পাশ থেকে আসছে।

  ```text
Person A ← Bridge → Person B
 ```
কেউ কাউকে আগে যেতে দিচ্ছে না।

ফলে:

  ```text
Both are waiting
 ```
কেউ move করতে পারছে না।

এটাই Deadlock-এর real-life example।

________________________________________
## Database Example

ধরি database এ দুইটা resource আছে:
 ```text
Resource A = Student Table
Resource B = Course Table

 ```
 
________________________________________

## Transaction T1

  ```text
Lock(Resource A)

Needs Resource B

 ```
________________________________________

## Transaction T2

  ```text
Lock(Resource B)

Needs Resource A

 ```
________________________________________

## Situation

  ```text
T1 has A
T1 waiting for B

T2 has B
T2 waiting for A

 ```
________________________________________

## Result:
 ```text
T1 ← waiting
T2 ← waiting

 ```
 
কেউই execute করতে পারছে না।

👉 Deadlock তৈরি হয়েছে।

________________________________________
## SQL-Based Example

________________________________________

## Transaction T1
 ```text
BEGIN TRANSACTION;

UPDATE Student
SET Name = 'Rahim'
WHERE ID = 1;

 ```
 
এখন Student row lock হয়েছে।

________________________________________

এরপর:

  ```text
UPDATE Course
SET Title = 'DBMS'
WHERE ID = 10;

 ```
কিন্তু Course row T2 lock করে রেখেছে।

________________________________________

## Transaction T2

  ```text
BEGIN TRANSACTION;

UPDATE Course
SET Title = 'OOP'
WHERE ID = 10;

 ```
এখন Course lock হয়েছে।

________________________________________

এরপর:

  ```text
UPDATE Student
SET Name = 'Karim'
WHERE ID = 1;

 ```
কিন্তু Student row T1 lock করে রেখেছে।

________________________________________

## Final State
 ```text
T1 waiting for Course

T2 waiting for Student

 ```
 
________________________________________

## Result:
 ```text
Deadlock
 ```
 
________________________________________
## Four Necessary Conditions of Deadlock

Deadlock হওয়ার জন্য 4টি condition একসাথে true হতে হবে।

একটাও না থাকলে deadlock হবে না।

________________________________________

## 1. Mutual Exclusion

এক resource একসাথে একজনই ব্যবহার করতে পারবে।

________________________________________

### Example:

  ```text
Exclusive Lock
 ```
________________________________________

## 2. Hold and Wait

Transaction একটি resource hold করে রেখে আরেকটি resource-এর জন্য wait করবে।

________________________________________

### Example:

  ```text
T1 holds A
Waiting for B

 ```
________________________________________

## 3. No Preemption

জোর করে resource কেড়ে নেওয়া যাবে না।

________________________________________

### Example:

  ```text
Lock owner must release it voluntarily
 ```
________________________________________

## 4. Circular Wait

একটি circular chain তৈরি হবে।

________________________________________

### Example:
 ```text
T1 → waits for T2

T2 → waits for T3

T3 → waits for T1

 ```
 
________________________________________

এটাই Deadlock-এর সবচেয়ে গুরুত্বপূর্ণ condition।

________________________________________
## Wait-For Graph (Very Important)

Deadlock detect করার সবচেয়ে popular method।

________________________________________

## Definition

Graph-এর node = Transaction

Edge = Waiting relationship

________________________________________

## Example

  ```text
T1 waits for T2
T2 waits for T3
T3 waits for T1

 ```
________________________________________

## Graph:

  ```text
T1 → T2
↑      ↓
|      |
T3 ←---

 ```
________________________________________

## Rule
 ```text
Cycle exists → Deadlock exists

No cycle → No deadlock

 ```
 
________________________________________
## Deadlock Handling Methods

DBMS deadlock handle করার জন্য 4টা major approach ব্যবহার করে।

________________________________________

## 1. Deadlock Prevention

Deadlock হওয়ার আগেই prevent করা।

________________________________________

## Idea:
 ```text
Break at least one deadlock condition
 ```
 
________________________________________

### Method 1: Eliminate Hold and Wait

Transaction সব resource একবারে request করবে।

________________________________________

### Example:

  ```text
Request A + B together
 ```
________________________________________

### Method 2: Resource Ordering

সব resource fixed order-এ request করতে হবে।

________________________________________

### Example:
 ```text
A → B → C
 ```
 
সব transaction একই order follow করবে।

________________________________________

Deadlock হবে না।

_______________________________________
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


