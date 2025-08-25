
## 1. DML (Data Manipulation Language)

- **Definition**: Commands to manipulate data within tables for insertion, updating, and deletion.
    
- **Key Points**: Manages table content, critical for maintaining university records like student data.
    
- **All Uses**:
    
    - **INSERT**: Add single/multiple rows, specific columns, or from queries.
    - **UPDATE**: Modify one/multiple columns conditionally or across rows.
    - **DELETE**: Remove specific or all rows based on conditions.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates a Students table.
    CREATE TABLE Students (StudentID INT PRIMARY KEY, Name VARCHAR(100), Department VARCHAR(50), Status VARCHAR(20));
    ```
    
    ```sql
    -- No output as CREATE defines structure, no data yet.
    ```
    
    - **Output Explanation**: `CREATE` sets up the Students table with columns. No data inserted, so no output from a SELECT query.
    
    ```sql
    -- What it does: Inserts multiple student records.
    INSERT INTO Students VALUES 
        (1001, 'Amit Sharma', 'Computer Science', 'Active'),
        (1002, 'Priya Patel', 'Mathematics', 'Active'),
        (1003, 'Rahul Verma', 'Physics', 'Inactive'),
        (1004, 'Sneha Gupta', 'Mathematics', 'Active');
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name         | Department      | Status
    1001      | Amit Sharma  | Computer Science| Active
    1002      | Priya Patel  | Mathematics     | Active
    1003      | Rahul Verma  | Physics         | Inactive
    1004      | Sneha Gupta  | Mathematics     | Active
    ```
    
    - **Output Explanation**: `INSERT` adds four student rows. `SELECT` shows all rows with their details.
    
    ```sql
    -- What it does: Updates department for Mathematics students.
    UPDATE Students SET Department = 'Data Science' WHERE Department = 'Mathematics';
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name         | Department      | Status
    1001      | Amit Sharma  | Computer Science| Active
    1002      | Priya Patel  | Data Science    | Active
    1003      | Rahul Verma  | Physics         | Inactive
    1004      | Sneha Gupta  | Data Science    | Active
    ```
    
    - **Output Explanation**: `UPDATE` changes Department to 'Data Science' for IDs 1002 and 1004 (previously Mathematics). `SELECT` shows updated departments.
    
    ```sql
    -- What it does: Deletes inactive students.
    DELETE FROM Students WHERE Status = 'Inactive';
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name         | Department      | Status
    1001      | Amit Sharma  | Computer Science| Active
    1002      | Priya Patel  | Data Science    | Active
    1004      | Sneha Gupta  | Data Science    | Active
    ```
    
    - **Output Explanation**: `DELETE` removes ID 1003 (Inactive). `SELECT` shows remaining active students.

## 2. DDL (Data Definition Language)

- **Definition**: Commands to define or modify database structures like tables or schemas.
    
- **Key Points**: Shapes the database framework, essential for university system setup.
    
- **All Uses**:
    
    - **CREATE**: Define tables, databases, indexes.
    - **ALTER**: Add, modify, drop columns/constraints.
    - **DROP**: Delete tables or databases.
    - **TRUNCATE**: Clear all table data, keep structure.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates a Courses table.
    CREATE TABLE Courses (CourseID INT PRIMARY KEY, CourseName VARCHAR(100), Department VARCHAR(50));
    ```
    
    ```sql
    -- No output as CREATE defines structure.
    ```
    
    - **Output Explanation**: `CREATE` sets up the Courses table. No data, so no output.
    
    ```sql
    -- What it does: Inserts course records.
    INSERT INTO Courses VALUES 
        (201, 'Database Systems', 'Computer Science'),
        (202, 'Calculus', 'Mathematics'),
        (203, 'Physics Lab', 'Physics');
    ```
    
    ```sql
    SELECT * FROM Courses;
    CourseID | CourseName       | Department
    201      | Database Systems | Computer Science
    202      | Calculus         | Mathematics
    203      | Physics Lab      | Physics
    ```
    
    - **Output Explanation**: `INSERT` adds three courses. `SELECT` shows all course records.
    
    ```sql
    -- What it does: Adds a Credits column to Courses.
    ALTER TABLE Courses ADD Credits INT DEFAULT 3;
    ```
    
    ```sql
    SELECT * FROM Courses;
    CourseID | CourseName       | Department      | Credits
    201      | Database Systems | Computer Science| 3
    202      | Calculus         | Mathematics     | 3
    203      | Physics Lab      | Physics         | 3
    ```
    
    - **Output Explanation**: `ALTER` adds Credits column with default 3. `SELECT` shows all courses with new column.
    
    ```sql
    -- What it does: Updates Credits for one course.
    UPDATE Courses SET Credits = 4 WHERE CourseID = 201;
    ```
    
    ```sql
    SELECT * FROM Courses;
    CourseID | CourseName       | Department      | Credits
    201      | Database Systems | Computer Science| 4
    202      | Calculus         | Mathematics     | 3
    203      | Physics Lab      | Physics         | 3
    ```
    
    - **Output Explanation**: `UPDATE` sets Credits to 4 for CourseID 201. `SELECT` shows updated Credits.
    
    ```sql
    -- What it does: Truncates all data from Courses.
    TRUNCATE TABLE Courses;
    ```
    
    ```sql
    SELECT * FROM Courses;
    CourseID | CourseName | Department | Credits
    -- Empty (no rows)
    ```
    
    - **Output Explanation**: `TRUNCATE` removes all rows but keeps table structure. `SELECT` shows empty table.
    
    ```sql
    -- What it does: Drops the Courses table.
    DROP TABLE Courses;
    ```
    
    ```sql
    -- No output as table is dropped.
    ```
    
    - **Output Explanation**: `DROP` deletes the table entirely. No output as table no longer exists.

