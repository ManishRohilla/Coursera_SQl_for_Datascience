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

--> SELECT 1+2; == Will print 3 with 1+2 as Column name

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

--> CREATE TABLE test ( id INT NOT NULL, name VARCHAR(30), address VARCHAR(255) ,city VARCHAR(30), state CHAR(25), zip INT(10));

--> CREATE TABLE employee  (ID int(8) PRIMARY KEY,
                            Name char(55) NOT NULL,
                            Contact int(10) NOT NULL UNIQUE,
                            Salary decimal(5,2) NOT NULL);
                            
--> CREATE TABLE temp (
  id INT UNSIGNED UNIQUE AUTO_INCREMENT PRIMARY KEY,
  stamp TIMESTAMP,
  name VARCHAR(64)
);
 == or id Datatype could be SERIAL;
--> CREATE TABLE test (
  id INT UNSIGNED UNIQUE AUTO_INCREMENT PRIMARY KEY,
  a VARCHAR(32)
);
                            
--> Show Create Table table_name;
                                           

## DELETING TABLE

--> DELETE FROM table_name WHERE col_name LIKE 'value_' OR col_name LIKE 'value%';

--> DELETE FROM table_name; == Will delete all rows from table.

--> Drop table_name; == will delete table as well as the rows.

--> Drop TABLE IF EXISTS table_name;

## MISC

--> Show Databases;

--> Use Databases_name;

--> Describe table_name;

--> Show tables;

--> Show Table Status;

--> SELECT NOW(); == Will print current date and time

--> SHOW VARIABLES LIKE '%time%';

--> SELECT 0 = 0;

**SELECT 0 = 1;
SELECT 0 = '0';
SELECT '0.1' > 0; == Strign will be converted into integer then it will be compared
SELECT 0.1 < 0;
SELECT 9 != 7;
SELECT 9 <= 7;
SELECT 9 >= 7;
SELECT (9 > 7) AND (12 < 27);
SELECT (9 > 7) OR (12 < 27);
SELECT (9 > 7) IS TRUE;
SELECT (9 > 7) IS NOT TRUE; == First the data type is converted into the latter the it is compared.
SELECT 9 IN (1, 5, 9); == Will give true.
**
## JOINING 

-->SELECT a.artist AS Artist, a.title AS Album, t.track_number AS 'Track Num',
    t.title AS Track, t.duration AS Seconds
  FROM album AS a
  JOIN track AS t ON a.id = t.album_id
  ORDER BY a.artist, a.title, t.track_number;

## DATATYPES

**NUMERICS**

--> DECIMAL(9,2) or NUMERIC(9,2) // 9 digits total and 2 after decimal. Default is DECIMAL(10,0)
example- 1234567.89

**Strings**

--> CHAR(14)
--> VARCHAR(25)

**ENUMS**
--> CREATE TABLE test (
  id INT UNSIGNED UNIQUE AUTO_INCREMENT PRIMARY KEY,
  a ENUM( 'Pablo', 'Henri', 'Jackson' )
); == ENUM OR SET

**hCASES**

SELECT
  CASE WHEN a < 5 THEN 'true' ELSE 'false' END AS boolA,
  CASE WHEN b > 0 THEN 'true' ELSE 'false' END AS boolB
  FROM booltest
;

SELECT
  CASE a WHEN 1 THEN 'true' ELSE 'false' END AS boolA,
  CASE b WHEN 1 THEN 'true' ELSE 'false' END AS boolB 
  FROM booltest
;

## String Comparison

--> SELECT Name FROM country WHERE Name LIKE '_a%' ORDER BY Name;

--> SELECT Name FROM country WHERE STRCMP(Name, 'France') <= 0 ORDER BY Name;

**Regular Expressions**

--> SELECT Name FROM country WHERE Name RLIKE 'y$' ORDER BY Name;

--> SELECT Name FROM country WHERE Name RLIKE '[xz][ai]' ORDER BY Name;

**Concat Strings**

--> SELECT CONCAT('Love', ' ', 'is', ' ', 'all', ' ', 'you', ' ', 'need'); == Love is all yotu need, will come on the output.

**Conversion**

--> SELECT HEX(32742);

--> SELECT OCT(32742);

--> SELECT BIN(32742);

--> SELECT CONV('32742',initial_base,to_final_base);

**Trimming Padding**

--> SELECT * FROM customer WHERE name LIKE TRIM('  Bill Smith  '); == Remove Spaces .. LTRIM (remove spaces from left) and RTRIM 

--> SELECT CONCAT(':', TRIM('x' FROM 'xxxBill Smithxxx'), ':'); == Customizing TRIM for other values

--> SELECT LPAD('Price', 20, '. '); == will add '.' 20 times to the left of 'Price'

--> SELECT RPAD('Price', 20, '. '); == will add '.' 20 times to the right of 'Price'

**Changing Cases**

--> SELECT UPPER(name) FROM customer; == UCASE can also be used to convert to upper case

--> SELECT LOWER(name) FROM customer; == LCASE can also be used to convert to lower case

--> SELECT CONCAT(UPPER(SUBSTRING(name, 1, 1)),LOWER(SUBSTRING(name, 2))) FROM customer;

**Substring**

--> SELECT SUBSTRING('this is a string', 6); == will give  'string' as output.

--> SELECT SUBSTR('this is a string', 6, 4); == will give 'is a' as output

--> SELECT SUBSTR('this is a string', -6); == count 6 from last.

--> SELECT SUBSTR('this is a string', -6, 4); == 'stri'

--> SELECT SUBSTRING_INDEX('this is a string', ' delimiter', No_of Times_Delimiter_should_be_encountered);

**SOUNDEX**

--> SELECT SOUNDEX('acting'), SOUNDEX('action');

--> SELECT 'bill' SOUNDS LIKE 'boil', 'bill' SOUNDS LIKE 'phil';
