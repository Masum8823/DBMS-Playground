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
## 2. Deadlock Avoidance

Deadlock হওয়ার সম্ভাবনা থাকলে request reject করা হয়।

________________________________________

### Most famous algorithm:

Banker's Algorithm

### Created by:

Edsger W. Dijkstra

________________________________________

## Idea:
 ```text
Grant request only if system remains safe
 ```
 
________________________________________

## Safe State

  ```text
All transactions can finish
 ```
________________________________________

## Unsafe State

  ```text
Deadlock may occur
 ```
________________________________________
## 3. Deadlock Detection

Deadlock allow করা হয়।

পরে detect করা হয়।

________________________________________

### Method:

  ```text
Wait-For Graph
 ```
________________________________________

### If cycle found:

  ```text
Deadlock detected
 ```
________________________________________

## 4. Deadlock Recovery

Deadlock detect হওয়ার পরে solve করা হয়।

________________________________________

### Method 1: Transaction Abort

একটি transaction terminate করা হয়।

________________________________________

### Example:

  ```text
Abort T2

T1 continues

 ```
________________________________________

### Method 2: Rollback

Transaction rollback করে previous state-এ নিয়ে যাওয়া হয়।

________________________________________

### Example:
 ```text
ROLLBACK;
 ```
 
________________________________________

## Victim Selection

Recovery-এর সময় কোন transaction abort হবে?

________________________________________

### Usually:

•	Less work done  
•	Less resources used  
•	Lower priority  

transaction কে victim বানানো হয়।
---
## Deadlock Prevention Protocols

________________________________________

## Wait-Die Protocol

Timestamp-based method।

________________________________________

## Rule:

### Older Transaction

Can wait

________________________________________

### Younger Transaction

Must abort

________________________________________

### Example:

  ```text
T1 = Older
T2 = Younger

 ```
________________________________________

### If:
 ```text
T2 wants T1 resource
 ```
 
### Result:

  ```text
T2 dies (abort)
 ```
________________________________________
## Wound-Wait Protocol

Wait-Die-এর opposite।

________________________________________

## Rule:

### Older Transaction

Can force younger to abort

________________________________________

### Younger Transaction

Must wait

________________________________________

### Example:

  ```text
T1 older
T2 younger

 ```
________________________________________

T1 needs T2 resource:

  ```text
T2 abort
 ```
________________________________________
## Deadlock vs Starvation

অনেক student viva-তে এইটা confuse করে।

________________________________________

| Deadlock | Starvation |
|-----------|------------|
| Transactions wait forever | Transaction never gets chance |
| Circular wait exists | Circular wait not necessary |
| System stuck | System running |
| More dangerous | Less dangerous |

________________________________________
## Example of Starvation

  ```text
High-priority transactions always run

Low-priority transaction never executes

 ```
---
## Deadlock vs Livelock

________________________________________

## Deadlock

  ```text
Nobody moves
 ```
________________________________________

## Livelock

  ```text
Everybody moves
But no progress

 ```
________________________________________

### Example:

দুইজন মানুষ বারবার একে অপরকে রাস্তা দিতে গিয়ে একই দিকে সরে যাচ্ছে।
 ```text
Move left
Move right
Move left
Move right

 ```
 
কিন্তু কেউই সামনে যেতে পারছে না।

________________________________________
## Advantages of Deadlock Handling

### 1. Prevents system freeze

### 2. Improves reliability

### 3. Better transaction management

### 4. Data consistency maintained

________________________________________

## Disadvantages

### 1. Extra overhead

### 2. Complex algorithms

### 3. Performance cost

### 4. Resource consumption

________________________________________
## Exam-Oriented Comparison

| Technique | Idea |
|------------|------|
| Prevention | Stop deadlock before it occurs |
| Avoidance | Avoid unsafe state |
| Detection | Find deadlock after it occurs |
| Recovery | Resolve deadlock |

________________________________________
## Viva Questions

### Q: Deadlock কী?

দুই বা ততোধিক transaction একে অপরের resource-এর জন্য indefinitely wait করলে তাকে deadlock বলে।

________________________________________

### Q: Deadlock হওয়ার 4টি condition কী?

•	Mutual Exclusion  
•	Hold and Wait  
•	No Preemption  
•	Circular Wait  

________________________________________

### Q: Wait-For Graph কী?

Transaction waiting relationship-এর graph।

________________________________________

### Q: Deadlock detect কিভাবে করা হয়?

Wait-For Graph এ cycle খুঁজে।

________________________________________

### Q: Deadlock recovery কিভাবে করা হয়?

Abort বা rollback করে।

________________________________________

### Q: Deadlock এবং Starvation-এর পার্থক্য কী?

Deadlock এ circular wait থাকে, starvation এ থাকে না।

