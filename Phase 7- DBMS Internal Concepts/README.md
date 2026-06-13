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