## 3. DQL (Data Query Language)

- **Definition**: Command to retrieve data from tables based on criteria.
- **Key Points**: Fetches data for university reports or analysis.
- **All Uses**:
    - **SELECT**: Retrieve all/specific columns, with conditions (WHERE), sorting (ORDER BY), limiting (LIMIT).
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Students table, inserts data, queries active Computer Science students, sorted by name.
    CREATE TABLE Students (StudentID INT PRIMARY KEY, Name VARCHAR(100), Department VARCHAR(50), Status VARCHAR(20));
    INSERT INTO Students VALUES 
        (1001, 'Amit Sharma', 'Computer Science', 'Active'),
        (1002, 'Priya Patel', 'Mathematics', 'Active'),
        (1003, 'Rahul Verma', 'Computer Science', 'Active'),
        (1004, 'Sneha Gupta', 'Mathematics', 'Inactive'),
        (1005, 'Vikram Singh', 'Computer Science', 'Active');
    SELECT StudentID, Name 
    FROM Students 
    WHERE Department = 'Computer Science' AND Status = 'Active' 
    ORDER BY Name 
    LIMIT 2;
    ```
    
    ```sql
    StudentID | Name
    1001      | Amit Sharma
    1003      | Rahul Verma
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds five students. `SELECT` filters for active Computer Science students (IDs 1001, 1003, 1005), sorts by Name, limits to 2 rows, showing Amit and Rahul (alphabetically first).

## 4. DCL (Data Control Language)

- **Definition**: Commands to manage database access and permissions.
    
- **Key Points**: Ensures secure access to university data (e.g., restricting student record access).
    
