# SQL
SQL CLI commands

Here’s an extensive list of SQL commands and techniques, including commands for various SQL dialects and advanced operations.

### **1. SQL Basics**

- **Create a Database:**
  ```sql
  CREATE DATABASE mydatabase;
  ```

- **Drop a Database:**
  ```sql
  DROP DATABASE mydatabase;
  ```

- **Create a Table:**
  ```sql
  CREATE TABLE mytable (
      id INT PRIMARY KEY,
      name VARCHAR(100),
      age INT
  );
  ```

- **Drop a Table:**
  ```sql
  DROP TABLE mytable;
  ```

- **Insert Data:**
  ```sql
  INSERT INTO mytable (id, name, age) VALUES (1, 'John Doe', 30);
  ```

- **Select Data:**
  ```sql
  SELECT * FROM mytable;
  ```

- **Update Data:**
  ```sql
  UPDATE mytable SET age = 31 WHERE id = 1;
  ```

- **Delete Data:**
  ```sql
  DELETE FROM mytable WHERE id = 1;
  ```

### **2. Advanced SQL Techniques**

- **Join Tables:**
  ```sql
  SELECT a.name, b.department
  FROM employees a
  JOIN departments b ON a.department_id = b.id;
  ```

- **Group By and Having:**
  ```sql
  SELECT department, COUNT(*) as count
  FROM employees
  GROUP BY department
  HAVING COUNT(*) > 5;
  ```

- **Subqueries:**
  ```sql
  SELECT name
  FROM employees
  WHERE department_id = (SELECT id FROM departments WHERE name = 'HR');
  ```

- **Window Functions:**
  ```sql
  SELECT name, salary, RANK() OVER (ORDER BY salary DESC) as rank
  FROM employees;
  ```

- **Common Table Expressions (CTEs):**
  ```sql
  WITH SalesCTE AS (
      SELECT product_id, SUM(amount) as total_sales
      FROM sales
      GROUP BY product_id
  )
  SELECT product_id, total_sales
  FROM SalesCTE
  WHERE total_sales > 1000;
  ```

### **3. MySQL Specific Commands**

- **Show Databases:**
  ```sql
  SHOW DATABASES;
  ```

- **Show Tables:**
  ```sql
  SHOW TABLES;
  ```

- **Describe Table:**
  ```sql
  DESCRIBE mytable;
  ```

- **Show Create Table:**
  ```sql
  SHOW CREATE TABLE mytable;
  ```

- **Backup Database:**
  ```bash
  mysqldump -u username -p mydatabase > backup.sql
  ```

- **Restore Database:**
  ```bash
  mysql -u username -p mydatabase < backup.sql
  ```

### **4. PostgreSQL Specific Commands**

- **Connect to Database:**
  ```bash
  psql -U username -d mydatabase
  ```

- **List Databases:**
  ```sql
  \l
  ```

- **List Tables:**
  ```sql
  \dt
  ```

- **Describe Table:**
  ```sql
  \d mytable
  ```

- **Backup Database:**
  ```bash
  pg_dump -U username mydatabase > backup.sql
  ```

- **Restore Database:**
  ```bash
  psql -U username mydatabase < backup.sql
  ```

### **5. SQLite Specific Commands**

- **Open Database:**
  ```bash
  sqlite3 mydatabase.db
  ```

- **List Tables:**
  ```sql
  .tables
  ```

- **Describe Table:**
  ```sql
  PRAGMA table_info(mytable);
  ```

- **Backup Database:**
  ```bash
  sqlite3 mydatabase.db .dump > backup.sql
  ```

- **Restore Database:**
  ```bash
  sqlite3 mydatabase.db < backup.sql
  ```

### **6. Microsoft SQL Server Specific Commands**

- **Connect to Database:**
  ```sql
  sqlcmd -S servername -U username -P password -d mydatabase
  ```

- **List Databases:**
  ```sql
  SELECT name FROM sys.databases;
  ```

- **List Tables:**
  ```sql
  SELECT table_name FROM information_schema.tables WHERE table_type = 'BASE TABLE';
  ```