________________________________________

## Quick Summary
 ```text
Deadlock = Transactions waiting forever

Necessary Conditions:
1. Mutual Exclusion
2. Hold and Wait
3. No Preemption
4. Circular Wait

Handling Methods:
- Prevention
- Avoidance
- Detection
- Recovery

Detection Tool:
Wait-For Graph

Recovery:
Abort / Rollback

 ```
---
</details>


<details>
    <summary><b>Serializability</b></summary>

# Serializability

Serializability হলো Concurrency Control-এর সবচেয়ে গুরুত্বপূর্ণ concept।

এটা নিশ্চিত করে যে, database-এ একাধিক transaction একসাথে (concurrently) execute হলেও final result এমন হবে যেন transaction গুলো serially (একটার পর একটা) execute হয়েছে।

👉 সহজভাবে:

  ```text
Concurrent Execution
        ↓
Result should be same as
        ↓
Serial Execution

 ```
________________________________________

## Why Serializability is Needed?

DBMS-এর মূল উদ্দেশ্য:

  ```text
High Performance + Correct Result
 ```
________________________________________

যদি আমরা সব transaction serially চালাই:

  ```text
T1 → T2 → T3 → T4
 ```
তাহলে result সবসময় correct হবে।

কিন্তু system slow হয়ে যাবে।

________________________________________

আর যদি concurrently চালাই:
 ```text
T1
 ↕
T2
 ↕
T3

 ```
 
তাহলে system fast হবে।

কিন্তু conflict হওয়ার chance থাকবে।

________________________________________

এই conflict prevent করার জন্য DBMS serializability ব্যবহার করে।

________________________________________
## What is a Schedule?

Transaction operations execute হওয়ার order-কে Schedule বলে।

________________________________________

### Example

ধরি:

### Transaction T1

  ```text
Read(A)
A = A + 100
Write(A)

 ```
________________________________________

### Transaction T2

  ```text
Read(A)
A = A - 50
Write(A)

 ```
________________________________________

এই operations কী order-এ execute হবে, সেটাই schedule।

________________________________________

## Types of Schedule

________________________________________

## 1. Serial Schedule

এক transaction সম্পূর্ণ শেষ হওয়ার পর আরেক transaction শুরু হয়।

________________________________________

### Example

  ```text
T1:
Read(A)
Write(A)

T2:
Read(A)
Write(A)

 ```
________________________________________

### Execution:

  ```text
T1 → Complete
↓
T2 → Complete

 ```
________________________________________

### Characteristics

✔ Correct

✔ No conflict

❌ Slow

❌ Poor resource utilization

________________________________________

### Example

Initial A = 1000

________________________________________

### T1
 ```text
+100
 ```
 
Result:
 ```text
1100
 ```
 
________________________________________

### T2

  ```text
-50
 ```
Result:

  ```text
1050
 ```
________________________________________

### Final:
 ```text
1050
 ```
 
________________________________________
## 2. Non-Serial Schedule

Transactions interleaved হয়।

________________________________________

### Example:

  ```text
T1: Read(A)

T2: Read(A)

T1: Write(A)

T2: Write(A)

 ```
________________________________________

Concurrent execution।

________________________________________

### May be:

✔ Correct

or

❌ Incorrect

________________________________________

তাই Non-Serial Schedule automatically safe না।

________________________________________
## Serializable Schedule

Serializable Schedule হলো এমন non-serial schedule যার result serial schedule-এর result-এর সমান।

________________________________________

### Definition
 ```text
Concurrent execution
produces same result
as some serial execution

 ```
 
________________________________________

### Example

Initial Balance = 1000

________________________________________

### T1

  ```text
+500
 ```
________________________________________

### T2
 ```text
-200
 ```
 
________________________________________

### Serial Result:
 ```text
1000 + 500 - 200
= 1300

 ```
 
________________________________________

Concurrent execution-এর result যদি:
 ```text
1300
 ```
 
হয়

✔ Serializable

________________________________________

যদি:
 ```text
800
 ```
 
হয়

❌ Not Serializable

________________________________________
## Types of Serializability

Exam-এর জন্য সবচেয়ে important section।

________________________________________

## 1. Conflict Serializability

Most Important

Most Asked

Most Used

________________________________________

## What is Conflict?

দুই operation conflict করবে যদি:

________________________________________

### Condition 1

Different transactions থেকে আসতে হবে।

________________________________________

### Condition 2

Same data item access করতে হবে।

________________________________________

### Condition 3

At least one operation Write হতে হবে।

________________________________________

## Conflict Cases

________________________________________

### Read-Read
 ```text
R1(A)
R2(A)

 ```
 
Conflict?

❌ No

________________________________________

কারণ কেউ data change করছে না।

________________________________________

