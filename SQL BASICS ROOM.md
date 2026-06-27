# SQL Basics - TryHackMe Writeup

## Overview

This room introduced the fundamentals of Structured Query Language (SQL), the standard language used to communicate with relational databases. Through practical exercises, I learned how to retrieve, filter, organize, and analyze data using SQL queries.

The room emphasized building query complexity step by step, reinforcing each concept before introducing the next.

---

## Learning Objectives

* Understand the purpose of SQL
* Retrieve data from database tables
* Select specific columns
* Filter records using conditions
* Sort query results
* Combine multiple SQL clauses into a single query
* Develop efficient querying habits

---

## Skills Practiced

### Retrieving Data

The first step was learning how to retrieve all records from a table.

Example:

```sql
SELECT * FROM CoffeeOrders;
```

This returns every column and every row from the selected table.

---

### Selecting Specific Columns

Instead of retrieving unnecessary information, SQL allows selecting only the required columns.

Example:

```sql
SELECT customer_name, drink_name
FROM CoffeeOrders;
```

Selecting only relevant data improves readability and query efficiency.

---

### Filtering Results

The `WHERE` clause limits returned data based on specific conditions.

Example:

```sql
SELECT *
FROM CoffeeOrders
WHERE drink_name = 'Latte';
```

Filtering enables analysts to locate only the information relevant to the investigation or business question.

---

### Sorting Results

The `ORDER BY` clause organizes results in ascending or descending order.

Example:

```sql
SELECT *
FROM CoffeeOrders
ORDER BY price DESC;
```

This displays the most expensive items first.

---

### Combining WHERE and ORDER BY

One of the key exercises involved combining multiple SQL concepts into a single query.

Example:

```sql
SELECT *
FROM CoffeeOrders
WHERE drink_name = 'Latte'
ORDER BY price DESC;
```

This query:

* Filters the results
* Sorts them from highest to lowest price
* Produces a focused and organized result set

---

## Key Lessons Learned

### 1. Build Queries Incrementally

Rather than writing complex queries immediately, it's better to develop them step by step.

Example workflow:

1. Retrieve all data
2. Select required columns
3. Apply filters
4. Sort results
5. Combine everything

This approach reduces mistakes and simplifies troubleshooting.

---

### 2. Query Efficiency Matters

During the lab, I accidentally executed the same sorting query twice.

Although harmless in the lab environment, unnecessary queries consume resources in production databases.

A good analyst should always think before executing a query.

---

### 3. LIMIT Improves Performance

When only a single record is needed, the `LIMIT` clause reduces unnecessary processing.

Example:

```sql
SELECT *
FROM Menu
ORDER BY price DESC
LIMIT 1;
```

This immediately returns the most expensive item.

---

## Commands Learned

```sql
SELECT
FROM
WHERE
ORDER BY
ASC
DESC
LIMIT
```

---

## Practical Skills Gained

* Reading data from relational databases
* Filtering records efficiently
* Organizing query output
* Combining SQL clauses
* Writing cleaner and more efficient queries
* Thinking systematically when constructing queries

---

## Reflection

### What surprised me

I realized that SQL is much more than simply retrieving data. The order in which clauses are combined can completely change the outcome of a query, making SQL a powerful tool for answering specific questions efficiently.

### Challenges I Encountered

One of the improvements highlighted in the room was that I accidentally executed the same sorting query twice. Although it did not affect the lab, it reminded me that unnecessary queries can waste computing resources in real-world environments.

### How I Solved Them

I adopted a more systematic workflow by reviewing query results before re-running commands and by building each query incrementally instead of rushing to the final solution.

### How This Knowledge Applies to Cybersecurity

SQL is widely used in cybersecurity for log analysis, forensic investigations, vulnerability assessments, and database administration. Understanding how to retrieve, filter, and sort information efficiently is a valuable skill for security analysts, penetration testers, and digital forensics professionals.

---

## Takeaway

This room demonstrated that SQL is more than a database language—it's a way of asking precise questions and retrieving meaningful information efficiently.

The biggest lesson from this room was learning to approach query construction methodically by building complexity one step at a time. This mindset applies not only to SQL but also to cybersecurity investigations, where structured thinking is essential.
