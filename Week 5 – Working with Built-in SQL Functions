# Online Library Management System – Week 5
## SQL Functions and Data Retrieval

### Week 5 – Working with Built-in SQL Functions

### 1. Introduction
SQL functions help perform calculations, manipulate text, work with dates, convert data types and summarize records.Retrieve information using aggregate functions and grouping operations.

### 2. Number Functions

Number functions are used to perform mathematical operations on numeric values.

| Function | Description | Example |
|---|---|---|
| ROUND() | Rounds a number to specified decimal places | ROUND(125.678, 2) = 125.68 |
| TRUNC() | Removes decimal places without rounding | TRUNC(125.678, 2) = 125.67 |
| MOD() | Returns the remainder | MOD(17, 5) = 2 |
| ABS() | Returns the positive value | ABS(-25) = 25 |

**SQL Query:**

```sql
SELECT BOOK_ID,
       PRICE,
       ROUND(PRICE, 0) AS ROUNDED_PRICE,
       MOD(BOOK_ID, 2) AS REMAINDER
FROM BOOK;
```


### 3. Character Functions

Character functions are used to modify and retrieve information from text values.

| Function | Description |
|---|---|
| UPPER() | Converts text into uppercase |
| LOWER() | Converts text into lowercase |
| INITCAP() | Converts the first letter of each word into uppercase |
| LENGTH() | Returns the number of characters |
| SUBSTR() | Extracts a portion of a string |
| INSTR() | Finds the position of a character or substring |
| TRIM() | Removes leading and trailing spaces |

**SQL Query:**

```sql
SELECT MEMBER_ID,
       UPPER(MEMBER_NAME) AS NAME_UPPER,
       LENGTH(MEMBER_NAME) AS NAME_LENGTH
FROM MEMBER;
```


### 4. Date Functions

Date functions are useful for performing operations on date values, calculating date differences and retrieving specific date information.

| Function | Description |
|---|---|
| SYSDATE | Returns the current database date and time |
| ADD_MONTHS() | Adds a specified number of months |
| MONTHS_BETWEEN() | Calculates the difference between two dates in months |
| LAST_DAY() | Returns the last day of a month |
| NEXT_DAY() | Returns the next specified weekday |

**SQL Query:**

```sql
SELECT MEMBER_ID,
       MEMBER_NAME,
       JOIN_DATE,
       ADD_MONTHS(JOIN_DATE, 12) AS RENEWAL_DATE
FROM MEMBER;
```

### 5. Data Conversion Functions

Conversion functions are used to change values from one data type to another.

The following functions:

- **TO_CHAR():** Converts numeric or date values into character format.
- **TO_DATE():** Converts character values into DATE format.
- **TO_NUMBER():** Converts character values into numeric format.

**SQL Queries:**

#### 5.1 TO_CHAR()

```sql
SELECT TO_CHAR(SYSDATE, 'DD-MON-YYYY') AS TODAY
FROM DUAL;
```

#### 5.2 TO_DATE()

```sql
SELECT TO_DATE('31-DEC-2026', 'DD-MON-YYYY') AS SAMPLE_DATE
FROM DUAL;
```

#### 5.3 TO_NUMBER()

```sql
SELECT TO_NUMBER('1250') + 50 AS TOTAL
FROM DUAL;
```

### 6. Aggregate Functions

Aggregate functions perform calculations on multiple records and return a single result for the selected group of rows.

| Function | Description |
|---|---|
| COUNT() | Counts the number of records |
| SUM() | Calculates the total of numeric values |
| AVG() | Calculates the average |
| MIN() | Returns the smallest value |
| MAX() | Returns the largest value |

**SQL Query:**

```sql
SELECT COUNT(*) AS TOTAL_BOOKS,
       AVG(PRICE) AS AVERAGE_PRICE,
       MIN(PRICE) AS LOWEST_PRICE,
       MAX(PRICE) AS HIGHEST_PRICE
FROM BOOK;
```

### 7. GROUP BY and HAVING Clauses

GROUP BY and HAVING are used to organize records into groups and filter the grouped results.

- **GROUP BY:** Groups records based on common column values.
- **HAVING:** Filters groups based on aggregate conditions.
- **WHERE:** Filters individual records before grouping.

#### 7.1 GROUP BY

This query groups books according to their category and counts the number of books in each category.

```sql
SELECT CATEGORY_ID,
       COUNT(*) AS BOOK_COUNT
FROM BOOK
GROUP BY CATEGORY_ID;
```

#### 7.2 GROUP BY with HAVING

This query displays only those categories that contain more than one book.

