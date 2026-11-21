# Online Library Management System – Week 4
## SQL Data Manipulation Language (DML)


### Week 4 -- Implementing SQL Data Manipulation Commands
### 1. Introduction
DML commands are used to insert new records, modify existing data and remove records from database tables.Retrieving information using SELECT queries and managing transactions.

### 2. Inserting Records – INSERT

The INSERT command is used to store new records in the database tables.

**General Syntax:**

```sql
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);
```

**SQL Queries:**

#### 2.1 Adding Book Categories

```sql
INSERT INTO CATEGORY VALUES
(1,'Computer Science','Programming Books');

INSERT INTO CATEGORY VALUES
(2,'Mathematics','Math Books');
```

#### 2.2 Adding Author Details

```sql
INSERT INTO AUTHOR VALUES
(1,'A Kumar','Database Author');

INSERT INTO AUTHOR VALUES
(2,'R Meena','Programming Author');
```

#### 2.3 Adding Publisher Information

```sql
INSERT INTO PUBLISHER VALUES
(1,'Tech Books','9876500001');
```

#### 2.4 Registering Library Members

```sql
INSERT INTO MEMBER VALUES
(101,'Arun Kumar','arun@mail.com','9000000001',SYSDATE,'STUDENT');

INSERT INTO MEMBER VALUES
(102,'Bala Devi','bala@mail.com','9000000002',SYSDATE,'STUDENT');
```

#### 2.5 Adding Book Details

```sql
INSERT INTO BOOK VALUES
(201,'ISBN001','Oracle Database',1,1,1,650,5,5);

INSERT INTO BOOK VALUES
(202,'ISBN002','Python Basics',1,2,1,500,4,4);
```

#### 2.6 Recording Book Issue Details

```sql
INSERT INTO BOOK_ISSUE VALUES
(301,201,101,SYSDATE,SYSDATE+14,'ISSUED');
```

After inserting the records, I used COMMIT to save the changes.

```sql
COMMIT;
```
### 3. Updating Existing Records – UPDATE

The UPDATE command is used to change the values of existing records based on a specified condition.

**SQL Query:**

```sql
UPDATE BOOK
SET AVAILABLE_COPIES = 4
WHERE BOOK_ID = 201;
```

### 4. Cancelling Changes – ROLLBACK

ROLLBACK is used to cancel database changes that have not yet been committed.

**SQL Query:**

```sql
ROLLBACK;
```

### 5. Retrieving Records – SELECT

SELECT is used to fetch information from database tables.

**SQL Queries:**

Display all book records:

```sql
SELECT * FROM BOOK;
```

Display all registered members:

```sql
SELECT * FROM MEMBER;
```

Retrieve book titles and prices:

```sql
SELECT TITLE, PRICE
FROM BOOK
WHERE PRICE > 400
ORDER BY PRICE DESC;
```

**Concepts:**

- **SELECT:** Retrieves data from tables.
- **WHERE:** Filters records based on a condition.
- **ORDER BY:** Arranges the retrieved records in ascending or descending order.

### 6. Using CASE Expression

The CASE expression is used to display different results depending on specified conditions.

**SQL Query:**

```sql
SELECT TITLE,
CASE
    WHEN AVAILABLE_COPIES > 0 THEN 'AVAILABLE'
    ELSE 'NOT AVAILABLE'
END STATUS
FROM BOOK;
```

### 7. Using Substitution Variables in SQL*Plus

Substitution variables allow users to provide values dynamically while executing SQL queries.

**SQL Query:**

```sql
SELECT TITLE
FROM BOOK
WHERE CATEGORY_ID = &CATEGORY_NO;
```

### 8. Transaction Control Commands

Transaction control commands help manage changes made to database records.

The following commands:

| Command | Purpose |
|---|---|
| COMMIT | Saves transaction changes permanently |
| ROLLBACK | Cancels uncommitted changes |
| SAVEPOINT | Creates a point within a transaction |

**SQL Practice:**

```sql
UPDATE BOOK
SET AVAILABLE_COPIES = AVAILABLE_COPIES - 1
WHERE BOOK_ID = 201;

SAVEPOINT after_update;

ROLLBACK TO after_update;

ROLLBACK;
```