- **Describe Table:**
  ```sql
  sp_help mytable;
  ```

- **Backup Database:**
  ```sql
  BACKUP DATABASE mydatabase TO DISK = 'C:\backup\mydatabase.bak';
  ```

- **Restore Database:**
  ```sql
  RESTORE DATABASE mydatabase FROM DISK = 'C:\backup\mydatabase.bak';
  ```

### **7. Oracle SQL Specific Commands**

- **Connect to Database:**
  ```sql
  sqlplus username/password@//hostname:port/service_name
  ```

- **List Databases:**
  ```sql
  SELECT name FROM v$database;
  ```

- **List Tables:**
  ```sql
  SELECT table_name FROM user_tables;
  ```

- **Describe Table:**
  ```sql
  DESCRIBE mytable;
  ```

- **Backup Database:**
  ```sql
  expdp username/password DIRECTORY=dump_dir DUMPFILE=mydatabase.dmp LOGFILE=mydatabase.log FULL=y
  ```

- **Restore Database:**
  ```sql
  impdp username/password DIRECTORY=dump_dir DUMPFILE=mydatabase.dmp LOGFILE=mydatabase.log FULL=y
  ```

### **8. NoSQL Databases**

#### **MongoDB**

- **Connect to Database:**
  ```bash
  mongo
  ```

- **Show Databases:**
  ```javascript
  show dbs;
  ```

- **Show Collections:**
  ```javascript
  show collections;
  ```

- **Insert Document:**
  ```javascript
  db.mycollection.insert({ name: "John Doe", age: 30 });
  ```

- **Find Document:**
  ```javascript
  db.mycollection.find({ name: "John Doe" });
  ```

- **Update Document:**
  ```javascript
  db.mycollection.update({ name: "John Doe" }, { $set: { age: 31 } });
  ```

- **Delete Document:**
  ```javascript
  db.mycollection.remove({ name: "John Doe" });
  ```

#### **Cassandra**

- **Connect to Database:**
  ```bash
  cqlsh
  ```

- **Create Keyspace:**
  ```sql
  CREATE KEYSPACE mykeyspace WITH replication = {'class': 'SimpleStrategy', 'replication_factor': 3};
  ```

- **Use Keyspace:**
  ```sql
  USE mykeyspace;
  ```

- **Create Table:**
  ```sql
  CREATE TABLE mytable (
      id UUID PRIMARY KEY,
      name TEXT,
      age INT
  );
  ```

- **Insert Data:**
  ```sql
  INSERT INTO mytable (id, name, age) VALUES (uuid(), 'John Doe', 30);
  ```

- **Select Data:**
  ```sql
  SELECT * FROM mytable;
  ```

- **Update Data:**
  ```sql
  UPDATE mytable SET age = 31 WHERE id = some-uuid;
  ```

- **Delete Data:**
  ```sql
  DELETE FROM mytable WHERE id = some-uuid;
  ```

### **9. Advanced SQL Topics**

#### **Indexing**

- **Create Index:**
  ```sql
  CREATE INDEX idx_name ON mytable (name);
  ```

- **Drop Index:**
  ```sql
  DROP INDEX idx_name;
  ```

#### **Transactions**

- **Begin Transaction:**
  ```sql
  BEGIN TRANSACTION;
  ```

- **Commit Transaction:**
  ```sql
  COMMIT;
  ```

- **Rollback Transaction:**
  ```sql
  ROLLBACK;
  ```

#### **Stored Procedures and Functions**

- **Create Stored Procedure:**
  ```sql
  CREATE PROCEDURE myprocedure (IN param1 INT, OUT param2 VARCHAR(100))
  BEGIN
      SELECT name INTO param2 FROM mytable WHERE id = param1;
  END;
  ```

- **Call Stored Procedure:**
  ```sql
  CALL myprocedure(1, @name);
  ```

- **Create Function:**
  ```sql
  CREATE FUNCTION myfunction (param1 INT) RETURNS VARCHAR(100)
  BEGIN
      DECLARE result VARCHAR(100);
      SELECT name INTO result FROM mytable WHERE id = param1;
      RETURN result;
  END;
  ```