- **All Uses**:
    
    - **GRANT**: Assigns privileges.
    - **REVOKE**: Removes privileges.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Students table for permission management.
    CREATE TABLE Students (StudentID INT PRIMARY KEY, Name VARCHAR(100));
    ```
    
    ```sql
    -- No output as CREATE defines structure.
    ```
    
    - **Output Explanation**: `CREATE` sets up Students table. No data, so no output.
    
    ```sql
    -- What it does: Grants SELECT and INSERT permissions to registrar user.
    GRANT SELECT, INSERT ON Students TO 'registrar'@'localhost';
    ```
    
    ```sql
    -- No output as GRANT affects permissions.
    ```
    
    - **Output Explanation**: `GRANT` gives registrar read and write access. No data output.
    
    ```sql
    -- What it does: Revokes INSERT permission from registrar.
    REVOKE INSERT ON Students FROM 'registrar'@'localhost';
    ```
    
    ```sql
    -- No output as REVOKE affects permissions.
    ```
    
    - **Output Explanation**: `REVOKE` removes write access, leaving only read. No data output.

## 5. TCL (Transaction Control Language)

- **Definition**: Commands to manage transactions for data consistency.
    
- **Key Points**: Ensures reliable updates in university systems (e.g., enrollment changes).
    
- **All Uses**:
    
    - **COMMIT**: Saves changes.
    - **ROLLBACK**: Undoes changes to last commit/savepoint.
    - **SAVEPOINT**: Marks a point for partial rollback.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Students table for transaction management.
    CREATE TABLE Students (StudentID INT PRIMARY KEY, Name VARCHAR(100), Status VARCHAR(20));
    ```
    
    ```sql
    -- No output as CREATE defines structure.
    ```
    
    - **Output Explanation**: `CREATE` sets up table. No data, so no output.
    
    ```sql
    -- What it does: Starts transaction, inserts students.
    START TRANSACTION;
    INSERT INTO Students VALUES 
        (1001, 'Amit Sharma', 'Active'),
        (1002, 'Priya Patel', 'Active'),
        (1003, 'Rahul Verma', 'Active');
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name        | Status
    1001      | Amit Sharma | Active
    1002      | Priya Patel | Active
    1003      | Rahul Verma | Active
    ```
    
    - **Output Explanation**: `START TRANSACTION` begins. `INSERT` adds three students. `SELECT` shows all rows (transaction not committed yet).
    
    ```sql
    -- What it does: Sets a savepoint and updates status.
    SAVEPOINT sp1;
    UPDATE Students SET Status = 'Inactive' WHERE StudentID = 1002;
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name        | Status
    1001      | Amit Sharma | Active
    1002      | Priya Patel | Inactive
    1003      | Rahul Verma | Active
    ```
    
    - **Output Explanation**: `SAVEPOINT sp1` marks state. `UPDATE` changes Priya’s status to Inactive. `SELECT` shows updated status.
    
    ```sql
    -- What it does: Rolls back to savepoint and commits.
    ROLLBACK TO sp1;
    COMMIT;
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name        | Status
    1001      | Amit Sharma | Active
    1002      | Priya Patel | Active
    1003      | Rahul Verma | Active
    ```
    
    - **Output Explanation**: `ROLLBACK TO sp1` undoes status change for 1002. `COMMIT` saves all data. `SELECT` shows original statuses.

## 6. Keys

- **Definition**: Constraints to ensure data integrity and relationships.
    
- **Key Points**: Maintains unique IDs and valid links in university databases.
    
