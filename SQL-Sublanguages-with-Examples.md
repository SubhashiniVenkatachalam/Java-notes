# SQL Sub-Languages — With Syntax & Examples

> **Memory trick: "D D D D T" = 4 D's, 1 T**

---

## DDL — Data Definition Language
Deals with the **structure** of the table.

### CREATE
```sql
CREATE TABLE students (
    id   INT PRIMARY KEY,
    name VARCHAR(50),
    age  INT,
    city VARCHAR(50)
);
```

### ALTER
```sql
-- Add a new column
ALTER TABLE students ADD email VARCHAR(100);

-- Modify a column type
ALTER TABLE students MODIFY age VARCHAR(3);
```

### DROP
```sql
-- Deletes the table and all its data permanently
DROP TABLE students;
```

### TRUNCATE
```sql
-- Removes all rows but keeps the table structure
TRUNCATE TABLE students;
```

### RENAME
```sql
ALTER TABLE students RENAME TO learners;
```

---

## DML — Data Manipulation Language
Used to **manipulate data** inside the table.

### INSERT
```sql
-- Insert one row
INSERT INTO students VALUES (1, 'Selbin', 21, 'Salem');

-- Insert specific columns
INSERT INTO students (id, name) VALUES (2, 'Subha');
```

### UPDATE
```sql
-- Update a specific row
UPDATE students SET city = 'Chennai' WHERE id = 1;

-- Update multiple columns
UPDATE students SET age = 22, city = 'Coimbatore' WHERE name = 'Selbin';
```

### DELETE
```sql
-- Delete a specific row
DELETE FROM students WHERE id = 1;

-- Delete all rows (keeps table structure — similar to TRUNCATE but slower)
DELETE FROM students;
```

---

## DQL — Data Query Language
Used to **query / read data** from the table.

### SELECT
```sql
-- Get all columns and all rows
SELECT * FROM students;

-- Get specific columns
SELECT name, city FROM students;

-- With condition
SELECT * FROM students WHERE city = 'Salem';

-- With ordering
SELECT * FROM students ORDER BY age DESC;

-- With limit
SELECT * FROM students LIMIT 5;
```

---

## DCL — Data Control Language
Controls **access** to the data.

### GRANT
```sql
-- Give SELECT permission to a user
GRANT SELECT ON students TO 'username'@'localhost';

-- Give all permissions
GRANT ALL PRIVILEGES ON students TO 'username'@'localhost';
```

### REVOKE
```sql
-- Remove SELECT permission from a user
REVOKE SELECT ON students FROM 'username'@'localhost';
```

---

## TCL — Transaction Control Language
Used to **manage transactions** (save / undo operations).

### COMMIT
```sql
-- Save all changes permanently
INSERT INTO students VALUES (3, 'Ravi', 23, 'Madurai');
COMMIT;
```

### ROLLBACK
```sql
-- Undo all changes since last COMMIT
DELETE FROM students WHERE id = 3;
ROLLBACK;  -- row comes back
```

### SAVEPOINT
```sql
-- Set a checkpoint
SAVEPOINT sp1;

DELETE FROM students WHERE id = 2;

-- Undo only back to sp1, not a full rollback
ROLLBACK TO sp1;

COMMIT;
```

> `COMMIT` = save permanently, `ROLLBACK` = undo, `SAVEPOINT` = checkpoint to rollback to