- **Call Function:**
  ```sql
  SELECT myfunction(1);
  ```

#### **Views**

- **Create View:**
  ```sql
  CREATE VIEW myview AS
  SELECT name, age
  FROM mytable
  WHERE age > 25;
  ```

- **Select from View:**
  ```sql
  SELECT * FROM myview;
  ```

- **Drop View:**
  ```sql
  DROP VIEW myview;
  ```

### **10. Security and User Management**

- **Create User:**
  ```sql
  CREATE USER 'username'@'hostname' IDENTIFIED BY 'password';
  ```

- **Grant Privileges:**
  ```sql
  GRANT SELECT, INSERT ON mydatabase.* TO 'username'@'hostname';
  ```

- **Revoke Privileges:**
  ```sql
  REVOKE INSERT ON mydatabase.* FROM 'username'@'hostname';
  ```

- **Show Grants:**
  ```sql
  SHOW GRANTS FOR 'username'@'hostname';
  ```

- **Drop User:**
  ```sql
  DROP USER 'username'@'hostname';
  ```

- **Set Password:**
  ```sql
  SET PASSWORD FOR 'username'@'hostname' = PASSWORD('newpassword');
  ```

### **11. SQL Optimization and Performance**

#### **Query Optimization**

- **Analyze Query:**
  ```sql
  EXPLAIN SELECT * FROM mytable WHERE name = 'John Doe';
  ```

- **Use Indexes:**
  ```sql
  CREATE INDEX idx_name ON mytable (name);
  ```

- **Partition Tables:**
  ```sql
  CREATE TABLE mytable (
      id INT,
      name VARCHAR(100),
      age INT,
      PRIMARY KEY (id, name)
  )
  PARTITION BY HASH(id) PARTITIONS 4;
  ```

- **Optimize Query:**
  ```sql
  OPTIMIZE TABLE mytable;
  ```

### **12. SQL Backup and Recovery**

#### **MySQL**

- **Backup Database:**
  ```bash
  mysqldump -u username -p mydatabase > backup.sql
  ```

- **Restore Database:**
  ```bash
  mysql -u username -p mydatabase < backup.sql
  ```

#### **PostgreSQL**

- **Backup Database:**
  ```bash
  pg_dump -U username mydatabase > backup.sql
  ```

- **Restore Database:**
  ```bash
  psql -U username mydatabase < backup.sql
  ```

#### **Oracle**

- **Backup Database:**
  ```sql
  expdp username/password DIRECTORY=dump_dir DUMPFILE=mydatabase.dmp LOGFILE=mydatabase.log FULL=y
  ```

- **Restore Database:**
  ```sql
  impdp username/password DIRECTORY=dump_dir DUMPFILE=mydatabase.dmp LOGFILE=mydatabase.log FULL=y
  ```

#### **SQL Server**

- **Backup Database:**
  ```sql
  BACKUP DATABASE mydatabase TO DISK = 'C:\backup\mydatabase.bak';
  ```

- **Restore Database:**
  ```sql
  RESTORE DATABASE mydatabase FROM DISK = 'C:\backup\mydatabase.bak';
  ```

### **13. SQL Monitoring and Maintenance**

#### **MySQL**

- **Check Table:**
  ```sql
  CHECK TABLE mytable;
  ```

- **Repair Table:**
  ```sql
  REPAIR TABLE mytable;
  ```

- **Analyze Table:**
  ```sql
  ANALYZE TABLE mytable;
  ```

#### **PostgreSQL**

- **Vacuum Table:**
  ```sql
  VACUUM mytable;
  ```

- **Analyze Table:**
  ```sql
  ANALYZE mytable;
  ```

### **14. SQL Data Import and Export**

#### **MySQL**

- **Import Data:**
  ```sql
  LOAD DATA INFILE '/path/to/file.csv' INTO TABLE mytable
  FIELDS TERMINATED BY ',' ENCLOSED BY '"'
  LINES TERMINATED BY '\n'
  IGNORE 1 ROWS;
  ```

