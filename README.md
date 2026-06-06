# University Management System

## Project Overview

The University Management System is a SQL-based database project designed to manage and organize university data efficiently. The system stores information about departments, professors, students, courses, and enrollments while demonstrating various SQL concepts and database operations.

---

## Objectives

* Manage university departments and academic programs.
* Store professor and student records.
* Maintain course information and enrollments.
* Demonstrate SQL commands, constraints, joins, functions, procedures, triggers, transactions, and views.

---

## Database Name

```sql
University
```

---

## Database Structure

### 1. Departments Table

Stores information about university departments.

| Column         | Data Type    | Description     |
| -------------- | ------------ | --------------- |
| DepartmentID   | INT          | Primary Key     |
| DepartmentName | VARCHAR(255) | Department Name |

---

### 2. Professors Table

Stores professor information.

| Column       | Data Type     |
| ------------ | ------------- |
| ProfessorID  | INT (PK)      |
| FirstName    | VARCHAR(100)  |
| LastName     | VARCHAR(100)  |
| DepartmentID | INT (FK)      |
| Salary       | DECIMAL(10,2) |

---

### 3. Students Table

Stores student information.

| Column         | Data Type    |
| -------------- | ------------ |
| StudentID      | INT (PK)     |
| FirstName      | VARCHAR(100) |
| LastName       | VARCHAR(100) |
| Age            | INT          |
| Gender         | VARCHAR(10)  |
| DepartmentID   | INT (FK)     |
| EnrollmentDate | DATE         |
| Address        | VARCHAR(255) |
| Email          | VARCHAR(100) |
| Contact        | VARCHAR(15)  |

---

### 4. Courses Table

Stores course information.

| Column       | Data Type    |
| ------------ | ------------ |
| CourseID     | INT (PK)     |
| CourseName   | VARCHAR(255) |
| DepartmentID | INT (FK)     |
| ProfessorID  | INT (FK)     |
| Credits      | INT          |

---

### 5. Enrollments Table

Stores student course registrations.

| Column         | Data Type |
| -------------- | --------- |
| EnrollmentID   | INT (PK)  |
| StudentID      | INT (FK)  |
| CourseID       | INT (FK)  |
| EnrollmentDate | DATE      |
| Grade          | CHAR(1)   |

---

## Relationships

* One Department can have many Professors.
* One Department can have many Students.
* One Department can offer many Courses.
* One Professor can teach multiple Courses.
* One Student can enroll in multiple Courses.
* One Course can have multiple Students.

---

## SQL Concepts Implemented

### Basic Queries

* SELECT
* SELECT DISTINCT
* WHERE Clause
* ORDER BY
* AND, OR, NOT Operators

### Data Manipulation

* INSERT
* UPDATE
* DELETE

### Aggregate Functions

* MIN()
* MAX()
* AVG()
* SUM()
* COUNT()

### Filtering

* LIKE
* IN
* BETWEEN
* IS NULL

### Joins

* INNER JOIN
* LEFT JOIN
* RIGHT JOIN
* FULL JOIN

### Set Operations

* UNION
* UNION ALL

### Grouping

* GROUP BY
* HAVING

### Advanced SQL

* EXISTS
* ANY
* ALL
* CASE Statement
* SELECT INTO

### Database Objects

* Stored Procedures
* User Defined Functions
* Views
* Indexes
* Triggers

### Transaction Handling

* BEGIN TRANSACTION
* COMMIT
* ROLLBACK
* TRY-CATCH Error Handling

---

## Stored Procedure

### GetProfessorsByDepartment

Returns professor details of a specific department.

```sql
EXEC GetProfessorsByDepartment 1;
```

---

## User Defined Function

### displayStudent()

Returns details of a specific student.

```sql
SELECT * FROM displayStudent(2);
```

---

## Trigger

### UpdateGrade

Automatically updates grade information after an update operation on the Enrollments table.

---

## View

### View1

Displays students whose StudentID is less than 7.

```sql
SELECT FirstName
FROM View1
WHERE StudentID = 5;
```

---

## Sample Reports Generated

* Student List
* Department-wise Student Count
* Professor Salary Analysis
* Course Enrollment Details
* Student Grade Information

---

## Technologies Used

