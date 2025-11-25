

# 📘 PL/SQL Project — Collections, Records & GOTO Statements

**Student Name:** IGIHOZO Regine Pacis

**Student ID:** 27703

**Lecturer:** Maniraguha Eric

**Course:** PL/SQL Programming

**Institution:** Adventist University of Central Africa

**Academic Year:** 2025–2026

---

## 🧭 Table of Contents

1. [Project Overview](#1-project-overview)
2. [Objectives](#2-objectives)
3. [Tools & Requirements](#3-tools--requirements)
4. [Database Design](#4-database-design)
5. [PLSQL Features Demonstrated](#5-plsql-features-demonstrated)

   * [a. Collections](#a-collections)
   * [b. Records](#b-records)
   * [c. GOTO Statement](#c-goto-statement)
6. [Sample Code](#6-sample-code)
7. [Expected Output](#8-expected-output)
8. [Conclusion](#9-conclusion)
9. [Author Information](#10-author-information)

---

## 1️⃣ Project Overview

This project demonstrates the use of **PL/SQL advanced concepts** — specifically **Collections**, **Records**, and **GOTO statements** — using a **school management scenario**.
The main idea is to manage student data, such as names and marks, and process results with PL/SQL blocks.

---

## 2️⃣ Objectives

* To understand and apply **Collections** in PL/SQL for handling groups of related data.
* To use **Records** for managing structured data within PL/SQL.
* To demonstrate the **GOTO statement** for conditional control flow.
* To design clear, documented PL/SQL code with practical examples.

---

## 3️⃣ Tools & Requirements

* **Database:** Oracle Database 23ai (or any version supporting PL/SQL)
* **Editor:** Oracle SQL Developer
* **Language:** PL/SQL

---

## 4️⃣ Database Design

This project simulates a **school area** with sample students:

| Student_ID | Student_Name   | Subject          | Marks | Grade | Status |
| ---------- | -------------- | ---------------- | ----- | ----- | ------ |
| 1          | Baziga Caleb   | Database Systems | 85    | A     | Passed |
| 2          | Nkuranga Sabin | Database Systems | 65    | C     | Passed |
| 3          | Muneza         | Database Systems | 35    | F     | Failed |
| 4          | Ngabo Prince   | Database Systems | 90    | A     | Passed |
| 5          | Uwase Aline    | Database Systems | 75    | B     | Passed |


* Baziga Caleb
* Nkuranga Sabin
* Muneza
* Ngabo Prince
* Uwase Aline

The system stores their names and marks, calculates grades, and skips students who failed using a `GOTO` statement.

---

## 5️⃣ PLSQL Features Demonstrated

### a. Collections

Used to store and iterate over multiple student names and marks.
**Example:** Associative Array & Nested Table.
<img width="1920" height="1008" alt="3PLSQL Collections" src="https://github.com/user-attachments/assets/e7c84a9f-f508-4496-9196-e45efe633fea" />


### b. Records

Used to store student information (ID, name, marks, and grade) as a single record.

<img width="1920" height="1008" alt="4 PLSQL Records" src="https://github.com/user-attachments/assets/3e2ddebb-beb2-47f6-bcec-16d3afea3610" />




### c. GOTO Statement

Used to skip processing for students who fail (for learning purposes).

<img width="1920" height="1008" alt="5 PLSQL GOTO" src="https://github.com/user-attachments/assets/9d412e58-ea59-4cce-9ed0-b041b41c4b71" />


---

## 6️⃣ Sample Code

```sql
SET SERVEROUTPUT ON;

DECLARE
  -- Collection for names
  TYPE student_names IS TABLE OF VARCHAR2(50) INDEX BY PLS_INTEGER;
  students student_names;

  -- Collection for marks
  TYPE student_marks IS TABLE OF NUMBER INDEX BY PLS_INTEGER;
  marks student_marks;

  -- Record type
  TYPE student_record IS RECORD (
    id NUMBER,
    name VARCHAR2(50),
    mark NUMBER,
    grade CHAR(1)
  );
  s student_record;

  i NUMBER;
BEGIN
  -- Assign values
  students(1) := 'Baziga Caleb';
  students(2) := 'Nkuranga Sabin';
  students(3) := 'Muneza';
  students(4) := 'Ngabo Prince';

  marks(1) := 85;
  marks(2) := 65;
  marks(3) := 35;
  marks(4) := 90;

  DBMS_OUTPUT.PUT_LINE('=== STUDENT RESULTS ===');

  FOR i IN 1 .. students.COUNT LOOP
    s.id := i;
    s.name := students(i);
    s.mark := marks(i);

    -- Use GOTO to skip failed students
    IF s.mark < 40 THEN
      GOTO skip_student;
    END IF;

    -- Determine grade
    IF s.mark >= 80 THEN
      s.grade := 'A';
    ELSIF s.mark >= 70 THEN
      s.grade := 'B';
    ELSE
      s.grade := 'C';
    END IF;

    DBMS_OUTPUT.PUT_LINE(s.id || '. ' || s.name || ' - ' || s.mark || ' - Grade ' || s.grade);
    CONTINUE;
    
    <<skip_student>>
    DBMS_OUTPUT.PUT_LINE(s.name || ' failed and was skipped.');
  END LOOP;
END;
/
```
<img width="1920" height="1008" alt="3PLSQL Collections" src="https://github.com/user-attachments/assets/3fa6e709-5228-4e8e-a83d-d459d42a99ae" />

---



---

## 7️⃣ Expected Output

```
=== STUDENT RESULTS ===
1. Baziga Caleb - 85 - Grade A
2. Nkuranga Sabin - 65 - Grade C
Muneza failed and was skipped.
4. Ngabo Prince - 90 - Grade A
```
<img width="960" height="504" alt="image" src="https://github.com/user-attachments/assets/381f56ea-2029-47b1-8eb2-fe2e799f0d86" />

---

## 8️⃣ Conclusion

This project successfully demonstrates how **PL/SQL Collections, Records, and GOTO statements** can be used in a real-world scenario.
By simulating a school environment, we learned how to store, process, and control the flow of data efficiently in PL/SQL.

---

## 9️⃣ Author Information

**Name:** Nkuranga Baziga Caleb
**Student ID:** 28845
**Lecturer:** Maniraguha Eric
**Course:** PL/SQL Programming
**Academic Year:** 2025–2026

---f