### Read-Write
 ```text
R1(A)
W2(A)

 ```
 
Conflict?

✔ Yes

________________________________________

### Write-Read
 ```text
W1(A)
R2(A)

 ```
 
Conflict?

✔ Yes

________________________________________

### Write-Write

  ```text
W1(A)
W2(A)

 ```
Conflict?

✔ Yes

________________________________________

## Example of Conflict Serializable Schedule

________________________________________

### Schedule:

  ```text
R1(A)

W1(A)

R2(A)

W2(A)

 ```
________________________________________

### Equivalent Serial Order:
 ```text
T1 → T2
 ```
 
________________________________________

✔ Conflict Serializable
---
## Precedence Graph (Serialization Graph)

Conflict Serializability check করার সবচেয়ে popular method।

________________________________________

## Construction Rules

________________________________________

### Step 1

Each transaction = Node

________________________________________

### Example:
 ```text
T1
T2
T3

 ```
 
________________________________________

### Step 2

Conflict operation থাকলে edge draw করো।

________________________________________

### Example
 ```text
W1(A)

R2(A)

 ```
 
________________________________________

### Edge:

  ```text
T1 → T2
 ```
________________________________________

কারণ T1 আগে execute হয়েছে।

________________________________________

### Rule
 ```text
No Cycle
    ↓
Conflict Serializable

 ```
 
________________________________________
 ```text
Cycle Exists
    ↓
Not Conflict Serializable


 ```
 
________________________________________

### Example

Schedule:
 ```text
W1(A)

R2(A)

W2(B)

R3(B)

 ```
 
________________________________________

### Graph:

  ```text
T1 → T2 → T3
 ```
________________________________________

Cycle নেই।

✔ Serializable

________________________________________

### Example with Cycle

  ```text
T1 → T2

T2 → T1

 ```
________________________________________

### Graph:

  ```text
T1 ↔ T2
 ```
________________________________________

Cycle আছে।

❌ Not Serializable

________________________________________
## 2. View Serializability

Conflict serializability-এর চেয়ে broader concept।

________________________________________

### Idea

Read-write relationship preserve থাকতে হবে।

________________________________________

Schedule view serializable হবে যদি:

________________________________________

### Initial Read preserved

কে প্রথম value read করেছে সেটা same থাকতে হবে।

________________________________________

### Read-From preserved

কে কার write থেকে value read করেছে সেটা same থাকতে হবে।

________________________________________

### Final Write preserved

Last write same transaction হতে হবে।

________________________________________

### Example

Some schedules conflict serializable না হলেও view serializable হতে পারে।

________________________________________

তাই:

  ```text
Conflict Serializable
⊂
View Serializable

 ```
________________________________________

মানে:
 ```text
Every Conflict Serializable
is View Serializable

But
Every View Serializable
is NOT Conflict Serializable

 ```
 
________________________________________
## Recoverable Schedule

Serializability-এর সাথে closely related।

________________________________________

### Example:
 ```text
T1 writes A

T2 reads A

 ```
 
________________________________________

T2 commit করার আগে:

  ```text
T1 must commit
 ```
________________________________________

Otherwise recovery problem হবে।

________________________________________
## Cascading Rollback Problem

________________________________________

### Example

### T1:

  ```text
Write(A)
 ```
________________________________________

### T2:
 ```text
Read(A)
 ```
 
________________________________________

### T3:
 ```text
Read(A)
 ```
 
________________________________________

Now:

  ```text
T1 Rollback
 ```
________________________________________

Then:
 ```text
T2 Rollback
T3 Rollback

 ```
 
________________________________________

এটাকে Cascading Rollback বলে।

________________________________________
## Serializability vs Concurrency

| Feature | Serial Execution | Concurrent Execution |
|----------|-----------------|----------------------|
| Speed | Low | High |
| Resource Usage | Poor | Better |
| Correctness | Guaranteed | Need Control |

________________________________________
## Serializability vs Isolation

অনেক student confuse করে।

________________________________________

### Isolation

ACID property

এক transaction অন্য transaction-এর intermediate result দেখতে পারবে না।

________________________________________

### Serializability

Schedule correctness নিশ্চিত করে।

________________________________________
## Advantages of Serializability

### 1. Ensures Correct Results

________________________________________

### 2. Maintains Consistency

________________________________________

### 3. Supports Concurrency

________________________________________

### 4. Prevents Transaction Anomalies

________________________________________

### 5. Basis of Concurrency Control

________________________________________

## Disadvantages

### 1. Extra Checking Overhead

________________________________________

### 2. Graph Construction Cost

________________________________________

### 3. Performance Impact

________________________________________

### 4. Complex Implementation

________________________________________

## Common Exam Confusions

________________________________________

### Serializable ≠ Serial

________________________________________

