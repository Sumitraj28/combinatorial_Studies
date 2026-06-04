# Unit III: DBMS - Lab Practicals

This guide contains complete SQL queries, PL/SQL blocks, and database scripts for **Practical 5: SQL Commands** and **Practical 6: PL/SQL Triggers, Procedures, & Functions**.

---

## 💻 Practical 5: SQL Commands (DDL, DML, TCL)

Let's build a database schema for a company department and write operational queries.

### 5.1 Data Definition Language (DDL)
DDL defines database structures and constraints.

```sql
-- 1. Create a Departments Table
CREATE TABLE Departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(50) NOT NULL,
    location VARCHAR(50)
);

-- 2. Create an Employees Table with Constraints
CREATE TABLE Employees (
    emp_id INT PRIMARY KEY,
    emp_name VARCHAR(50) NOT NULL,
    salary DECIMAL(10, 2) CHECK (salary > 0),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES Departments(dept_id)
);

-- 3. Alter Table to add an Email Column
ALTER TABLE Employees ADD email VARCHAR(100);

-- 4. Truncate Employees table (Removes rows but keeps schema)
-- TRUNCATE TABLE Employees;

-- 5. Drop Employees table (Removes schema and data)
-- DROP TABLE Employees;
```

### 5.2 Data Manipulation Language (DML)
DML is used to query and modify records.

```sql
-- Insert Sample Departments
INSERT INTO Departments VALUES (10, 'Engineering', 'New York');
INSERT INTO Departments VALUES (20, 'Human Resources', 'Chicago');
INSERT INTO Departments VALUES (30, 'Sales', 'San Francisco');

-- Insert Sample Employees
INSERT INTO Employees VALUES (101, 'Alice Smith', 85000.00, 10, 'alice@company.com');
INSERT INTO Employees VALUES (102, 'Bob Jones', 60000.00, 10, 'bob@company.com');
INSERT INTO Employees VALUES (103, 'Charlie Brown', 55000.00, 20, 'charlie@company.com');
INSERT INTO Employees VALUES (104, 'Diana Prince', 95000.00, 30, 'diana@company.com');

-- Update Employee Salary
UPDATE Employees SET salary = 90000.00 WHERE emp_id = 101;

-- Delete an Employee
DELETE FROM Employees WHERE emp_id = 103;

-- Complex SELECT Query: INNER JOIN with GROUP BY and HAVING
-- Retrieve department names and their average salaries where average salary is > 65,000
SELECT d.dept_name, AVG(e.salary) AS avg_salary
FROM Employees e
INNER JOIN Departments d ON e.dept_id = d.dept_id
GROUP BY d.dept_name
HAVING AVG(e.salary) > 65000;
```

### 5.3 Transaction Control Language (TCL)
TCL controls transaction flow.

```sql
-- Start Transaction Scenario
INSERT INTO Employees VALUES (105, 'Evan Wright', 50000.00, 20, 'evan@company.com');
SAVEPOINT sp1; -- Set a restore point

-- Modify salary
UPDATE Employees SET salary = 55000.00 WHERE emp_id = 105;
SAVEPOINT sp2;

-- Oops, made a mistake. Rollback to sp1.
ROLLBACK TO sp1;

-- Commit the transaction (Saves Evan with salary = 50000.00)
COMMIT;
```

---

## 💻 Practical 6: PL/SQL Programming

PL/SQL extends SQL with procedural logic (loops, conditionals, variables).

### 6.1 Database Prep
First, let's create an audit table to capture salary modification logs:

```sql
CREATE TABLE SalaryAuditLog (
    audit_id INT GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    emp_id INT,
    old_salary DECIMAL(10, 2),
    new_salary DECIMAL(10, 2),
    update_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 6.2 PL/SQL Stored Procedure
Procedures execute business tasks. This procedure takes an Employee ID and a raise percentage, updates their salary, and prints details.

```sql
CREATE OR REPLACE PROCEDURE GiveSalaryRaise (
    p_emp_id IN INT,
    p_percentage IN DECIMAL
) IS
    v_old_salary DECIMAL(10,2);
    v_new_salary DECIMAL(10,2);
BEGIN
    -- Fetch current salary
    SELECT salary INTO v_old_salary FROM Employees WHERE emp_id = p_emp_id;
    
    -- Calculate new salary
    v_new_salary := v_old_salary + (v_old_salary * (p_percentage / 100));
    
    -- Update salary
    UPDATE Employees SET salary = v_new_salary WHERE emp_id = p_emp_id;
    
    DBMS_OUTPUT.PUT_LINE('Employee ID: ' || p_emp_id || ' Old Salary: ' || v_old_salary || ' New Salary: ' || v_new_salary);
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('Error: Employee ' || p_emp_id || ' does not exist.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred.');
END;
/
```

*   **To run the procedure**:
    ```sql
    EXEC GiveSalaryRaise(101, 10); -- Give 10% raise to Alice
    ```

### 6.3 PL/SQL Stored Function
Functions calculate and return values. This function returns the total number of employees in a department.

```sql
CREATE OR REPLACE FUNCTION GetDeptEmpCount (
    p_dept_id IN INT
) RETURN INT IS
    v_count INT := 0;
BEGIN
    SELECT COUNT(*) INTO v_count FROM Employees WHERE dept_id = p_dept_id;
    RETURN v_count;
END;
/
```

*   **To run the function**:
    ```sql
    SELECT GetDeptEmpCount(10) AS engineering_count FROM dual;
    ```

### 6.4 PL/SQL Database Trigger
Triggers fire automatically in response to database changes. This trigger logs salary changes in `SalaryAuditLog` whenever an update is executed on `Employees`.

```sql
CREATE OR REPLACE TRIGGER AuditSalaryUpdate
AFTER UPDATE OF salary ON Employees
FOR EACH ROW
BEGIN
    -- Insert a log record if the salary was modified
    IF :OLD.salary <> :NEW.salary THEN
        INSERT INTO SalaryAuditLog (emp_id, old_salary, new_salary)
        VALUES (:OLD.emp_id, :OLD.salary, :NEW.salary);
    END IF;
END;
/
```

*   **To test the trigger**:
    ```sql
    -- Update Alice's salary
    UPDATE Employees SET salary = 95000.00 WHERE emp_id = 101;

    -- Check audit logs
    SELECT * FROM SalaryAuditLog;
    ```