```sql
SELECT CATEGORY_ID,
       COUNT(*) AS BOOK_COUNT
FROM BOOK
GROUP BY CATEGORY_ID
HAVING COUNT(*) > 1
ORDER BY CATEGORY_ID;
```
### 8. Adding Records to Library Tables

Inserting additional sample records into the library database to work with different SQL functions and retrieval queries.

#### 8.1 Category Records

```sql
INSERT INTO CATEGORY VALUES
(1,'Computer Science','Programming and Database Books');

INSERT INTO CATEGORY VALUES
(2,'Mathematics','Mathematics Reference Books');

INSERT INTO CATEGORY VALUES
(3,'Literature','English Literature Books');
```

#### 8.2 Author Records

```sql
INSERT INTO AUTHOR VALUES
(1,'Abraham Silberschatz','Database Systems Author');

INSERT INTO AUTHOR VALUES
(2,'E Balagurusamy','Programming Author');

INSERT INTO AUTHOR VALUES
(3,'R S Aggarwal','Mathematics Author');

INSERT INTO AUTHOR VALUES
(4,'William Shakespeare','Literature Author');
```

#### 8.3 Publisher Records

```sql
INSERT INTO PUBLISHER VALUES
(1,'Tech Publications','9876500001');

INSERT INTO PUBLISHER VALUES
(2,'Education Books','9876500002');
```

#### 8.4 Member Records

```sql
INSERT INTO MEMBER VALUES
(101,'Arun Kumar','arun@gmail.com','9000000001',
TO_DATE('01-01-2026','DD-MM-YYYY'),'STUDENT');

INSERT INTO MEMBER VALUES
(102,'Bala Devi','bala@gmail.com','9000000002',
TO_DATE('05-01-2026','DD-MM-YYYY'),'STUDENT');

INSERT INTO MEMBER VALUES
(103,'Charan Raj','charan@gmail.com','9000000003',
TO_DATE('10-01-2026','DD-MM-YYYY'),'STAFF');

INSERT INTO MEMBER VALUES
(104,'Divya Sri','divya@gmail.com','9000000004',
TO_DATE('15-01-2026','DD-MM-YYYY'),'STUDENT');

INSERT INTO MEMBER VALUES
(105,'Elango','elango@gmail.com','9000000005',
TO_DATE('20-01-2026','DD-MM-YYYY'),'STUDENT');
```

#### 8.5 Book Records

```sql
INSERT INTO BOOK VALUES
(201,'ISBN001','Oracle Database',1,1,1,650,5,4);

INSERT INTO BOOK VALUES
(202,'ISBN002','Python Programming',1,2,1,500,4,3);

INSERT INTO BOOK VALUES
(203,'ISBN003','Java Programming',1,2,2,550,6,5);

INSERT INTO BOOK VALUES
(204,'ISBN004','Mathematics for Engineers',2,3,2,400,5,5);

INSERT INTO BOOK VALUES
(205,'ISBN005','English Literature',3,4,1,350,3,3);
```

#### 8.6 Book Issue Records

```sql
INSERT INTO BOOK_ISSUE VALUES
(301,201,101,TO_DATE('01-10-2026','DD-MM-YYYY'),
TO_DATE('15-10-2026','DD-MM-YYYY'),'RETURNED');

INSERT INTO BOOK_ISSUE VALUES
(302,202,102,TO_DATE('05-10-2026','DD-MM-YYYY'),
TO_DATE('19-10-2026','DD-MM-YYYY'),'ISSUED');

INSERT INTO BOOK_ISSUE VALUES
(303,203,103,TO_DATE('07-10-2026','DD-MM-YYYY'),
TO_DATE('21-10-2026','DD-MM-YYYY'),'RETURNED');

INSERT INTO BOOK_ISSUE VALUES
(304,204,101,TO_DATE('10-10-2026','DD-MM-YYYY'),
TO_DATE('24-10-2026','DD-MM-YYYY'),'ISSUED');

INSERT INTO BOOK_ISSUE VALUES
(305,205,104,TO_DATE('12-10-2026','DD-MM-YYYY'),
TO_DATE('26-10-2026','DD-MM-YYYY'),'RETURNED');
```

#### 8.7 Book Return Records

```sql
INSERT INTO BOOK_RETURN VALUES
(401,301,TO_DATE('14-10-2026','DD-MM-YYYY'),0,'PAID');

INSERT INTO BOOK_RETURN VALUES
(402,303,TO_DATE('20-10-2026','DD-MM-YYYY'),0,'PAID');

INSERT INTO BOOK_RETURN VALUES
(403,305,TO_DATE('25-10-2026','DD-MM-YYYY'),10,'PAID');
```

#### 8.8 Saving the Records – COMMIT

After inserting the records, used COMMIT to save the changes.

```sql
COMMIT;
```