- **All Uses**:
    
    - **PRIMARY KEY**: Unique, non-null identifier.
    - **FOREIGN KEY**: Links to another table’s key.
    - **UNIQUE**: No duplicates (allows NULL).
    - **CHECK**: Enforces conditions.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Department table with primary key.
    CREATE TABLE Department (DeptID INT PRIMARY KEY, DeptName VARCHAR(50));
    ```
    
    ```sql
    -- No output as CREATE defines structure.
    ```
    
    - **Output Explanation**: `CREATE` sets up Department with DeptID as unique identifier. No data yet.
    
    ```sql
    -- What it does: Inserts department records.
    INSERT INTO Department VALUES 
        (1, 'Computer Science'),
        (2, 'Mathematics'),
        (3, 'Physics');
    ```
    
    ```sql
    SELECT * FROM Department;
    DeptID | DeptName
    1      | Computer Science
    2      | Mathematics
    3      | Physics
    ```
    
    - **Output Explanation**: `INSERT` adds three departments. `SELECT` shows all rows with unique DeptIDs.
    
    ```sql
    -- What it does: Creates Students table with all key constraints.
    CREATE TABLE Students (
        StudentID INT PRIMARY KEY AUTO_INCREMENT,
        Name VARCHAR(100) NOT NULL,
        Email VARCHAR(100) UNIQUE,
        Grade VARCHAR(1) CHECK (Grade IN ('A', 'B', 'C')),
        DeptID INT,
        FOREIGN KEY (DeptID) REFERENCES Department(DeptID)
    );
    ```
    
    ```sql
    -- No output as CREATE defines structure.
    ```
    
    - **Output Explanation**: `CREATE` sets up Students with constraints: auto-incrementing StudentID, non-null Name, unique Email, valid Grade, linked DeptID. No data yet.
    
    ```sql
    -- What it does: Inserts valid student records.
    INSERT INTO Students (Name, Email, Grade, DeptID) VALUES 
        ('Amit Sharma', 'amit@uni.com', 'A', 1),
        ('Priya Patel', 'priya@uni.com', 'B', 2),
        ('Rahul Verma', 'rahul@uni.com', 'C', 3);
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name        | Email          | Grade | DeptID
    1         | Amit Sharma | amit@uni.com   | A     | 1
    2         | Priya Patel | priya@uni.com  | B     | 2
    3         | Rahul Verma | rahul@uni.com  | C     | 3
    ```
    
    - **Output Explanation**: `INSERT` adds three valid students (existing DeptIDs, unique emails, valid grades). `SELECT` shows auto-incremented StudentIDs and all data.

## 7. Operators

- **Definition**: Symbols for arithmetic, comparison, or logical operations.
    
- **Key Points**: Filters or computes data for university queries (e.g., student performance).
    
- **All Uses**:
    
    - **Arithmetic**: `+`, `-`, `*`, `/`, `%`.
    - **Comparison**: `=`, `!=`, `>`, `<`, `LIKE`, `IN`.
    - **Logical**: `AND`, `OR`, `NOT`.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Students table and inserts data.
    CREATE TABLE Students (StudentID INT PRIMARY KEY, Name VARCHAR(100), Marks INT);
    INSERT INTO Students VALUES 
        (1001, 'Amit Sharma', 80),
        (1002, 'Priya Patel', 90),
        (1003, 'Rahul Verma', 85),
        (1004, 'Sneha Gupta', 75);
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name        | Marks
    1001      | Amit Sharma | 80
    1002      | Priya Patel | 90
    1003      | Rahul Verma | 85
    1004      | Sneha Gupta | 75
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds four students. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Uses operators to filter and compute bonus marks.
    SELECT StudentID, Name, Marks * 1.2 AS BonusMarks 
    FROM Students 
    WHERE Marks > 80 AND Name LIKE 'P%' OR StudentID IN (1001, 1003);
    ```
    
    ```sql
    StudentID | Name        | BonusMarks
    1001      | Amit Sharma | 96.0
    1002      | Priya Patel | 108.0
    1003      | Rahul Verma | 102.0
    ```
    
    - **Output Explanation**: `SELECT` uses `*` to increase Marks by 20% (e.g., 80 * 1.2 = 96), filters with `>` (Marks > 80), `LIKE` (names starting with 'P'), `IN` (IDs 1001, 1003), and `OR`/`AND`. Shows Amit (ID 1001), Priya (Marks 90, starts with 'P'), Rahul (ID 1003).

## 8. Set Operators

- **Definition**: Combine results from multiple queries.
    
- **Key Points**: Merges university data for analysis, removing duplicates unless specified.
    