- **Export Data:**
  ```sql
  SELECT * FROM mytable INTO OUTFILE '/path/to/file.csv'
  FIELDS TERMINATED BY ',' ENCLOSED BY '"'
  LINES TERMINATED BY '\n';
  ```

#### **PostgreSQL**

- **Copy Data:**
  ```sql
  COPY mytable TO '/path/to/file.csv' DELIMITER ',' CSV HEADER;
  ```

- **Import Data:**
  ```sql
  COPY mytable FROM '/path/to/file.csv' DELIMITER ',' CSV HEADER;
  ```

### **15. SQL Reporting and Analytics**

- **Basic Aggregations:**
  ```sql
  SELECT COUNT(*), AVG(age), MAX(age), MIN(age) FROM mytable;
  ```

- **Advanced Aggregations:**
  ```sql
  SELECT department, SUM(salary), AVG(salary) FROM employees
  GROUP BY department
  HAVING SUM(salary) > 50000;
  ```

- **Pivot Tables:**
  ```sql
  SELECT 
      department,
      SUM(CASE WHEN gender = 'Male' THEN 1 ELSE 0 END) as Male,
      SUM(CASE WHEN gender = 'Female' THEN 1 ELSE 0 END) as Female
  FROM employees
  GROUP BY department;
  ```

### **16. SQL Special Techniques and Functions**

#### **String Functions**

- **Concatenate:**
  ```sql
  SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;
  ```

- **Substring:**
  ```sql
  SELECT SUBSTRING(name, 1, 5) FROM mytable;
  ```

- **Length:**
  ```sql
  SELECT LENGTH(name) FROM mytable;
  ```

#### **Date Functions**

- **Current Date:**
  ```sql
  SELECT CURRENT_DATE;
  ```

- **Date Difference:**
  ```sql
  SELECT DATEDIFF(CURRENT_DATE, hire_date) FROM employees;
  ```

- **Add Date:**
  ```sql
  SELECT DATE_ADD(hire_date, INTERVAL 1 YEAR) FROM employees;
  ```

### **17. SQL Programming Constructs**

#### **Conditional Logic**

- **Case Statements:**
  ```sql
  SELECT name,
         CASE
             WHEN age < 18 THEN 'Minor'
             WHEN age BETWEEN 18 AND 65 THEN 'Adult'
             ELSE 'Senior'
         END as age_group
  FROM mytable;
  ```

#### **Loops and Iterations**

- **While Loop:**
  ```sql
  DELIMITER //
  CREATE PROCEDURE LoopExample()
  BEGIN
      DECLARE x INT DEFAULT 0;
      WHILE x < 10 DO
          SET x = x + 1;
      END WHILE;
  END//
  DELIMITER ;
  ```

- **For Loop (in PL/pgSQL):**
  ```sql
  DO $$ 
  DECLARE
      r record;
  BEGIN
      FOR r IN SELECT * FROM mytable LOOP
          RAISE NOTICE '%', r.name;
      END LOOP;
  END $$;
  ```

### **18. Database Design and Normalization**

#### **Normalization**

- **First Normal Form (1NF):**
  - Eliminate duplicate columns from the same table.
  - Create separate tables for each group of related data.

- **Second Normal Form (2NF):**
  - Remove subsets of data that apply to multiple rows of a table and place them in separate tables.

- **Third Normal Form (3NF):**
  - Remove columns that are not dependent upon the primary key.

#### **Relationships**

- **One-to-Many Relationship:**
  ```sql
  CREATE TABLE orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
  );
  ```

- **Many-to-Many Relationship:**
  ```sql
  CREATE TABLE course_student (
      course_id INT,
      student_id INT,
      PRIMARY KEY (course_id, student_id),
      FOREIGN KEY (course_id) REFERENCES courses(course_id),
      FOREIGN KEY (student_id) REFERENCES students(student_id)
  );
  ```

This comprehensive guide covers a wide range of SQL commands and techniques, suitable for various SQL dialects and including advanced operations. It should provide a solid foundation for both basic and complex SQL tasks.

