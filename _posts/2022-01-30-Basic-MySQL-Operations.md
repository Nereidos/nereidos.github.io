---
layout: post
category: Linux Guides
---

# MySQL Operations and Commands

> Some mysql commands (still in progress...)


## Table of contents
- [SHOW and USE DB](#show-and-use-db)
- [Create database and tables](#create-database-and-tables)
- [Show content in Tables](#show-content-in-tables)
- [Insert into Table](#insert-into-table)
- [Update Table](#update-table)
- [ADD COLUMN](#add-column)
- [Search in Table](#search-in-table)
- [Example Databases](#example-databases)
- [Drop Statement](#drop-statement)

## [SHOW and USE DB](#show-and-use-db)
- Show all databases

```
 SHOW DATABASES;
```

- use database

```
 use testdb;
```
- show all tables

```
 show tables;
```

## [Create database and tables](#create-database-and-tables)
- create database

```
 create database testdb;
```
- Creating tables

```
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```
- Create table with PRIMARY KEY
CREATE TABLE table_name1 (
idcolumn1 INT AUTO_INCREMENT PRIMARY KEY NOT NULL,
...
);
``` 
- Create Table with FOREIGN KEYS

``` 
CREATE TABLE table_name2 ( 
fkColumn1 INT NOT NULL, 
PRIMARY KEY (fkColumn1), 
FOREIGN KEY (leser_idleser) REFERENCES table_name1 (idcolumn1),
...
);
``` 
- Create Table with multipe several FOREIGN KEYS
``` 
CREATE TABLE table_name3 ( 
column2 INT NOT NULL, 
column3 INT NOT NULL, 
column4 DATE NOT NULL, 
PRIMARY KEY (column2, column3, column4), 
FOREIGN KEY (column2) REFERENCES table_name2 (idleser), 
FOREIGN KEY (column3) REFERENCES table_name2 (idbuch) 
);


## [Show content in Tables](#show-content-in-tables)

- show content

```
 SELECT * FROM Users;
```

- show chracktertype

```
 desc Users;
```

## [Insert into Table](#insert-into-table)
- Insert to all

```
 INSERT INTO Users(Username,Active) VALUES('t');
 INSERT INTO Users(Username,Username) VALUES('max.muster');
 INSERT INTO Users(Username) VALUES('max.muster');
 INSERT INTO Users(Username) VALUES('max.muster');
 INSERT INTO Users(Firstname) VALUES('max');
 INSERT INTO Users(Firstname) VALUES('max');
 
```

- Insert into all columns

```
 INSERT INTO Users(Username,Firstname,Lastname,Age,Country,Active) VALUES('johnny.down','johnny','down','25','CH','t');
 INSERT INTO Users(Username,Firstname,Lastname,Age,Country,Active) VALUES('klaus.wolf','klaus','wolf','22','DE','t');
```

## [Update Table](#update-table)
- Update All

```
UPDATE Users SET Active = 't';
UPDATE Users SET Country = 'CH';
```
- Update with WHERE (specific)

```
UPDATE Users SET Country = 'CH' WHERE Firstname ='max';
UPDATE Users SET Lastname = 'muster' WHERE Firstname = 'max';
UPDATE Users SET Firstname = 'rainer' WHERE Firstname = 'schmid';
UPDATE Users SET Lastname = 'kienzel' WHERE Firstname = 'kienzel';
```

- Update data type

```
Alter Table Users Modify column Username Varchar(255);
Alter Table Users Modify column Age int;
ALTER TABLE Users CHANGE Active Active BOOLEAN;
ALTER TABLE Users CHANGE Active Active varchar(255) ;
```

- Update datetype with default value

```
 Alter Table Users Modify column Active BOOLEAN default false;
```

## [ADD COLUMN](#add-column)
- Add columns

```
 ALTER TABLE Users ADD COLUMN ALTER TABLE table
```
- Add Column on specific place
- 
```
 ALTER TABLE Users ADD COLUMN Lastname Varchar(255) AFTER Firstname;
``` 

[Search in Table](#search-in-table)

- Where statement
```
 select * from records where name 'konsumenten';
```
- Like statement
```
 select * from records where name like '%konsumenten%';
```
- Select all the different values from the Age column in the Users table.
```
 select DISTINCT Age from Users;
```
- Select all records from the Users table, sort the result alphabetically by the column name.
```
 SELECT * FROM Users ORDER BY name;
```
- Select all records from the Users table, sort the result reversed alphabetically by the column name.
```
 SELECT * FROM Users ORDER BY name DESC;
```
- Select all records from the Users table, sort the result alphabetically, first by the column name, then, by the column firstname.
```
 SELECT * FROM Users ORDER BY name, firstname;
```
- Select all records where the value of the name column starts with the letter "a".
```
 SELECT * FROM Users WHERE name LIKE 'a%';
```                                        
- At the Ending
```
 SELECT * FROM Users WHERE name LIKE '%a';										
```
- Column contains the letter "a".
```
 SELECT * FROM Users WHERE name LIKE '%a%';
```
- Column starts with letter "a" and ends with the letter "b".
```
 SELECT * FROM Users WHERE name LIKE 'a%b'
```
- Column does NOT start with the letter "a".
```
 SELECT * FROM Users WHERE name NOT LIKE 'a%'
``` 									
- The second letter of the name is an "a"
```
 SELECT * FROM Users WHERE name LIKE '_a%';
```
## [Drop Statement](#drop-statement)

- Drop Databases
``` 
DROP DATABASE databasename;
``` 
- Drop Tables
``` 
DROP TABLE table_name;
``` 
-  Drop Column
``` 
ALTER TABLE Lieferant DROP Column1;
``` 
## [Example Databases](#example-databases)

- Example Database customer contact
```
CREATE DATABASE customer_contact;
```
- Create Table with PRIMARY KEY
```
CREATE TABLE tbl_person ( 
PID INT AUTO_INCREMENT PRIMARY KEY NOT NULL, 
name VARCHAR(50), 
vname VARCHAR(50) 
);
```
- Second Table
```
CREATE TABLE tbl_ort (
OID INT AUTO_INCREMENT PRIMARY KEY NOT NULL,
town VARCHAR(50),
postcode CHAR(4)
);
```
-  third Tables
```
CREATE TABLE tbl_adress_art (
AAID INT AUTO_INCREMENT PRIMARY KEY NOT NULL,
address_type VARCHAR(50)
);
```
- Last Table with FOREIGN KEY
```
CREATE TABLE tbl_address (
PID INT NOT NULL,
AAID INT NOT NULL,
address VARCHAR(50),
OID INT NOT NULL,
FOREIGN KEY (PID) REFERENCES tbl_person (PID),
FOREIGN KEY (AAID) REFERENCES tbl_adress_art(AAID),
FOREIGN KEY (OID) REFERENCES tbl_ort(OID),
PRIMARY KEY (PID,AAID)
);
```

---
{: data-content="Elias"}