### Serial
 ```text
T1 complete
then T2

 ```
 
________________________________________

### Serializable

  ```text
T1 and T2 interleaved
but same final result

 ```
________________________________________

### Conflict Serializable ≠ View Serializable

________________________________________

### Conflict Serializable:

More strict

________________________________________

### View Serializable:

Less strict

________________________________________
## Viva Questions

### Q: Serializability কী?

Concurrent schedule-এর result যদি serial schedule-এর result-এর সমান হয়, তাহলে সেটি serializable।

________________________________________

### Q: Conflict Serializability কী?

Conflict operations reorder করে serial schedule পাওয়া গেলে।

________________________________________

### Q: Precedence Graph কী?

Conflict relationship দেখানোর graph।

________________________________________

### Q: Graph-এ cycle থাকলে কী হবে?

Schedule conflict serializable হবে না।

________________________________________

### Q: View Serializability কী?

Read-from এবং final write relationship preserve থাকলে।

________________________________________

### Q: Conflict Serializable এবং View Serializable-এর সম্পর্ক কী?

  ```text
Conflict Serializable ⊂ View Serializable
 ```
________________________________________
## Quick Summary
 ```text
Serializability = Correct Concurrent Execution

Types:
1. Conflict Serializability
2. View Serializability

Conflict Rules:
RW → Conflict
WR → Conflict
WW → Conflict
RR → No Conflict

Precedence Graph:
No Cycle → Serializable
Cycle → Not Serializable

Conflict Serializable ⊂ View Serializable

 ```
---
</details>


<details>
    <summary><b>Locking Protocol</b></summary>

# Locking Protocol

Locking Protocol হলো DBMS-এর এমন একটি technique, যা concurrent transactions-এর মধ্যে data access control করে এবং data inconsistency, lost update, dirty read ইত্যাদি সমস্যা প্রতিরোধ করে।

👉 সহজভাবে:

  ```text
Locking Protocol = Before using data,
take permission (lock) first

 ```
________________________________________

## Why Locking Protocol is Needed?

ধরুন একটি bank account-এ balance আছে:
 ```text
Balance = 10000
 ```
 
________________________________________

## Transaction T1

  ```text
Withdraw 2000
 ```
________________________________________

## Transaction T2
 ```text
Deposit 5000
 ```
 
________________________________________

যদি T1 এবং T2 একই সময়ে balance update করে, তাহলে wrong result আসতে পারে।

তাই DBMS বলে:

  ```text
"Before reading or writing data,
first lock it."

 ```
________________________________________
## What is a Lock?

Lock হলো database object (row, table, page, record)-এর উপর temporary restriction।

________________________________________

### Example

T1 Student table-এর একটি row lock করেছে।

তখন:

  ```text
Other transactions may wait
or be blocked

 ```
________________________________________

## Basic Idea

  ```text
Acquire Lock
      ↓
Perform Operation
      ↓
Release Lock

 ```
________________________________________
## Types of Locks

DBMS-এ প্রধানত দুই ধরনের lock ব্যবহৃত হয়।

________________________________________

## 1. Shared Lock (S-Lock)

Shared Lock read operation-এর জন্য ব্যবহৃত হয়।

________________________________________

### Characteristics

✔ Multiple transactions একই data read করতে পারে  
✔ Data modify করা যায় না  

________________________________________

### Example

T1:
 ```text
SELECT * FROM Student;
 ```
 
________________________________________

DBMS:
 ```text
Shared Lock on Student
 ```
 
________________________________________

এখন T2-ও read করতে পারবে।

________________________________________

### Example
 ```text
T1 → Read(A)

T2 → Read(A)

 ```
 
✔ Allowed

________________________________________

কারণ:
 ```text
Read + Read = No Conflict
 ```
 
________________________________________
## 2. Exclusive Lock (X-Lock)

Exclusive Lock write operation-এর জন্য ব্যবহৃত হয়।

________________________________________

### Characteristics

✔ Only one transaction allowed  
✔ Read/Write block হতে পারে  

________________________________________

### Example

T1:

  ```text
UPDATE Student
SET CGPA = 4.00
WHERE ID = 101;

 ```
________________________________________

DBMS:

  ```text
Exclusive Lock on Student
 ```
________________________________________

এখন:
 ```text
T2 Read? ❌ Not Allowed

T2 Write? ❌ Not Allowed

 ```
 
________________________________________
## Lock Compatibility Matrix

এটা exam-এর জন্য খুব গুরুত্বপূর্ণ।

| Existing Lock | Requested S | Requested X |
|----------------|------------|-------------|
| S | ✔ Allowed | ❌ Not Allowed |
| X | ❌ Not Allowed | ❌ Not Allowed |

________________________________________


---
### Easy Memory Trick

  ```text
S + S = Allowed

S + X = Block

X + S = Block

X + X = Block

 ```
