Here are some essential MySQL commands categorized for different tasks:

### **1. Database Management**
```sql
SHOW DATABASES;                      -- List all databases
CREATE DATABASE db_name;              -- Create a new database
DROP DATABASE db_name;                -- Delete a database
USE db_name;                          -- Switch to a database
```

### **2. Table Management**
```sql
SHOW TABLES;                          -- List all tables in the current database
CREATE TABLE table_name (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);                                    -- Create a new table

DESCRIBE table_name;                  -- Show table structure
DROP TABLE table_name;                -- Delete a table
TRUNCATE TABLE table_name;             -- Remove all records from a table but keep the structure
ALTER TABLE table_name ADD column_name VARCHAR(255); -- Add a new column
ALTER TABLE table_name DROP COLUMN column_name;      -- Remove a column
```

### **3. Data Manipulation (DML)**
```sql
-- Insert Data
INSERT INTO table_name (name, age) VALUES ('Alice', 25);

-- Select Data
SELECT * FROM table_name;
SELECT name FROM table_name WHERE age > 20;

-- Update Data
UPDATE table_name SET age = 30 WHERE name = 'Alice';

-- Delete Data
DELETE FROM table_name WHERE name = 'Alice';
```

### **4. Filtering & Sorting**
```sql
SELECT * FROM table_name WHERE age > 20 ORDER BY age DESC;  -- Sort by age in descending order
SELECT * FROM table_name LIMIT 5;                           -- Limit results to 5 rows
SELECT DISTINCT name FROM table_name;                       -- Get unique names
```

### **5. Joins**
```sql
-- Inner Join
SELECT a.id, a.name, b.salary
FROM employees a
INNER JOIN salaries b ON a.id = b.emp_id;

-- Left Join
SELECT a.id, a.name, b.salary
FROM employees a
LEFT JOIN salaries b ON a.id = b.emp_id;

-- Right Join
SELECT a.id, a.name, b.salary
FROM employees a
RIGHT JOIN salaries b ON a.id = b.emp_id;
```

### **6. Aggregate Functions**
```sql
SELECT COUNT(*) FROM table_name;      -- Count total records
SELECT AVG(age) FROM table_name;      -- Average age
SELECT SUM(salary) FROM employees;    -- Sum of salaries
SELECT MAX(salary) FROM employees;    -- Maximum salary
SELECT MIN(salary) FROM employees;    -- Minimum salary
```

### **7. Indexing**
```sql
CREATE INDEX idx_name ON table_name (column_name);  -- Create an index
DROP INDEX idx_name ON table_name;                  -- Drop an index
```

### **8. User & Access Control**
```sql
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON db_name.* TO 'username'@'localhost';
FLUSH PRIVILEGES; -- Apply changes
```

Would you like any specific MySQL queries or explanations? 🚀