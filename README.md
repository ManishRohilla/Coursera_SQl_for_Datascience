##LinkedIn MYSQL

###Download the Excercise files from linkedinCourse and add it into the 
###workbench.

## USER,Accounts and ROLES commands
--> \sql == To shift to sql query in Mysql shell

--> \connect root@localhost == To connect to root localhost in Mysql shell

** CREATE USER "username"@"hostname" IDENTIFIED BY "password"; -- Create User by command **

** CREATE USER "username"@"%hostname" IDENTIFIED BY "password"; -- "%" wildcard means any string of characters with ends with "hostname".**

** CREATE USER "username"@"abc_hostname" IDENTIFIED BY "password"; -- "-" matches only one character starting with 'abc' and ending with 'hostname'.**

--> CREATE ROLE 'app_dev','app_read','app_write'; == To create access roles.

--> GRANT ALL ON database_name.* TO role_name_created == grant permisions to role_name_created in database_name all tables (as * is used). if database_name.table_name is written then access is granted for table_name mentioned only.

--> GRANT INSERT,UPDATE,DELETE ON database_name.* TO role_name_created

--> GRANT access_role_name TO 'username' @ 'host'; == might show error as role is not made active for this connection. (To resolve this error see next command)

--> SET DEFAULT ROLE access_role_name TO 'username' @ 'host';

--> DROP ROLE role_name; == To delete role_name.

--> DROP USER'username' @ 'host'; == To delete a user.

--> ALTER USER 'username' @ 'host' PASSWORD EXPIRE; == user have to write new password.

--> ALTER USER 'username' @ 'host' PASSWORD EXPIRE INTERVAL 90 DAY/NEVER/DEFAULT; 



## SELECT Statements

--> SELECT 'Hello, World'; == To print Hello World.

--> SELECT 1+2; == Will print 3

--> SELECT col_name ,  col_name from country ORDER BY col_name DESC; == To print selected columns in descending w.r.t col_name used after ORDER BY clause

--> SELECT count(*) from table_name; == To print the number of rows.

--> SELECT count(col_name) from table_name ORDER BY col_name LIMIT 5;

--> SELECT * FROM table_name ORDER BY col_name LIMIT 10, 5; == To skip 10 rows and print 5 rows

--> SELECT col_name AS col_name_you_want FROM table_name ORDER BY col_name; == To change name of columns as we want in printing.

--> SELECT * FROM table_name WHERE col_name LIKE 'value'; == To get row which matches value after LIKE clause__ '%' or '_' operators can be used % for string and _ for one single word. 

--> SELECT * from table_name; -- To print complete table.

--> SELECT * from table_name WHERE column_name = 'Condition'; == To get rows from table which satisfies the condition given using WHERE clause.

--> SELECT column_name, column_name/2 AS view_name FROM table_name WHERE column_name >= 2 
     ORDER BY column_name DESC;

--> SELECT * FROM table_name WHERE col_name LIKE 'value_' OR col_name LIKE 'value%';

## INSERTING 
--> INSERT INTO table_name (col_name, col_name) VALUES ('value_string', value);

## Updating

--> UPDATE table_name SET col_name = 'value' WHERE col_name LIKE 'man%';

## CREATING Table

--> CREATE TABLE test ( a INT, b VARCHAR(16), c VARCHAR(16) );

## DELETING TABLE

--> DELETE FROM table_name WHERE col_name LIKE 'value_' OR col_name LIKE 'value%';

--> DELETE FROM table_name; == Will delete all rows from table.

--> Drop table_name; == will delete table as well as the rows.

## 