________________________________________
## Lock Manager

DBMS-এর ভিতরে Lock Manager নামে component থাকে।

এর কাজ:

• Lock grant করা  
• Lock release করা  
• Waiting queue maintain করা  
• Deadlock detect করা  

________________________________________
## Locking Protocol Workflow

________________________________________

### Step 1

Transaction lock request করে।

________________________________________

### Step 2

DBMS compatibility check করে।

________________________________________

### Step 3

Compatible হলে:
 ```text
Lock Granted
 ```
 
________________________________________

### Step 4

Compatible না হলে:
 ```text
Transaction Waits
 ```
 
________________________________________

## Example

________________________________________

T1:
 ```text
Lock-X(A)
 ```
 
Granted

________________________________________

T2:

  ```text
Lock-S(A)
 ```
Denied

________________________________________

কারণ:

  ```text
X + S = Not Compatible
 ```
________________________________________
## Binary Locking Protocol

সবচেয়ে basic locking protocol।

________________________________________

## Rules

Lock এর দুইটা state থাকে:

  ```text
0 = Unlocked

1 = Locked

 ```
________________________________________

### Example
 ```text
A = Unlocked
 ```
 
T1:
 ```text
Lock(A)
 ```
 
________________________________________

Now:

  ```text
A = Locked
 ```
________________________________________

### Problem:

Binary lock read/write distinction করতে পারে না।

________________________________________

তাই modern DBMS এটি খুব কম ব্যবহার করে।

________________________________________
## Two-Phase Locking Protocol (2PL)

Concurrency Control-এর সবচেয়ে important locking protocol।

Exam এবং viva-তে খুব common।

________________________________________

## Basic Rule

Transaction দুই phase-এ কাজ করবে।

________________________________________

## Phase 1: Growing Phase

শুধু lock acquire করা যাবে।

________________________________________

### Example

  ```text
Lock(A)

Lock(B)

Lock(C)

 ```
Allowed

________________________________________

## Phase 2: Shrinking Phase

শুধু lock release করা যাবে।

________________________________________

### Example

  ```text
Unlock(A)

Unlock(B)

Unlock(C)

 ```
Allowed

________________________________________

## Important Rule
 ```text
After first unlock,
new lock cannot be acquired

 ```
 
________________________________________

### Example

  ```text
Lock(A)

Lock(B)

Unlock(A)

Lock(C)

 ```
❌ Invalid

________________________________________

কারণ unlock করার পরে নতুন lock নেওয়া হয়েছে।

________________________________________

## Why 2PL is Important?

2PL guarantee করে:

  ```text
Conflict Serializability
 ```
________________________________________

অর্থাৎ concurrent schedule correct থাকবে।

________________________________________
## Types of Two Phase Locking

________________________________________

## 1. Basic 2PL

Normal growing + shrinking phase।

________________________________________

### Example
 ```text
Lock(A)

Lock(B)

Unlock(A)

Unlock(B)

 ```
 
✔ Valid

________________________________________

### Problem

Deadlock হতে পারে।

________________________________________
## 2. Strict 2PL

সব X-lock commit/rollback পর্যন্ত release করা যাবে না।

________________________________________

### Example

  ```text
Lock-X(A)

Update A

COMMIT

Unlock(A)

 ```
________________________________________

### Benefits:

✔ Prevents Dirty Read  
✔ Prevents Cascading Rollback  
✔ Easier Recovery  

________________________________________

Modern DBMS-এ সবচেয়ে বেশি ব্যবহৃত।

________________________________________
## 3. Rigorous 2PL

সব lock (S এবং X) commit পর্যন্ত hold করা হয়।

________________________________________

### Example

  ```text
Lock-S(A)

Lock-X(B)

COMMIT

Release All Locks

 ```
________________________________________

### Benefits:

Very strict consistency

________________________________________

### Drawback:

Less concurrency

________________________________________
## 4. Conservative (Static) 2PL

Transaction শুরু হওয়ার আগে সব lock acquire করতে হবে।

________________________________________

### Example

  ```text
Need A,B,C

Acquire A,B,C first

Then start execution

 ```
________________________________________

### Benefit:

  ```text
Deadlock Impossible
 ```
________________________________________

### Drawback:

Low concurrency

---
## Lock Granularity

Lock কত বড় data unit-এর উপর apply হবে।

________________________________________

## Database Level Lock

পুরো database lock।
 ```text
One lock
Huge restriction

 ```
 
________________________________________

## Table Level Lock

একটি table lock।

________________________________________

### Example

  ```text
Student Table Locked
 ```
________________________________________

## Page Level Lock

Memory page lock।

Moderate overhead

________________________________________

## Row Level Lock

Most common।