- **All Uses**:
    
    - **UNION**: Unique rows.
    - **UNION ALL**: All rows (with duplicates).
    - **INTERSECT**: Common rows.
    - **EXCEPT**: Rows in first query not in second.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates CS_Students table and inserts data.
    CREATE TABLE CS_Students (StudentID INT, Name VARCHAR(100));
    INSERT INTO CS_Students VALUES 
        (1001, 'Amit Sharma'),
        (1002, 'Priya Patel'),
        (1003, 'Rahul Verma');
    ```
    
    ```sql
    SELECT * FROM CS_Students;
    StudentID | Name
    1001      | Amit Sharma
    1002      | Priya Patel
    1003      | Rahul Verma
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds three students. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Creates Math_Students table and inserts data.
    CREATE TABLE Math_Students (StudentID INT, Name VARCHAR(100));
    INSERT INTO Math_Students VALUES 
        (1002, 'Priya Patel'),
        (1004, 'Sneha Gupta'),
        (1005, 'Vikram Singh');
    ```
    
    ```sql
    SELECT * FROM Math_Students;
    StudentID | Name
    1002      | Priya Patel
    1004      | Sneha Gupta
    1005      | Vikram Singh
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds three students. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Combines students with UNION and INTERSECT.
    SELECT StudentID, Name FROM CS_Students 
    UNION 
    SELECT StudentID, Name FROM Math_Students;
    SELECT StudentID, Name FROM CS_Students 
    INTERSECT 
    SELECT StudentID, Name FROM Math_Students;
    ```
    
    ```sql
    -- UNION output
    StudentID | Name
    1001      | Amit Sharma
    1002      | Priya Patel
    1003      | Rahul Verma
    1004      | Sneha Gupta
    1005      | Vikram Singh
    -- INTERSECT output
    StudentID | Name
    1002      | Priya Patel
    ```
    
    - **Output Explanation**: `UNION` combines unique students from both tables (all five, duplicates removed). `INTERSECT` shows only Priya (ID 1002, in both). `SELECT` displays results separately.

## 9. Aggregate Functions

- **Definition**: Calculate a single value from multiple rows.
    
- **Key Points**: Summarizes data for university reports (e.g., department performance).
    
- **All Uses**:
    
    - **COUNT**: Count rows/values.
    - **SUM**: Sum values.
    - **AVG**: Average values.
    - **MAX**: Highest value.
    - **MIN**: Lowest value.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Student_Marks table and inserts data.
    CREATE TABLE Student_Marks (StudentID INT, Department VARCHAR(50), Marks INT);
    INSERT INTO Student_Marks VALUES 
        (1001, 'Computer Science', 80),
        (1002, 'Computer Science', 90),
        (1003, 'Mathematics', 70),
        (1004, 'Mathematics', 85),
        (1005, 'Physics', 75);
    ```
    
    ```sql
    SELECT * FROM Student_Marks;
    StudentID | Department      | Marks
    1001      | Computer Science| 80
    1002      | Computer Science| 90
    1003      | Mathematics     | 70
    1004      | Mathematics     | 85
    1005      | Physics         | 75
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds five student marks. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Calculates summary statistics by department.
    SELECT Department, 
           COUNT(*) AS TotalStudents, 
           SUM(Marks) AS TotalMarks, 
           AVG(Marks) AS AvgMarks, 
           MAX(Marks) AS Highest, 
           MIN(Marks) AS Lowest 
    FROM Student_Marks 
    GROUP BY Department;
    ```
    
    ```sql
    Department      | TotalStudents | TotalMarks | AvgMarks | Highest | Lowest
    Computer Science| 2             | 170        | 85.0000  | 90      | 80
    Mathematics     | 2             | 155        | 77.5000  | 85      | 70
    Physics         | 1             | 75         | 75.0000  | 75      | 75
    ```
    
    - **Output Explanation**: `SELECT` groups by Department. `COUNT` counts students (CS: 2, Math: 2, Physics: 1). `SUM` adds marks (170, 155, 75). `AVG` computes averages (170/2=85, etc.). `MAX`/`MIN` find highest/lowest marks. Shows results per department.

## 10. GROUP BY

- **Definition**: Groups rows with identical values for aggregation.
    
- **Key Points**: Organizes data for summary reports (e.g., department-wise performance).
    
- **All Uses**:
    
    - Group by one/multiple columns, with aggregates.
    - Use with HAVING to filter groups.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Students table and inserts data.
    CREATE TABLE Students (StudentID INT, Department VARCHAR(50), Marks INT);
    INSERT INTO Students VALUES 
        (1001, 'Computer Science', 80),
        (1002, 'Computer Science', 90),
        (1003, 'Mathematics', 70),
        (1004, 'Mathematics', 85),
        (1005, 'Physics', 60),
        (1006, 'Computer Science', 95);
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Department      | Marks
    1001      | Computer Science| 80
    1002      | Computer Science| 90
    1003      | Mathematics     | 70
    1004      | Mathematics     | 85
    1005      | Physics         | 60
    1006      | Computer Science| 95
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds six students. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Groups by department, counts students, filters high-performing departments.
    SELECT Department, COUNT(*) AS StudentCount, AVG(Marks) AS AvgMarks 
    FROM Students 
    GROUP BY Department 
    HAVING AVG(Marks) > 85;
    ```
    
    ```sql
    Department      | StudentCount | AvgMarks
    Computer Science| 3            | 88.3333
    ```
    
    - **Output Explanation**: `GROUP BY` groups by Department (CS: 3, Math: 2, Physics: 1). `COUNT` counts students. `AVG` computes marks (CS: (80+90+95)/3=88.3333, Math: 77.5, Physics: 60). `HAVING` filters for AvgMarks > 85, showing only Computer Science.

## 11. Views

- **Definition**: Virtual tables based on SELECT queries.
    
- **Key Points**: Simplifies complex queries for university reports.
    
- **All Uses**:
    
    - **CREATE VIEW**: Define a view.
    - **DROP VIEW**: Delete a view.
    - Variations: Simple, complex, updatable views.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Students table and inserts data.
    CREATE TABLE Students (StudentID INT PRIMARY KEY, Name VARCHAR(100), Marks INT);
    INSERT INTO Students VALUES 
        (1001, 'Amit Sharma', 80),
        (1002, 'Priya Patel', 95),
        (1003, 'Rahul Verma', 70),
        (1004, 'Sneha Gupta', 90),
        (1005, 'Vikram Singh', 85);
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name        | Marks
    1001      | Amit Sharma | 80
    1002      | Priya Patel | 95
    1003      | Rahul Verma | 70
    1004      | Sneha Gupta | 90
    1005      | Vikram Singh| 85
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds five students. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Creates a view for top performers.
    CREATE VIEW TopStudents AS 
    SELECT StudentID, Name, Marks 
    FROM Students 
    WHERE Marks >= 90;
    ```
    
    ```sql
    SELECT * FROM TopStudents;
    StudentID | Name        | Marks
    1002      | Priya Patel | 95
    1004      | Sneha Gupta | 90
    ```
    
    - **Output Explanation**: `CREATE VIEW` defines a virtual table for Marks >= 90. `SELECT` from view shows Priya and Sneha.
    
    ```sql
    -- What it does: Drops the view.
    DROP VIEW TopStudents;
    ```
    
    ```sql
    -- No output as view is dropped.
    ```
    
    - **Output Explanation**: `DROP` removes the view. No output as view no longer exists.

