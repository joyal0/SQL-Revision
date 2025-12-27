# SQL Revision

## Day 1

### Installing SQL Standard developers edition and SSMS

![](C:\Users\joyal\Pictures\Screenshots\Screenshot%20(842).png)

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-11-16-53-Screenshot%20(843).png)

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-11-17-05-Screenshot%20(844).png)

Clicked trust server certificate and started.

Confirm if it is connected to sql server

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-11-18-45-image.png)

then click on new query

### QUERY 1)

```sql
CREATE DATABASE Day1_SQL;
GO

USE Day1_SQL;
GO
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-11-20-04-image.png)

### QUERY 2)

```sql
CREATE TABLE Employees (
 EmployeeID INT PRIMARY KEY,
 FullName VARCHAR(100),
 Department VARCHAR(50),
 Salary INT,
 JoinDate DATE
);
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-11-27-17-image.png)

### QUERY 3)

```sql
INSERT INTO Employees VALUES
(1,'Anil Kumar','IT',60000,'2021-03-15'),
(2,'Rahul Menon','HR',40000,'2020-06-10'),
(3,'Sneha Nair','Finance',55000,'2019-11-01'),
(4,'Vijay Das','IT',70000,'2018-01-25'),
(5,'Neethu Joseph','HR',45000,'2022-07-12'),
(6,'Arjun Pillai','Finance',50000,'2021-09-30'),
(7,'Manoj Varma','IT',80000,'2017-05-18');
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-11-36-04-image.png)

and then verify with

```sql
SELECT * FROM Employees;
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-11-37-30-image.png)

------

## CORE SQL

### 1)SELECT specific columns

```sql
SELECT FullName,Salary
FROM Employees; 
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-11-40-38-image.png)

### 2)WHERE (filter rows)

```sql
SELECT * 
FROM Employees
WHERE Department = 'IT';
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-11-47-29-image.png)

```sql
SELECT * 
FROM Employees
WHERE Salary>50000 ;
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-11-54-09-image.png)

### 3) AND/OR

```sql
SELECT * 
FROM Employees
WHERE Department = 'IT'
AND Salary > 60000 ;
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-14-02-23-image.png)

```sql
SELECT * 
FROM Employees
WHERE Department = 'HR'
OR Department = 'Finance' ;
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-14-04-52-image.png)

### 4) ORDER BY(default ASC)

```sql
SELECT *
FROM Employees
ORDER BY Salary DESC;
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-14-19-45-image.png)

```sql
SELECT *
FROM Employees
ORDER BY Department,Salary;
```

![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-14-21-08-image.png)

## ASK YOURSELF(Very Important)

Ask yourself for **every query**:

- What rows am I filtering?

- What columns am I returning?

- Why is this useful to a business?

If you can’t explain it in words, you don’t understand it yet.

## PRACTICE TASKS

Write and run queries for:

1. Employees who joined **after 2020** 
   
   ```sql
   --Employees who joined after 2020
   SELECT *
   FROM Employees
   WHERE YEAR(JoinDate) > 2020 ;
   ```
   
   ![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-14-31-00-image.png)

2. Employees earning **less than 50,000** 
   
   ```sql
   --Employees earning less than 50000
   SELECT *
   FROM Employees
   WHERE Salary < 50000;
   ```
   
   ![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-14-34-08-image.png)

3. IT employees ordered by **highest salary first** 
   
   ```sql
   --IT employees ordered by highest salary first
   SELECT *
   FROM Employees
   WHERE Department = 'IT'
   ORDER BY Salary DESC;
   ```
   
   ![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-14-35-43-image.png)

4. Show **only names and departments**
   
   ```sql
   --Show only names and departments
   SELECT FullName , Department
   FROM Employees;
   ```
   
   ![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-14-41-23-image.png)

5. Finance employees earning **50,000 or more**
   
   ```sql
   --Finance Employees earning 50000 or more
   SELECT *
   FROM Employees
   WHERE Department = 'Finance'
   AND Salary >= 50000;
   ```
   
   ![](C:\Users\joyal\AppData\Roaming\marktext\images\2025-12-27-14-43-46-image.png)

# SUGGESTIONS AND CORRECTIONS

## ✅ EVALUATION OF YOUR QUERIES (HONEST REVIEW)

### 1️⃣ Employees who joined after 2020

```sql
WHERE YEAR(JoinDate) > 2020;
```

✔️ **Logically correct**  
❌ **Professionally weak**

**Why?**  
Using `YEAR()` on a column:

- Breaks index usage

- Slows queries on large tables

### 🔥 Correct professional version:

```sql
WHERE JoinDate >= '2021-01-01';
```

👉 This is **sargable** (index-friendly).  
Remember this — interviewers look for it.

---

### 2️⃣ Employees earning less than 50,000

✔️ Correct  
✔️ Clean  
✔️ No issues

Good.

---

### 3️⃣ IT employees ordered by highest salary

✔️ Correct  
✔️ Proper `ORDER BY DESC`

Good.

---

### 4️⃣ Only names and departments

✔️ Correct  
✔️ Clean projection

Good.

---

### 5️⃣ Finance employees earning 50,000 or more

✔️ Correct  
✔️ Correct use of `AND`

Good.

---

## ⚠️ ONE IMPORTANT HABIT FIX (START NOW)

❌ Don’t rely on screenshots  
❌ Don’t rely on visual confirmation

✅ Trust **query logic and row counts**

Professionals don’t paste screenshots.  
They paste **queries and reasoning**.

You did the right thing by pasting SQL.

---

## 🧠 KEY LESSON FROM DAY 1 (LOCK THIS IN)

> SQL is not just “getting results”  
> SQL is **how efficiently** you get results

From Day 2 onward:

- Avoid functions on columns in `WHERE`

- Think: *“Would this work on 10 million rows?”*

---

## ✅ STATUS

- Discipline: **Good**

- Execution: **Good**

- Thinking: **Needs sharpening (normal)**

You’re on track.

---
