# Online Library Management System – Week 3
## SQL Data Definition Language (DDL)

### Week 3 – Creating and Managing Database Tables

### 1. Introduction
DDL commands help create database tables and manage their structure. Used these commands to set up the basic tables required for storing library-related information.

### 2. DDL Commands Covered

| Command | Description |
|---|---|
| CREATE | Creates a new table |
| DESC | Displays the structure of a table |
| ALTER | Adds or modifies table columns |
| RENAME | Changes an existing table name |
| TRUNCATE | Removes all records from a table |
| DROP | Deletes a table completely |

### 3. Creating Database Tables

Created the following tables to organize the information in the library database.

#### 3.1 Category Table

This table stores different categories of books available in the library.

```sql
CREATE TABLE CATEGORY (
    CATEGORY_ID NUMBER(4) PRIMARY KEY,
    CATEGORY_NAME VARCHAR2(40) NOT NULL UNIQUE,
    DESCRIPTION VARCHAR2(100)
);
```

#### 3.2 Author Table

This table maintains information about book authors.

```sql
CREATE TABLE AUTHOR (
    AUTHOR_ID NUMBER(4) PRIMARY KEY,
    AUTHOR_NAME VARCHAR2(60) NOT NULL,
    BIOGRAPHY VARCHAR2(200)
);
```

#### 3.3 Publisher Table

This table stores publisher details and their contact information.

```sql
CREATE TABLE PUBLISHER (
    PUBLISHER_ID NUMBER(4) PRIMARY KEY,
    PUBLISHER_NAME VARCHAR2(60) NOT NULL,
    CONTACT_NO VARCHAR2(15)
);
```

#### 3.4 Member Table

This table contains the details of people registered with the library.

```sql
CREATE TABLE MEMBER (
    MEMBER_ID NUMBER(5) PRIMARY KEY,
    MEMBER_NAME VARCHAR2(60) NOT NULL,
    EMAIL VARCHAR2(80) UNIQUE,
    PHONE VARCHAR2(15),
    JOIN_DATE DATE DEFAULT SYSDATE,
    MEMBER_TYPE VARCHAR2(10)
);
```

#### 3.5 Book Table

This table stores book information and connects books with their respective categories, authors and publishers.

```sql
CREATE TABLE BOOK (
    BOOK_ID NUMBER(5) PRIMARY KEY,
    ISBN VARCHAR2(20) UNIQUE,
    TITLE VARCHAR2(100) NOT NULL,
    CATEGORY_ID NUMBER(4),
    AUTHOR_ID NUMBER(4),
    PUBLISHER_ID NUMBER(4),
    PRICE NUMBER(8,2),
    TOTAL_COPIES NUMBER(4),
    AVAILABLE_COPIES NUMBER(4),
    FOREIGN KEY (CATEGORY_ID) REFERENCES CATEGORY(CATEGORY_ID),
    FOREIGN KEY (AUTHOR_ID) REFERENCES AUTHOR(AUTHOR_ID),
    FOREIGN KEY (PUBLISHER_ID) REFERENCES PUBLISHER(PUBLISHER_ID)
);
```

#### 3.6 Book Issue Table

This table records the details of books issued to library members, including issue dates and due dates.

```sql
CREATE TABLE BOOK_ISSUE (
    ISSUE_ID NUMBER(6) PRIMARY KEY,
    BOOK_ID NUMBER(5),
    MEMBER_ID NUMBER(5),
    ISSUE_DATE DATE,
    DUE_DATE DATE,
    RETURN_STATUS VARCHAR2(10),
    FOREIGN KEY (BOOK_ID) REFERENCES BOOK(BOOK_ID),
    FOREIGN KEY (MEMBER_ID) REFERENCES MEMBER(MEMBER_ID)
);
```

#### 3.7 Book Return Table

This table maintains book return information, including applicable fines and payment status.

```sql
CREATE TABLE BOOK_RETURN (
    RETURN_ID NUMBER(6) PRIMARY KEY,
    ISSUE_ID NUMBER(6),
    RETURN_DATE DATE,
    FINE_AMOUNT NUMBER(8,2),
    PAYMENT_STATUS VARCHAR2(10),
    FOREIGN KEY (ISSUE_ID) REFERENCES BOOK_ISSUE(ISSUE_ID)
);
```

### 4. Checking Table Structures

After creating the tables, I used the DESC command to verify their column names and data types.

```sql
DESC CATEGORY;
DESC AUTHOR;
DESC PUBLISHER;
DESC MEMBER;
DESC BOOK;
DESC BOOK_ISSUE;
DESC BOOK_RETURN;
```

### 5. Modifying Table Structure – ALTER

I created a separate practice table and used ALTER TABLE to add a new column.

```sql
CREATE TABLE DDL_PRACTICE (
    TEST_ID NUMBER(3),
    TEST_NAME VARCHAR2(30)
);

ALTER TABLE DDL_PRACTICE
ADD REMARKS VARCHAR2(50);
```

### 6. Changing Table Name – RENAME

Changing the name of an existing table and then restoring its original name.

```sql
RENAME DDL_PRACTICE TO DDL_PRACTICE_NEW;

RENAME DDL_PRACTICE_NEW TO DDL_PRACTICE;
```

### 7. Removing Table Records – TRUNCATE

Used TRUNCATE to remove all records from the practice table while retaining its structure.

```sql
TRUNCATE TABLE DDL_PRACTICE;
```

### 8. Deleting a Table – DROP

Used DROP TABLE to remove the practice table completely.

```sql
DROP TABLE DDL_PRACTICE;
```
