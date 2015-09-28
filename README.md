# mysql

To Check MYSQL sock in Ubuntu

    /etc/mysql/my.cnf

Rules
1.  Use all uppercase on mysql commands
2.  End the command with semicolon
3.  Mysql commands are separated by comma
4.  Variables are combination lowercase letters and underscores

$ mysql <Enter>

To start a mysql

	mysql -u root -p
	>Enter password: **********

	mysql>

To QUIT

	mysql> quit;<ENTER>

Show database

    SHOW DATABASES;

Create database

    CREATE DATABASE <name>;
    CREATE DATABASE test1;

Use the database

    USE <database name>;
    USE test1;

To show my current Database

    SELECT DATABASE();

To show tables

    SHOW TABLES;    

To delete a database

    DROP DATABASE <database name>;
    DROP DATABASE test1;

#Creating a Database Sample

Model all the data to what it will look like
Break it all down into tables

Create a database

    CREATE DATABASE student;    

Use that database

    USE student;

#1 Create a table for student

    CREATE TABLE student(
    -> first_name VARCHAR(30) NOT NULL,
    -> last_name VARCHAR(30) NOT NULL,
    -> email VARCHAR(60) NULL,                  #NULL can have no value
    -> street VARCHAR(50) NOT NULL,
    -> state CHAR(2) NOT NULL DEFAULT 'PA',     #fix char max to 2
                                                #has default value
    -> zip MEDIUMINT UNSIGNED NOT NULL,         #unsigned can use negative numbers
    -> phone VARCHAR(20) NOT NULL,
    -> birth_date DATE NOT NULL,                #DATE from mysql
    -> sex ENUM('M', 'F') NOT NULL,             #ENUM choices M or F
    -> date_entered TIMESTAMP,
    -> lunch_cost FLOAT NULL,                   #FLOAT has decimal
    -> student_id INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY);
    
After you create a DATABASE

Show TABLES to view what is inside the database

    SHOW TABLES;

Show what is inside the DATABASE table

    DESCRIBE student;
    or
    SHOW COLUMNS FROM  student;

Enter value 

    INSERT INTO student VALUE
    ->('Renielle', 'Bernardo', 'renielle@gmail.com',
    -> 'LosBanos',
    -> 'Laguna',
    -> 'PH',
    -> 081011,
    -> '0909-293-3908',
    -> "2011-08-10",
    -> 'F',
    -> NOW(),           #Built in msql
    -> 3.50,
    -> NULL);           #NULL for PRIMARY KEY

To show all the data in the TABLE

    SELECT * FROM student;

#2 Create table class

    CREATE TABLE class(
    -> name VARCHAR(30) NOT NULL,
    -> class_id INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY); <Enter>

    SHOW TABLES;

To insert values in the class table

    INSERT INTO  class VALUES
    ->('english', NULL);

To show what is inside the table class

    SELECT * FROM class;

#Create table test

    CREATE TABLE test(
    -> date DATE NOT NULL,
    -> type ENUM('T', 'Q') NOT NULL,
    -> class_id INT UNSIGNED NOT NULL,          #Foreign key from the class table
    -> test_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY); <Enter>

    >SHOW TABLES;

Foreign Key - used to make references to the primary key of ANOTHER table

#Create score table

    CREATE TABLE score(
    -> student_id INT UNSIGNED NOT NULL,
    -> event_id INT UNSIGNED NOT NULL,
    -> score INT NOT NULL,
    -> PRIMARY KEY(event_id, student_id));  #2 foreign keys used in primary key
                                            #to be unique

#Create absence table

    CREATE TABLE absence(
    -> student_id INT UNSIGNED NOT NULL,
    -> date DATE NOT NULL,
    -> PRIMARY KEY(student_id, date));      #Foreign key and date as primary key

    >SHOW TABLES;

Add new data to the table

    >DESCRIBE test;          #to view what is inside test table

    >ALTER TABLE test
    ->ADD maxscore INT NOT NULL AFTER type;     #Add new row

    >DESCRIBE test;          #to view what is inside test table

Another way to enter data all at once

    > DESCRIBE test;          #to view what is inside test table

    > INSERT INTO test VALUES
    ->('2014-8-25', 'Q', 15, 1, NULL),
    ->('2014-8-25', 'Q', 25, 1, NULL),
    ->('2014-8-28', 'Q', 35, 2, NULL),
    ->('2014-8-29', 'Q', 35, 4, NULL),
    ->('2014-8-29', 'Q', 55, 4, NULL); <Enter>

    > SELECT * FROM test    #to view the DATA inside test table

How to change the name

    DESCRIBE score;

    ALTER TABLE score CHANGE event_id test_id   #event_id to test_id
    -> INT UNSIGNED NOT NULL;                   #define the data type

    DESCRIBE score;

hash to comment

/* Multiline comment */

If i am going to input data to a table

    describe the table
        DESCRIBE absence;      #to show the data structure
    to insert values
        INSERT INTO absence VALUES
        -> (6, '2015-8-21'),
        -> (7, '2015-8-22'),
        -> (8, '2015-8-23');

To view only specific from the table instead of * to view all

    > SELECT first_name, lastname FROM student; 

To rename a table

    > RENAME TABLE
    -> abscence to absences,
    -> class to classes,
    -> score to scores,
    -> student to students,
    -> test to tests; <Enter>

    > SHOW TABLES;

Querying tables

    > SELECT first_name, last_name, state
    -> FROM students
    -> WHERE state="WA";            #WHERE is used to target specific

    > SELECT first_name, last_name, birth_date
    -> FROM students
    -> WHERE YEAR(birth_date) >= 1965;             #compare the values
    
    > SELECT first_name, last_name, birth_date
    -> FROM students
    -> WHERE MONTH(birth_date) = 2 OR state="CA";  #compare the values










    