## 12. Joins

- **Definition**: Combine rows from multiple tables based on conditions.
    
- **Key Points**: Links related university data (e.g., students and enrollments).
    
- **All Uses**:
    
    - **INNER JOIN**: Matching rows only.
    - **LEFT JOIN**: All left table rows, NULL for unmatched right.
    - **RIGHT JOIN**: All right table rows, NULL for unmatched left.
    - **FULL OUTER JOIN**: All rows from both, NULL for non-matches.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Students table and inserts data.
    CREATE TABLE Students (StudentID INT PRIMARY KEY, Name VARCHAR(100));
    INSERT INTO Students VALUES 
        (1001, 'Amit Sharma'),
        (1002, 'Priya Patel'),
        (1003, 'Rahul Verma'),
        (1004, 'Sneha Gupta');
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name
    1001      | Amit Sharma
    1002      | Priya Patel
    1003      | Rahul Verma
    1004      | Sneha Gupta
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds four students. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Creates Enrollments table and inserts data.
    CREATE TABLE Enrollments (StudentID INT, CourseID INT, CourseName VARCHAR(100));
    INSERT INTO Enrollments VALUES 
        (1001, 201, 'Database Systems'),
        (1002, 202, 'Calculus'),
        (1004, 203, 'Physics Lab');
    ```
    
    ```sql
    SELECT * FROM Enrollments;
    StudentID | CourseID | CourseName
    1001      | 201      | Database Systems
    1002      | 202      | Calculus
    1004      | 203      | Physics Lab
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds three enrollments. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Joins Students and Enrollments with LEFT JOIN.
    SELECT Students.StudentID, Name, CourseName 
    FROM Students 
    LEFT JOIN Enrollments ON Students.StudentID = Enrollments.StudentID;
    ```
    
    ```sql
    StudentID | Name        | CourseName
    1001      | Amit Sharma | Database Systems
    1002      | Priya Patel | Calculus
    1003      | Rahul Verma | NULL
    1004      | Sneha Gupta | Physics Lab
    ```
    
    - **Output Explanation**: `LEFT JOIN` keeps all Students, matches Enrollments where StudentID equals. Rahul (1003) has no enrollment, so CourseName is NULL.

## 13. Query Structuring

- **Definition**: Keywords to organize queries for clarity or reusability.
    
- **Key Points**: Enhances readability in complex university queries.
    
- **All Uses**:
    
    - **AS**: Aliases columns/tables.
    - **WITH**: Defines CTEs for reusable subqueries.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Students table and inserts data.
    CREATE TABLE Students (StudentID INT, Department VARCHAR(50), Marks INT);
    INSERT INTO Students VALUES 
        (1001, 'Computer Science', 80),
        (1002, 'Computer Science', 95),
        (1003, 'Mathematics', 70),
        (1004, 'Mathematics', 90),
        (1005, 'Physics', 85);
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Department      | Marks
    1001      | Computer Science| 80
    1002      | Computer Science| 95
    1003      | Mathematics     | 70
    1004      | Mathematics     | 90
    1005      | Physics         | 85
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds five students. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Uses WITH and AS to summarize high performers.
    WITH HighPerformers AS (
        SELECT StudentID, Department, Marks AS Score 
        FROM Students 
        WHERE Marks >= 90
    )
    SELECT Department, COUNT(*) AS TopCount 
    FROM HighPerformers 
    GROUP BY Department;
    ```
    
    ```sql
    Department      | TopCount
    Computer Science| 1
    Mathematics     | 1
    ```
    
    - **Output Explanation**: `WITH` creates a CTE for students with Marks >= 90 (IDs 1002, 1004). `AS` aliases Marks as Score. `SELECT` counts rows per department in CTE (one each).