* SQL Server
* T-SQL
* Relational Database Management System (RDBMS)

---

## Learning Outcomes

Through this project, students can learn:

* Database Design
* Table Relationships
* Primary and Foreign Keys
* Data Manipulation Language (DML)
* Data Definition Language (DDL)
* SQL Joins
* Aggregate Functions
* Stored Procedures
* Functions
* Views
* Triggers
* Transactions
* Indexing Techniques

---

## Conclusion

The University Management System demonstrates the practical implementation of SQL concepts in a real-world academic environment. It provides an efficient structure for managing university data while showcasing essential database management techniques and advanced SQL features.


# Installation and Setup Guide (SQL Server)

## Prerequisites

Before running the project, install:

1. Microsoft SQL Server
2. SQL Server Management Studio (SSMS)

---

## Step 1: Open SQL Server Management Studio (SSMS)

* Launch SQL Server Management Studio.
* Connect to your SQL Server instance using Windows Authentication or SQL Server Authentication.
* Click **Connect**.

---

## Step 2: Create a New Query

* In Object Explorer, select your server.
* Click **New Query** from the toolbar.
* A new SQL query window will open.

---

## Step 3: Copy the Project Script

* Open the University Management System SQL file.
* Copy the complete SQL script.
* Paste it into the query window.

---

## Step 4: Execute the Script

Click the **Execute** button or press **F5**.

The script will:

* Create the University database.
* Create all tables.
* Define relationships using foreign keys.
* Insert sample records.
* Create procedures, functions, triggers, views, and indexes.

---

## Step 5: Verify Database Creation

In Object Explorer:

1. Expand **Databases**.
2. Refresh the database list.
3. Verify that the **University** database appears.

---

## Step 6: Select the Database

Run:

```sql
USE University;
```

This makes University the active database.

---

## Step 7: Verify Tables

Run:

```sql
SELECT * FROM Departments;
SELECT * FROM Professors;
SELECT * FROM Students;
SELECT * FROM Courses;
SELECT * FROM Enrollments;
```

If records are displayed, the setup is successful.

---

## Step 8: Test Stored Procedure

Run:

```sql
EXEC GetProfessorsByDepartment 1;
```

Expected Result:

* Displays professors belonging to Department ID 1.

---

## Step 9: Test Function

Run:

```sql
SELECT * FROM displayStudent(2);
```

Expected Result:

* Displays details of Student ID 2.

---

## Step 10: Test View

Run:

```sql
SELECT * FROM View1;
```

Expected Result:

* Displays students having StudentID less than 7.

---

## Step 11: Test Trigger

Run:

```sql
UPDATE Enrollments
SET Grade = 'A'
WHERE EnrollmentID = 1;
```

Then verify:

```sql
SELECT * FROM Enrollments
WHERE EnrollmentID = 1;
```

Expected Result:

* Trigger automatically updates the grade according to its logic.

---

## Step 12: Test Transaction

Run:

```sql
BEGIN TRANSACTION

UPDATE Students
SET Age = 25
WHERE StudentID = 3;

COMMIT;
```

Verify:

```sql
SELECT * FROM Students
WHERE StudentID = 3;
```

---

## Project Structure

University Database
│
├── Departments
├── Professors
├── Students
├── Courses
├── Enrollments
│
├── Stored Procedure
│   └── GetProfessorsByDepartment
│
├── Function
│   └── displayStudent()
│
├── Trigger
│   └── UpdateGrade
│
├── View
│   └── View1
│
└── Index
└── idx_student_name

---

## Troubleshooting

### Error: Database Already Exists

If the University database already exists, run:

```sql
DROP DATABASE University;
```

Then execute the project script again.

### Error Near GO Statement

Make sure the script is executed in SQL Server Management Studio (SSMS), as GO is recognized by SSMS.

### Foreign Key Constraint Error

Execute the script in the provided order:

1. Departments
2. Professors
3. Students
4. Courses
5. Enrollments

This ensures parent tables are created before child tables.

---

## How to Run Again Later

1. Open SSMS.
2. Connect to SQL Server.
3. Expand Databases.
4. Select University database.
5. Click New Query.
6. Execute any SELECT, INSERT, UPDATE, DELETE, or testing queries.