________________________________________
### Example

  ```text
Student Table Locked
 ```
________________________________________

### Benefits:

High concurrency

________________________________________

## Granularity Comparison

| Lock Level | Concurrency | Overhead |
|-------------|------------|----------|
| Database | Low | Low |
| Table | Medium | Medium |
| Page | High | Medium |
| Row | Very High | High |

________________________________________

## Lock Conversion

কখনো transaction lock upgrade/downgrade করে।

________________________________________

## Upgrade

  ```text
Shared → Exclusive
 ```
________________________________________

### Example
 ```text
Read First
Then Update

 ```
 
________________________________________

## Downgrade

  ```text
Exclusive → Shared
 ```
________________________________________
## Problems in Locking Protocol

________________________________________

## 1. Deadlock

________________________________________

### Example


 ```text
T1 holds A

Needs B

 ```
________________________________________

 ```text
T2 holds B

Needs A

 ```
________________________________________

### Result:

 ```text
Deadlock
 ```
________________________________________

## 2. Starvation

________________________________________

এক transaction বারবার wait করে।

________________________________________

### Example

 ```text
High priority transactions always execute

Low priority waits forever

 ```
________________________________________
## Advantages of Locking Protocol

### 1. Maintains Consistency

### 2. Prevents Lost Update

### 3. Prevents Dirty Read

### 4. Supports Concurrent Execution

### 5. Ensures Serializability

________________________________________

## Disadvantages

### 1. Deadlock Risk

### 2. Waiting Overhead

### 3. Performance Cost

### 4. Complex Lock Management

________________________________________
## Locking Protocol vs Timestamp Protocol

| Feature | Locking | Timestamp |
|----------|--------|----------|
| Uses Locks | Yes | No |
| Deadlock | Possible | Not Possible |
| Waiting | Yes | No |
| Rollback | Less | More |

________________________________________
## Viva Questions

### Q: Locking Protocol কী?

Concurrency control technique যেখানে data access-এর আগে lock নেওয়া হয়।

________________________________________

### Q: Shared Lock কী?

Read lock।

________________________________________

### Q: Exclusive Lock কী?

Write lock।

________________________________________

### Q: 2PL কী?

Two-Phase Locking protocol যেখানে growing phase এবং shrinking phase থাকে।

________________________________________

### Q: Strict 2PL কী?

সব exclusive lock commit পর্যন্ত hold করা হয়।

________________________________________

### Q: Conservative 2PL-এর সুবিধা কী?

Deadlock prevent করে।

________________________________________

### Q: Lock Manager-এর কাজ কী?

Lock grant, release এবং management করা।

________________________________________
## Quick Summary
```text
Locking Protocol = Permission-based concurrency control

Locks:
S-Lock → Read
X-Lock → Write

Protocols:
1. Binary Locking
2. Basic 2PL
3. Strict 2PL
4. Rigorous 2PL
5. Conservative 2PL

Benefits:
- Consistency
- Isolation
- Serializability

Problems:
- Deadlock
- Starvation

 ```
________________________________________


</details>


<details>
    <summary><b>Recovery System</b></summary>

# Recovery System in DBMS

Recovery System হলো DBMS-এর এমন একটি mechanism, যা system failure, software crash, hardware failure, power failure বা transaction failure-এর পরে database কে আবার consistent state-এ ফিরিয়ে আনে।

👉 সহজভাবে:

 ```text
Recovery System = Database Crash
                    ↓
              Restore Correct Data

 ```
________________________________________

## Why Recovery System is Needed?

Database system সবসময় perfectly run করে না।

অনেক কারণে failure হতে পারে:
l
• Power failure  
• Software bug  
• Operating System crash  
• Hard disk failure  
• Network problem  
• Transaction error  
• Human mistake  

________________________________________
ধরুন:

Rahim ATM থেকে 5000 টাকা withdraw করলো।

### Transaction:
```text
Balance = 10000

Withdraw = 5000

New Balance = 5000

 ```
 
________________________________________

ঠিক balance update হওয়ার আগে system crash করলো।

________________________________________

## Possible Problems:

 ```text
Money deducted from ATM

But database not updated

 ```
or
```text
Database updated

But money not delivered

 ```
 
________________________________________

এখন database inconsistent হয়ে যাবে।

________________________________________

এই সমস্যা solve করার জন্য Recovery System ব্যবহার করা হয়।

________________________________________
## Main Goal of Recovery System

Recovery System-এর প্রধান লক্ষ্য:

 ```text
Maintain Database Consistency
 ```
________________________________________

এছাড়া:

1. Preserve Data  
2. Recover Lost Data  
3. Ensure Transaction Reliability  
4. Maintain ACID Properties  

বিশেষ করে:
```text
Atomicity
Durability

 ```
 
________________________________________

## Recovery Concepts