## 14. String Functions

- **Definition**: Functions to manipulate text data.
    
- **Key Points**: Formats text for university reports (e.g., student names).
    
- **All Uses**:
    
    - **CONCAT**: Joins strings.
    - **LENGTH**: Counts characters.
    - **UPPER/LOWER**: Changes case.
    - **SUBSTRING**: Extracts part.
    - **TRIM**: Removes spaces.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Students table and inserts data.
    CREATE TABLE Students (StudentID INT, Name VARCHAR(100), Department VARCHAR(50));
    INSERT INTO Students VALUES 
        (1001, '  Amit Sharma  ', 'Computer Science'),
        (1002, 'Priya Patel', 'Mathematics'),
        (1003, '  Rahul Verma  ', 'Physics'),
        (1004, 'Sneha Gupta', 'Mathematics');
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name          | Department
    1001      |   Amit Sharma | Computer Science
    1002      | Priya Patel   | Mathematics
    1003      |   Rahul Verma | Physics
    1004      | Sneha Gupta   | Mathematics
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds four students, some with extra spaces. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Formats names with string functions.
    SELECT StudentID, 
           CONCAT(UPPER(TRIM(Name)), ' - ', Department) AS FormattedName, 
           LENGTH(Name) AS NameLength 
    FROM Students;
    ```
    
    ```sql
    StudentID | FormattedName                  | NameLength
    1001      | AMIT SHARMA - Computer Science | 14
    1002      | PRIYA PATEL - Mathematics      | 11
    1003      | RAHUL VERMA - Physics          | 14
    1004      | SNEHA GUPTA - Mathematics      | 11
    ```
    
    - **Output Explanation**: `TRIM` removes spaces from names, `UPPER` converts to uppercase, `CONCAT` adds Department. `LENGTH` counts original Name characters (including spaces). `SELECT` shows formatted names and lengths.

## 15. Numeric Functions

- **Definition**: Functions for numerical calculations.
    
- **Key Points**: Computes values for university data (e.g., grades).
    
- **All Uses**:
    
    - **ABS**: Absolute value.
    - **ROUND**: Rounds to decimals.
    - **CEIL**: Rounds up.
    - **FLOOR**: Rounds down.
    - **MOD**: Remainder.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Student_Marks table and inserts data.
    CREATE TABLE Student_Marks (StudentID INT, Marks FLOAT);
    INSERT INTO Student_Marks VALUES 
        (1001, 85.567),
        (1002, 92.345),
        (1003, 78.912),
        (1004, 88.123);
    ```
    
    ```sql
    SELECT * FROM Student_Marks;
    StudentID | Marks
    1001      | 85.567
    1002      | 92.345
    1003      | 78.912
    1004      | 88.123
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds four student marks. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Applies numeric functions to marks.
    SELECT StudentID, 
           ROUND(Marks, 1) AS RoundedMarks, 
           CEIL(Marks) AS CeilingMarks, 
           MOD(Marks, 10) AS Remainder 
    FROM Student_Marks;
    ```
    
    ```sql
    StudentID | RoundedMarks | CeilingMarks | Remainder
    1001      | 85.6        | 86           | 5
    1002      | 92.3        | 93           | 2
    1003      | 78.9        | 79           | 8
    1004      | 88.1        | 89           | 8
    ```
    
    - **Output Explanation**: `ROUND` rounds to 1 decimal (e.g., 85.567 to 85.6). `CEIL` rounds up (85.567 to 86). `MOD` gives remainder (85.567 % 10 ≈ 5). `SELECT` shows computed values.

## 16. Date/Time Functions

