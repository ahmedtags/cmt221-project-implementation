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
