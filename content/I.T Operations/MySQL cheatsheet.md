### **Connecting to MySQL**

|Command|Description|
|---|---|
|`mysql -u username -p`|Connect to MySQL as a specific user. You will be prompted for a password.|
|`mysql -u root -p`|Connect to MySQL as root (admin).|
|`exit`|Exit the MySQL shell.|

### **Database Operations**

|Command|Description|
|---|---|
|`SHOW DATABASES;`|List all databases on the server.|
|`CREATE DATABASE dbname;`|Create a new database.|
|`DROP DATABASE dbname;`|Delete a database (irreversible).|
|`USE dbname;`|Switch to and use a specific database.|
|`SELECT DATABASE();`|Show the currently selected database.|
|`SHOW TABLES;`|List all tables in the current database.|

### **Table Operations**

|Command|Description|
|---|---|
|`CREATE TABLE tablename (columns);`|Create a new table with specified columns.|
|`SHOW COLUMNS FROM tablename;`|Show details of the columns in a table.|
|`DESCRIBE tablename;`|Describe the structure of a table.|
|`ALTER TABLE tablename ADD columnname datatype;`|Add a new column to an existing table.|
|`ALTER TABLE tablename DROP COLUMN columnname;`|Delete a column from a table.|
|`DROP TABLE tablename;`|Delete a table (irreversible).|
|`RENAME TABLE oldname TO newname;`|Rename a table.|
|`SHOW INDEX FROM tablename;`|Show indexes of a table.|

### **Basic Data Operations**

|Command|Description|
|---|---|
|`INSERT INTO tablename (columns) VALUES (values);`|Insert data into specific columns.|
|`SELECT * FROM tablename;`|Select all records from a table.|
|`SELECT column1, column2 FROM tablename;`|Select specific columns from a table.|
|`UPDATE tablename SET column1 = value WHERE condition;`|Update data in a table based on a condition.|
|`DELETE FROM tablename WHERE condition;`|Delete data from a table based on a condition.|
|`TRUNCATE TABLE tablename;`|Remove all data from a table but keep the table structure.|

### **Filtering & Sorting**

|Command|Description|
|---|---|
|`SELECT * FROM tablename WHERE condition;`|Select records that match a specific condition.|
|`SELECT * FROM tablename ORDER BY column ASC|DESC;`|
|`SELECT * FROM tablename LIMIT number;`|Limit the number of rows returned.|
|`SELECT * FROM tablename WHERE column LIKE 'pattern';`|Filter results based on a pattern (e.g., `%` wildcard).|

### **Joins (Combining Data from Multiple Tables)**

|Command|Description|
|---|---|
|`SELECT * FROM table1 INNER JOIN table2 ON table1.column = table2.column;`|Perform an inner join (matching rows from both tables).|
|`SELECT * FROM table1 LEFT JOIN table2 ON table1.column = table2.column;`|Perform a left join (all rows from table1 and matching rows from table2).|
|`SELECT * FROM table1 RIGHT JOIN table2 ON table1.column = table2.column;`|Perform a right join (all rows from table2 and matching rows from table1).|

### **Indexes**

|Command|Description|
|---|---|
|`CREATE INDEX indexname ON tablename (column);`|Create an index on a column to speed up queries.|
|`DROP INDEX indexname ON tablename;`|Remove an index from a table.|

### **Foreign Keys**

|Command|Description|
|---|---|
|`ALTER TABLE childtable ADD CONSTRAINT fk_name FOREIGN KEY (childcolumn) REFERENCES parenttable(parentcolumn);`|Add a foreign key constraint.|
|`ALTER TABLE childtable DROP FOREIGN KEY fk_name;`|Drop a foreign key constraint.|

### **Users and Permissions**

|Command|Description|
|---|---|
|`CREATE USER 'username'@'host' IDENTIFIED BY 'password';`|Create a new MySQL user.|
|`GRANT ALL PRIVILEGES ON dbname.* TO 'username'@'host';`|Grant all privileges to a user on a database.|
|`GRANT SELECT, INSERT ON dbname.* TO 'username'@'host';`|Grant specific privileges to a user on a database.|
|`SHOW GRANTS FOR 'username'@'host';`|Show the privileges of a specific user.|
|`REVOKE ALL PRIVILEGES ON dbname.* FROM 'username'@'host';`|Revoke all privileges from a user.|
|`DROP USER 'username'@'host';`|Delete a MySQL user.|

### **Backup and Restore**

|Command|Description|
|---|---|
|`mysqldump -u username -p dbname > backup.sql`|Back up a database to a `.sql` file.|
|`mysqldump -u username -p --all-databases > backup.sql`|Back up all databases.|
|`mysql -u username -p dbname < backup.sql`|Restore a database from a backup file.|

### **Transactions**

|Command|Description|
|---|---|
|`START TRANSACTION;`|Begin a new transaction.|
|`COMMIT;`|Commit the current transaction.|
|`ROLLBACK;`|Roll back the current transaction (undo changes).|

### **Advanced Queries**

|Command|Description|
|---|---|
|`SELECT COUNT(*) FROM tablename;`|Count the number of rows in a table.|
|`SELECT AVG(column) FROM tablename;`|Calculate the average value of a column.|
|`SELECT SUM(column) FROM tablename;`|Calculate the sum of a column.|
|`SELECT MAX(column) FROM tablename;`|Find the maximum value in a column.|
|`SELECT MIN(column) FROM tablename;`|Find the minimum value in a column.|
|`GROUP BY column`|Group rows that have the same values in specified columns.|
|`HAVING condition`|Filter rows after the `GROUP BY` clause.|

### **Import/Export Data**

|Command|Description|
|---|---|
|`LOAD DATA INFILE 'filepath' INTO TABLE tablename;`|Import data from a file into a table.|
|`SELECT * INTO OUTFILE 'filepath' FROM tablename;`|Export data from a table into a file.|

### **Information and Debugging**

|Command|Description|
|---|---|
|`SHOW PROCESSLIST;`|Show running MySQL processes (useful for debugging).|
|`SHOW VARIABLES LIKE '%timeout%';`|Show current timeout settings for MySQL connections.|
|`SHOW ENGINE INNODB STATUS;`|Show detailed InnoDB engine status (useful for diagnosing issues).|

### **General Tips**

- **End Every MySQL Command with a Semicolon (`;`):** MySQL statements should be terminated with a semicolon.
- **Case Sensitivity:** MySQL commands are not case-sensitive, but database names and table names can be.