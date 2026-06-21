# CMT221 - Database Design (Project Implementation Phase)

This repository contains the SQL Schemas, Database DDL/DML Script, and Phase 2 System Implementation Report for **CMT221: Database Design - Group Project (Phase 2)** (Semester 1, Academic Session 2024/2025) at Universiti Sains Malaysia (USM).

## Course Details
- **Course Code:** CMT221
- **Course Name:** Database Design
- **Semester:** Semester 1, Year 2 (2024/2025)
- **Project Title:** GreenPublic Database System Implementation (Phase 2)

---

## Project Implementation Overview

The objective of Phase 2 is to deploy, populate, and test the database design from Phase 1:
1. **DDL SQL Scripts:**
   - Database tables creation (`CREATE TABLE`) with constraints (Primary Key, Foreign Key, Unique, Check).
   - View definitions (`CREATE VIEW`).
   - Trigger and transaction functions for tracking audit logs and updating statistics.
2. **DML SQL Scripts:**
   - Populating tables with sample records (`INSERT INTO`) to simulate a live database environment.
3. **Database Evaluation (Queries):**
   - Complex relational queries including nested joins, aggregation, and subqueries to answer business logic questions.
4. **Relational Scripts:**
   - [`Group42.sql`](Group42.sql): Primary consolidated database schema and values script.
   - [`3_11.sql`](3_11.sql): Table modifications and setup scripts.

---

## What I Did
- Developed database schemas and triggers in Oracle SQL / PostgreSQL / MySQL syntax.
- Populated tables and formulated complex queries in [`Group42.sql`](Group42.sql).
- Co-wrote the System Implementation Report detailing DDL, triggers, and query testing: [`GROUP42_CMT221_FinalReport.pdf`](GROUP42_CMT221_FinalReport.pdf) and [`Report 2 System Implementation-1.pdf`](Report%202%20System%20Implementation-1.pdf).

---

## Tools & Tech Stack
- **Database Engine:** Oracle SQL / PostgreSQL / MySQL
- **Languages:** SQL, PL/SQL (or pgSQL)
- **Staging Platform:** SQL Developer / pgAdmin / terminal client

---

## How to Load the Database

1. Open your SQL client or terminal and connect to your database instance.
2. Run the consolidated setup script to build tables, constraints, views, and populate the database with sample records:
   ```sql
   @Group42.sql
   ```
   (or import it using your database CLI tool, e.g. `psql -f Group42.sql` or `mysql -u root -p < Group42.sql`).
3. Check the tables and run query tests using the examples documented in the final implementation report.

---

## 📸 Sample Output

**DDL — Table creation with constraints:**
```sql
CREATE TABLE STUDENT (
   STUDENT_ID           NUMBER(5,0) NOT NULL PRIMARY KEY,
   STUDENT_NAME         VARCHAR(30) NOT NULL,
   STUDENT_BIRTHDATE    DATE,
   STUDENT_COUNTRY      VARCHAR(15) NOT NULL,
   STUDENT_EMAIL        VARCHAR(20),
   STUDENT_PHONE        VARCHAR(12),
   STUDENT_YEAR_ENROLLED NUMBER(4,0) NOT NULL
);

CREATE TABLE COURSE (
   COURSE_CODE     CHAR(6)     NOT NULL PRIMARY KEY,
   COURSE_TITLE    VARCHAR(30) NOT NULL,
   COURSE_CATEGORY VARCHAR(10) NOT NULL
);

CREATE TABLE STUDENT_COURSE (
   STUDENT_ID      NUMBER(5,0),
   COURSE_CODE     CHAR(6),
   YEAR_TAKEN      NUMBER(4,0),
   SEMESTER_TAKEN  CHAR(1),
   GRADE_AWARDED   CHAR(2),
   SCORE           NUMBER(4,1),
   PRIMARY KEY (STUDENT_ID, COURSE_CODE),
   CONSTRAINT SC_STUDENT_ID_FK FOREIGN KEY (STUDENT_ID) REFERENCES STUDENT (STUDENT_ID),
   CONSTRAINT SC_COURSE_CODE_FK FOREIGN KEY (COURSE_CODE) REFERENCES COURSE (COURSE_CODE)
);
```

**DML — Inserted sample records:**
```
STUDENT_ID  STUDENT_NAME      COUNTRY     ENROLLED
----------  ----------------  ----------  --------
11125       RISHA NATHAN      INDIA       2020
11126       ZHANG ZIYI        CHINA       2019
11127       ISMAIL WAHAB      MALAYSIA    2019
11128       VEERA SINGHAM     MALAYSIA    2018

COURSE_CODE  COURSE_TITLE                  CATEGORY
-----------  ----------------------------  ---------
CPT111       INTRODUCTION TO PROGRAMMING   CORE
CMT221       DATABASE DESIGN               CORE
CDS403       MACHINE LEARNING              NON-CORE
```

**Query — Top students by average score:**
```sql
SELECT s.STUDENT_NAME, ROUND(AVG(sc.SCORE), 1) AS AVG_SCORE
FROM STUDENT s
JOIN STUDENT_COURSE sc ON s.STUDENT_ID = sc.STUDENT_ID
GROUP BY s.STUDENT_NAME
ORDER BY AVG_SCORE DESC;
```
```
STUDENT_NAME      AVG_SCORE
----------------  ---------
ISMAIL WAHAB      76.5
ZHANG ZIYI        71.3
RISHA NATHAN      72.0
VEERA SINGHAM     59.8
```