Recovery বুঝতে হলে কিছু basic concept আগে জানতে হবে।

________________________________________

## Transaction

Transaction হলো logical unit of work।

________________________________________

### Example:

 ```text
BEGIN TRANSACTION

Withdraw 5000

Update Balance

COMMIT

 ```
________________________________________

Transaction complete না হওয়া পর্যন্ত DBMS এটাকে monitor করে।

________________________________________
## Transaction States

________________________________________

## 1. Active

Transaction execute হচ্ছে।

________________________________________

## 2. Partially Committed

Last statement execute হয়েছে।

কিন্তু COMMIT এখনো হয়নি।

________________________________________

## 3. Committed

Successfully complete হয়েছে।

________________________________________

## 4. Failed

Error হয়েছে।

________________________________________

## 5. Aborted

Rollback করা হয়েছে।

________________________________________
## Transaction State Diagram

 ```text
Active
   ↓
Partially Committed
   ↓
Committed

 ```
________________________________________

Failure হলে:
```text
Active
   ↓
Failed
   ↓
Aborted

 ```
 
________________________________________
## Types of Failures

Recovery System-এর সবচেয়ে important topic।

________________________________________

## 1. Transaction Failure

Single transaction fail করে।

________________________________________

### Causes

• Invalid input  
• Arithmetic error  
• Constraint violation  
• Deadlock victim  

________________________________________

### Example

 ```text
Balance = Balance / 0
 ```
________________________________________

Result:

 ```text
Transaction Failed
 ```
________________________________________
## 2. System Crash

পুরো DBMS crash করে।

________________________________________

### Causes

• Power failure  
• OS crash  
• RAM failure  

________________________________________

### Example
```text
Electricity gone
 ```
 
________________________________________

All active transactions interrupted।

________________________________________
## 3. Media Failure

Storage device damage।

________________________________________

### Causes

• Hard disk crash  
• SSD corruption  

________________________________________

### Example

 ```text
Disk physically damaged
 ```
________________________________________

Most dangerous failure।

________________________________________

## 4. Communication Failure

Distributed database-এ network issue।

________________________________________

### Example
```text
Server disconnected
 ```
 
________________________________________
## Recovery Techniques

DBMS recovery-এর জন্য কয়েকটি technique ব্যবহার করে।

________________________________________

## 1. Log-Based Recovery

সবচেয়ে popular technique।

Almost every modern DBMS ব্যবহার করে।

________________________________________

## What is Log?

Log হলো special file যেখানে transaction-এর history store হয়।

________________________________________

### Example
```text
T1 Started

T1 Updated A

T1 Updated B

T1 Committed

 ```
 
________________________________________

সব log stable storage-এ রাখা হয়।

________________________________________

## Log Record Format

________________________________________

## Transaction Start
```text
<T1 START>
 ```
 
________________________________________

## Write Operation
```text
<T1, A, 1000, 1500>
 ```
 
Meaning:

 ```text
A changed

Old Value = 1000

New Value = 1500

 ```
________________________________________

## Commit

 ```text
<T1 COMMIT>
 ```
________________________________________

## Rollback

 ```text
<T1 ABORT>
 ```
________________________________________
## Write Ahead Logging (WAL)

Most important recovery rule।

________________________________________

## Rule

 ```text
Write Log First

Write Database Later

 ```
________________________________________

Meaning:

 ```text
Log must reach disk
before actual data update

 ```
________________________________________

This guarantees recovery।

________________________________________

### Example

Wrong:
```text
Update Database

Then Write Log

 ```
 
❌ Dangerous

________________________________________

Correct:
```text
Write Log

Then Update Database

 ```
 
✔ Safe

________________________________________
## Deferred Update Recovery

Also called:
```text
NO-UNDO / REDO
 ```
 
________________________________________

Idea:

Database update commit-এর আগে করা হবে না।

________________________________________

### Example

 ```text
Transaction running

Changes only in log

 ```
________________________________________

After COMMIT:

 ```text
Apply changes
 ```
________________________________________

Crash হলে:

 ```text
Only REDO required
 ```
________________________________________
## Immediate Update Recovery

Most common technique।

________________________________________

Idea:

Database commit-এর আগেই update হতে পারে।

________________________________________

### Example

 ```text
Update database

Before COMMIT

 ```
________________________________________

Crash হলে:

Need:
```text
UNDO + REDO
 ```
 
________________________________________

## UNDO Operation

Transaction-এর changes remove করা।

________________________________________

### Example

Before:

 ```text
Balance = 1000
 ```
________________________________________

Transaction changed:
```text
Balance = 1500
 ```
 
________________________________________

Crash before commit।

________________________________________

UNDO:

 ```text
Balance = 1000
 ```
________________________________________
## REDO Operation

