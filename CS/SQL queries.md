#cs #database #mysql

# Introduction
> SQL is the standard language for dealing with Relational Databases. SQL is used to insert, search, update, and delete database records.

# How to use SQL?
[W3 schools 學習資源](https://www.w3schools.com/mysql/mysql_sql.asp)
```sql
SELECT * FROM Customers;
```
- SQL keywords are NOT case sensitive: select is the same as SELECT.

# Overview important commands
```mysql
CREATE DATABASE mydatabase;
```
```mysql
CREATE TABLE mytable (
  id INT PRIMARY KEY,
  name VARCHAR(50),
  age INT
);
```
```mysql
INSERT INTO mytable (id, name, age)
VALUES (1, 'John Doe', 25);
```

- `SELECT` - extracts data from a database
- `UPDATE` - updates data in a database
- `DELETE` - deletes data from a database
- `INSERT INTO` - inserts new data into a database
- `CREATE DATABASE` - creates a new database
- `ALTER DATABASE` - modifies a database
- `CREATE TABLE` - creates a new table
- `ALTER TABLE` - modifies a table
- `DROP TABLE` - deletes a table
- `CREATE INDEX` - creates an index (search key)
- `DROP INDEX` - deletes an index