- **Definition**: Functions to handle date and time data.
    
- **Key Points**: Manages temporal data for university events or deadlines.
    
- **All Uses**:
    
    - **NOW()**: Current date/time.
    - **DATE_ADD**: Adds interval.
    - **DATEDIFF**: Days between dates.
    - **CURDATE()**: Current date.
    - **CURTIME()**: Current time.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Course_Deadlines table and inserts data.
    CREATE TABLE Course_Deadlines (CourseID INT, Deadline DATE);
    INSERT INTO Course_Deadlines VALUES 
        (201, '2025-07-15'),
        (202, '2025-08-01'),
        (203, '2025-08-15'),
        (204, '2025-09-01');
    ```
    
    ```sql
    SELECT * FROM Course_Deadlines;
    CourseID | Deadline
    201      | 2025-07-15
    202      | 2025-08-01
    203      | 2025-08-15
    204      | 2025-09-01
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds four deadlines. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Applies date functions to deadlines.
    SELECT CourseID, 
           DATE_ADD(Deadline, INTERVAL 7 DAY) AS ExtendedDeadline, 
           DATEDIFF(CURDATE(), Deadline) AS DaysSince 
    FROM Course_Deadlines 
    WHERE Deadline < CURDATE();
    ```
    
    ```sql
    CourseID | ExtendedDeadline | DaysSince
    201      | 2025-07-22      | 42
    202      | 2025-08-08      | 25
    203      | 2025-08-22      | 11
    ```
    
    - **Output Explanation**: `WHERE` filters for deadlines before 2025-08-26 (excludes 204). `DATE_ADD` adds 7 days (e.g., 2025-07-15 to 2025-07-22). `DATEDIFF` calculates days to 2025-08-26 (e.g., 42 for 201). `SELECT` shows results.

## 17. Control Flow Functions

- **Definition**: Functions for conditional logic in queries.
    
- **Key Points**: Adds dynamic logic for university data (e.g., grading).
    
- **All Uses**:
    
    - **IF**: Returns value based on condition.
    - **CASE**: Multi-condition logic.
    - **COALESCE**: First non-NULL value.
    - **NULLIF**: NULL if values equal.
- **Example** (MySQL, University System):
    
    ```sql
    -- What it does: Creates Students table and inserts data.
    CREATE TABLE Students (StudentID INT, Name VARCHAR(100), Email VARCHAR(100), Marks INT);
    INSERT INTO Students VALUES 
        (1001, 'Amit Sharma', NULL, 80),
        (1002, 'Priya Patel', 'priya@uni.com', 95),
        (1003, 'Rahul Verma', NULL, 70),
        (1004, 'Sneha Gupta', 'sneha@uni.com', 90),
        (1005, 'Vikram Singh', 'vikram@uni.com', 85);
    ```
    
    ```sql
    SELECT * FROM Students;
    StudentID | Name        | Email          | Marks
    1001      | Amit Sharma | NULL           | 80
    1002      | Priya Patel | priya@uni.com  | 95
    1003      | Rahul Verma | NULL           | 70
    1004      | Sneha Gupta | sneha@uni.com  | 90
    1005      | Vikram Singh| vikram@uni.com | 85
    ```
    
    - **Output Explanation**: `CREATE` sets up table. `INSERT` adds five students, some with NULL emails. `SELECT` shows all rows.
    
    ```sql
    -- What it does: Applies control flow to categorize grades and handle NULLs.
    SELECT StudentID, 
           Name, 
           COALESCE(Email, 'No Email') AS Contact, 
           CASE 
               WHEN Marks >= 90 THEN 'Excellent'
               WHEN Marks >= 80 THEN 'Good'
               ELSE 'Average'
           END AS Grade 
    FROM Students;
    ```
    
    ```sql
    StudentID | Name        | Contact         | Grade
    1001      | Amit Sharma | No Email        | Good
    1002      | Priya Patel | priya@uni.com   | Excellent
    1003      | Rahul Verma | No Email        | Average
    1004      | Sneha Gupta | sneha@uni.com   | Excellent
    1005      | Vikram Singh| vikram@uni.com  | Good
    ```
    
    - **Output Explanation**: `COALESCE` replaces NULL emails with 'No Email'. `CASE` assigns grades: ≥90 (Excellent), ≥80 (Good), else Average. `SELECT` shows results with computed grades.