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

- Create table named Users

``` 
 CREATE TABLE Users ( Username varchar(255), Firstname varchar(255),Lastname varchar(255) Age int, Country varchar(255), Active BOOLEAN );
```
- Create tabel with ID with an auto-increment

```
CREATE TABLE Users2 (
 ID INT AUTO_INCREMENT PRIMARY KEY, 
 Username  varchar(255) NOT NULL,,
 Firstname varchar(255) NOT NULL,,
 Lastname  varchar(255) NOT NULL,, 
 Age       int          NOT NULL, 
 Country   varchar(255) NOT NULL,, 
 Active    BOOLEAN 
);
```

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

[ADD COLUMN](#add-column)
- Add columns

```
ALTER TABLE Users ADD COLUMN ALTER TABLE table
```
- Add Column on specific place

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

---
{: data-content="Elias"}
