# MySQL How-to 


```
$ sudo mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 601
Server version: 8.0.28-0ubuntu0.20.04.3 (Ubuntu)

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 

# See MYSQL version information 
mysql> SHOW VARIABLES LIKE '%version%';
+--------------------------+-------------------------+
| Variable_name            | Value                   |
+--------------------------+-------------------------+
| admin_tls_version        | TLSv1.2,TLSv1.3         |
| immediate_server_version | 999999                  |
| innodb_version           | 8.0.28                  |
| original_server_version  | 999999                  |
| protocol_version         | 10                      |
| replica_type_conversions |                         |
| slave_type_conversions   |                         |
| tls_version              | TLSv1.2,TLSv1.3         |
| version                  | 8.0.28-0ubuntu0.20.04.3 |
| version_comment          | (Ubuntu)                |
| version_compile_machine  | x86_64                  |
| version_compile_os       | Linux                   |
| version_compile_zlib     | 1.2.11                  |
+--------------------------+-------------------------+
13 rows in set (0.00 sec)

# Create a User 'calvin' with password 'PASSWORD'
mysql> CREATE USER 'calvin'@'%' IDENTIFIED BY 'PASSWORD';

# Grant privileges
mysql> GRANT ALL PRIVILEGES ON *.* TO 'calvin'@'%' WITH GRANT OPTION;
Query OK, 0 rows affected (0.02 sec)
mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.01 sec)

# Create a Database
mysql> CREATE DATABASE demo;

# Select a Database
mysql> USE demo;

# Add a Table (with AUTO_INCREMENT)
CREATE TABLE TODO (
  id integer not null AUTO_INCREMENT, 
  description varchar(255), 
  is_done boolean not null, 
  target_date timestamp, 
  user varchar(255), 
  primary key (id)
);

# Insert rows to the table
mysql> INSERT INTO TODO VALUES(10001, 'Learn Spring Boot', false, sysdate() 'in28Minutes');
Query OK, 1 row affected (0.02 sec)

mysql> INSERT INTO TODO VALUES(10002, 'Learn RESTful Web Services', false, sysdate(),'in28Minutes');
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO TODO VALUES(10003, 'Learn SOAP Web Services', false, sysdate(),'in28Minutes');
Query OK, 1 row affected (0.02 sec)

# Check entries in the table
mysql> SELECT * FROM TODO;
+-------+----------------------------+---------+---------------------+-------------+
| id    | description                | is_done | target_date         | user        |
+-------+----------------------------+---------+---------------------+-------------+
| 10001 | Learn Spring Boot          |       0 | 2022-02-25 08:25:07 | in28Minutes |
| 10002 | Learn RESTful Web Services |       0 | 2022-02-25 08:25:13 | in28Minutes |
| 10003 | Learn SOAP Web Services    |       0 | 2022-02-25 08:25:29 | in28Minutes |
3 rows in set (0.00 sec)

# Delete a Table
# Delete Table
mysql> DROP TABLE TODO; 



```