Committed transaction-এর changes reapply করা।

________________________________________

### Example

Committed:
```text
Balance = 1500
 ```
 
________________________________________

Crash happened।

________________________________________

REDO:
```text
Balance = 1500 again
 ```
 
________________________________________

## Checkpointing

Very important recovery optimization।

________________________________________

## Problem Without Checkpoint

Suppose log contains:
```text
10 Million Records
 ```
 
________________________________________

Crash হলে:

সব log scan করতে হবে।

Slow হবে।

________________________________________

## Solution

Checkpoint ব্যবহার করা।

________________________________________

### Example
```text
<Checkpoint>
 ```
 
________________________________________

Meaning:

 ```text
Database consistent until here
 ```
________________________________________

Recovery শুরু হবে checkpoint থেকে।

________________________________________

Not from beginning।

________________________________________
## Recovery Using Checkpoint

________________________________________

Crash হলে:

### Step 1

Find latest checkpoint

________________________________________

### Step 2

Check active transactions

________________________________________

### Step 3

UNDO incomplete transactions

________________________________________

### Step 4

REDO committed transactions

________________________________________
## Shadow Paging

Alternative recovery technique।

________________________________________

Modern DBMS-এ কম ব্যবহৃত।

________________________________________

## Idea

Two copies maintain করা হয়।

________________________________________

## Current Page

Original data

________________________________________

## Shadow Page

Backup copy

________________________________________

If crash:

 ```text
Use shadow page
 ```
________________________________________

No need for log।

________________________________________

## Recovery Manager

DBMS-এর internal component।

________________________________________

Responsibilities:

• Maintain logs  
• Perform rollback  
• Perform redo  
• Handle checkpoints  
• Crash recovery  

________________________________________
## Recovery and ACID Properties

Recovery System mainly supports:

________________________________________

## Atomicity
```text
All or Nothing
 ```
 
________________________________________

If transaction incomplete:
```text
UNDO
 ```

________________________________________

## Durability

 ```text
Committed = Permanent
 ```
________________________________________

If crash occurs:
```text
REDO
 ```
________________________________________
## Example (Complete Recovery Scenario)

Initial Balance:
```text
10000
 ```
 
________________________________________

Transaction T1:
```text
Withdraw 2000
 ```
   
________________________________________

## Log:

 ```text
<T1 START>

<T1,Balance,10000,8000>

 ```
________________________________________

Before commit:

 ```text
System Crash
 ```
________________________________________

## Recovery:

 ```text
T1 incomplete
 ```
________________________________________

UNDO:

 ```text
Balance restored to 10000
 ```
________________________________________

Database consistent again।

________________________________________
## Recovery Algorithms Summary

| Technique | Undo | Redo |
|------------|------|------|
| Deferred Update | No | Yes |
| Immediate Update | Yes | Yes |
| Shadow Paging | No | No |

________________________________________
## Advantages of Recovery System

### 1. Data Consistency

### 2. Data Reliability

### 3. Crash Recovery

### 4. Supports Atomicity

### 5. Supports Durability

________________________________________

## Disadvantages

### 1. Extra Storage for Logs

### 2. Performance Overhead

### 3. Complex Implementation

### 4. Checkpoint Cost
---
## Common Viva Questions

### Q: Recovery System কী?

Failure-এর পরে database কে consistent state-এ ফিরিয়ে আনার mechanism।

________________________________________

### Q: Log কী?

Transaction history store করা special file।

________________________________________

### Q: WAL কী?

Write-Ahead Logging, যেখানে log আগে write হয়।

________________________________________

### Q: UNDO কী?

Uncommitted changes remove করা।

________________________________________

### Q: REDO কী?

Committed changes reapply করা।

________________________________________

### Q: Checkpoint কী?

Recovery fast করার জন্য consistency marker।

________________________________________

### Q: Deferred Update কী?

Commit-এর আগে database update হয় না।

________________________________________

### Q: Immediate Update কী?

Commit-এর আগেই database update হতে পারে।

________________________________________
## Recovery Flow (Exam Favourite)
```text
Transaction Starts
        ↓
     Log Write
        ↓
 Database Update
        ↓
      COMMIT
        ↓
 Crash?
   ↓      ↓
 No      Yes
 ↓        ↓
Done   Recovery
            ↓
      UNDO / REDO
            ↓
 Consistent Database

 ```
---
## Quick Summary
```text
Recovery System = Restore database after failure

Main Components:
- Log
- WAL
- Checkpoint
- Recovery Manager

Recovery Operations:
- UNDO
- REDO

Failure Types:
- Transaction Failure
- System Crash
- Media Failure
- Communication Failure

Techniques:
- Deferred Update
- Immediate Update
- Shadow Paging

Supports:
- Atomicity
- Durability

 ```
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


