# Online Library Management System – Week 6
## SQL Operators and Joins

### Week 6 – Working with SQL Operators, Joins and Set Operations

### 1. Introduction
SQL operators help filter, compare and perform calculations on data. Joins help retrieve related information from multiple tables, while set operators are used to combine the results of different SELECT queries.

### 2. SQL Operators

SQL operators are used to perform different operations on database values and conditions.

The following operator categories were covered:

| Operator Type | Operators | Purpose |
|---|---|---|
| Arithmetic | +, -, *, / | Performs mathematical calculations |
| Comparison | =, <>, >, <, >=, <= | Compares two values |
| Logical | AND, OR, NOT | Combines multiple conditions |
| Special | IN, BETWEEN, LIKE, IS NULL | Filters records using specific conditions |
| Set | UNION, INTERSECT, MINUS | Combines query results |

### 3. Practising Special Operators

Used special operators to retrieve book and member information based on different conditions.

#### 3.1 BETWEEN Operator

BETWEEN is used to retrieve records within a specified range. Both boundary values are included.

**SQL Query:**

```sql
SELECT TITLE
FROM BOOK
WHERE PRICE BETWEEN 300 AND 700;
```

#### 3.2 IN Operator

IN is used to check whether a column value matches any value in a specified list.

**SQL Query:**

```sql
SELECT TITLE
FROM BOOK
WHERE CATEGORY_ID IN (1,2);
```

#### 3.3 LIKE Operator

LIKE is used to search for records that match a particular text pattern.

**SQL Query:**

```sql
SELECT TITLE
FROM BOOK
WHERE TITLE LIKE 'O%';
```
**Wildcards used with LIKE:**

- `%` – Matches zero or more characters.
- `_` – Matches exactly one character.

#### 3.4 IS NULL Operator

IS NULL is used to identify records where a column does not contain a value.

**SQL Query:**

```sql
SELECT MEMBER_NAME
FROM MEMBER
WHERE EMAIL IS NULL;
```

**Note:** NULL values should be checked using IS NULL or IS NOT NULL instead of using the equals operator.

### 4. Understanding SQL Joins

Joins are used to retrieve related information from two or more tables.

In the library database, information is maintained in separate tables such as BOOK, MEMBER, BOOK_ISSUE and CATEGORY.

### 5. INNER JOIN

INNER JOIN returns only the records that have matching values in the related tables.

**SQL Query:**

```sql
SELECT ISSUE_ID,
       MEMBER_NAME,
       TITLE
FROM BOOK_ISSUE I
INNER JOIN MEMBER M
ON I.MEMBER_ID = M.MEMBER_ID
INNER JOIN BOOK B
ON I.BOOK_ID = B.BOOK_ID;
```

### 6. LEFT OUTER JOIN

LEFT OUTER JOIN returns all records from the left table and matching records from the right table.

When no matching record exists, the right-side columns display NULL.

**SQL Query:**

```sql
SELECT M.MEMBER_NAME,
       I.ISSUE_ID
FROM MEMBER M
LEFT OUTER JOIN BOOK_ISSUE I
ON M.MEMBER_ID = I.MEMBER_ID;
```

### 7. SELF JOIN

A SELF JOIN is used to join a table with itself. It is useful for comparing records within the same table.

**SQL Query:**

```sql
SELECT B1.TITLE,
       B2.TITLE
FROM BOOK B1
JOIN BOOK B2
ON B1.CATEGORY_ID = B2.CATEGORY_ID
AND B1.BOOK_ID < B2.BOOK_ID;
```

### 8. NATURAL JOIN

NATURAL JOIN automatically matches columns that have the same name and compatible data types in both tables.

**SQL Query:**

```sql
SELECT CATEGORY_NAME,
       TITLE
FROM CATEGORY
NATURAL JOIN BOOK;
```

### 9. CROSS JOIN

CROSS JOIN produces a Cartesian product by combining every row from the first table with every row from the second table.

**SQL Query:**

```sql
SELECT CATEGORY_NAME,
       AUTHOR_NAME
FROM CATEGORY
CROSS JOIN AUTHOR;
```

### 10. Set Operators

Set operators are used to combine the results of two or more SELECT statements.

The queries must return the same number of columns in the same order, with compatible data types.

The set operators :

#### 10.1 UNION

UNION combines the results of two queries and removes duplicate records.

**SQL Query:**

```sql
SELECT MEMBER_ID
FROM BOOK_ISSUE

UNION

SELECT MEMBER_ID
FROM BOOK_RETURN;
```

#### 10.2 INTERSECT

INTERSECT returns only the records that are common to both query results.

**SQL Query:**

```sql
SELECT MEMBER_ID
FROM BOOK_ISSUE

INTERSECT

SELECT MEMBER_ID
FROM BOOK_RETURN;
```

#### 10.3 MINUS

MINUS returns records from the first query that are not present in the second query.

**SQL Query:**

```sql
SELECT MEMBER_ID
FROM BOOK_ISSUE

MINUS

SELECT MEMBER_ID
FROM BOOK_RETURN;
```

### 11. Practising Set Operators with ISSUE_ID
 ISSUE_ID to understand how set operators work with issue and return records.

**UNION:**

```sql
SELECT ISSUE_ID
FROM BOOK_ISSUE

UNION

SELECT ISSUE_ID
FROM BOOK_RETURN;
```

**INTERSECT:**

```sql
SELECT ISSUE_ID
FROM BOOK_ISSUE

INTERSECT

SELECT ISSUE_ID
FROM BOOK_RETURN;
```

**MINUS:**

```sql
SELECT ISSUE_ID
FROM BOOK_ISSUE

MINUS

SELECT ISSUE_ID
FROM BOOK_RETURN;
```
