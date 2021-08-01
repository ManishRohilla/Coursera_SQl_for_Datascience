##LinkedIn MYSQL

###Download the Excercise files from linkedinCourse and add it into the 
###workbench.

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


