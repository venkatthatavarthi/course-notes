# SQL

# SQL

    Relational Database
    
    Structured Query Language
    	Microsoft 				MSSQL  (paid product)
    	Free 					MYSQL
    Relational Database
    Tables
    ID
    Fields

    User
    	UserId;
    	UserName;
    
    Category
    	CategoryId;
    	CategoryName;
    
    We can create RELATIONSHIPS
    
    User
    	UserId;
    	UserName;
    	CategoryId;      FOREIGN KEY (Id in another table)
    
    Id  'IDENTITY'  ==> Unique, Auto-Increment To Highest Value

Proposal today
SQL : Create database with rabbit tables
Entity : C# ==> hook into this database
View, Update Rabbits

SQL commands

    View => Server Explorer.  Data Connection, Add
    	(localdb)\\mssqllocaldb 
    View => SQL Object Explorer	
    
    	Gives access to the local computer using SQL server
    
    	Files called ....mdf Microsoft Database File
    	Stored in C:\\Users\\<username>\\ folder

    use master
    go
    
    drop database if exists RabbitDb
    go
    
    create database RabbitDb
    go
    
    use RabbitDb
    go
    
    drop table if exists Rabbits
    
    
    CREATE TABLE Rabbits(
    	RabbitId INT NOT NULL IDENTITY PRIMARY KEY,
    	Age INT NULL,
    	Name VARCHAR(50) NULL
    );
    
    INSERT INTO Rabbits Values ('1','Rabbit01')
    INSERT INTO Rabbits Values ('0','Rabbit02')
    INSERT INTO Rabbits Values ('0','Rabbit03')
    
    SET IDENTITY_INSERT Rabbits ON
    INSERT INTO Rabbits (RabbitId, Age, Name) values (4,0,'Rabbit04')
    SET IDENTITY_INSERT Rabbits OFF
    
    select 'Rabbit Database'
    
    UPDATE Rabbits Set Name='Changed' WHERE RabbitId=3
    
    delete from rabbits where RabbitId=4
    
    select * from Rabbits

# SQL Day 2

# SQL Warm Up

Create from scratch

A database
3 Tables which have
One main table
Two Sub-tables which have foreign keys in the main table eg

    Students (main)
    		Qualifications (sub)
    		Teachers (sub)
    		Grades (sub)
    		Classroom (sub)
    
    	Create somewhere some data which has
    		INT
    		DATE  eg DATEOFBIRTH
    		BIT  (0 or 1)
    		TINYINT (0 TO 255)

Fill with data
Use INNER JOIN to show some data across all 3 tables
Use DATEDIFF to find the difference between today and the given date
Use DATEADD to add 7 days to the given date
INSERT A NEW RECORD
UPDATE A RECORD
DELETE A RECORD
Select items where a field is LIKE '%abc%' ie contains the letters 'abc'

# SQL Day 2 Notes

# SQL

Sql theory terms

4 categories

DML Data Manipulation Language
Basic queries : SELECT, INSERT, UPDATE, DELETE (CRUD operations)

DDL Data Definition Language
Create Data Structures ie Database/Table
CREATE/DROP - database & table ie add new or remove completely
ALTER table ie to add key/column
TRUNCATE remove

DCL Data Control Language
Permissions GRANT / REVOKE

TCL Transaction Control Language
Group of transactions TOGETHER
1) COMMIT (all of transactions in the group as a whole) eg ATM withdrawl
is either ALL COMMIT or nothing.
2) ROLLBACK to a given point eg start of transaction group
3) SAVEPOINT : mid-way point of saving data progression throughout
a series of transactions

# Basic Commands

    use db01   // bring into scope
    go
    drop database db01  // risk of exception if no db present
    drop database if exists db01
    go
    create database db01
    go

Data types

INT
TINYINT
BIT	0,1,null
CHAR(5)	FIXED WIDTH IE CUSTOMERID='ALFKI'; ASCII ie 8 bit
VARCHAR(50)	VARIABLE WIDTH UP TO 50 MAX ASCII ie 8 bit
NCHAR / NVARCHAR	UNICODE IE 16 BIT
DATE/TIME/DATETIME
BLOB / BINARY BINARY LARGE OBJECT eg MOVIE .mov
??? FLOAT
??? DECIMAL

# Getting help

    # meta data about your table 
    SP_HELP

    /* put master in scope */
    use master
    go
    drop database if exists OrangeDb
    go
    create database OrangeDb
    go
    use OrangeDb
    drop table if exists Oranges
    
    
    
    /* create sub-relationship table FIRST */
    create table Categories(
       CategoryId INT NOT NULL IDENTITY PRIMARY KEY,
       CategoryName NVARCHAR(50) NULL
    )
    
    create table Oranges(
      OrangeId int not null IDENTITY PRIMARY KEY,
      OrangeName NVARCHAR(50) NULL,
      DateHarvested Date NULL,
      IsLuxuryGrade Bit NULL,
      CategoryId int null FOREIGN KEY REFERENCES Categories(CategoryId)
    )
    
    create table Batch(
    	BatchId int NOT NULL IDENTITY PRIMARY KEY,
    	OrangeID int NULL FOREIGN KEY REFERENCES Oranges(OrangeID),
    	Quantity int NULL,
    	DespatchDate Date NULL
    )
    
    /* populate minor category table FIRST */
    INSERT INTO Categories values ('clementines')
    INSERT INTO Categories values ('reds')
    INSERT INTO Categories values ('easy peelers')
    
    insert into Oranges values('Clementine','2019-09-07',0,2)
    insert into Oranges values('Blood Orange','2019-09-15',1,1)
    insert into Oranges values('Tangerine','2019-09-08','false',3)
    insert into Oranges values('Clementine','2018-12-25',0,1)
    go
    
    insert into Batch values (1,100,'2019-09-30')
    insert into Batch values (2,100,'2019-09-30')
    insert into Batch values (3,100,getdate())
    insert into Batch values (4,50,'2019-08-01')
    
    
    select * from Oranges
    select * from Categories
    
    select orangeid, orangename, categoryname from Oranges 
    inner join categories on oranges.categoryid = categories.categoryid
    
    /* Expiry date = harvested date + 90 days */
    select orangeid, orangename, categoryname, dateharvested, 
    DATEADD(d,90,dateharvested) as 'expirydate' from oranges
    inner join categories on oranges.CategoryId=Categories.CategoryId
    
    select *, (DATEDIFF(d, dateharvested, GETDATE()))  as 'SinceHarvested',
    CASE
    WHEN (DATEDIFF(d, dateharvested, GETDATE())) > 90  THEN 'true'
    ELSE 'false' 
    END 
    AS 'IsExpired'
    from batch 
    inner join oranges on oranges.OrangeId=batch.OrangeID

# UPDATE

    UPDATE mytable set name='fred' where id=2

# DELETE

## care - can delete all records if omit 'where'

    DELETE from mytable WHERE id=2

# Normal Form

Aims to ensure INTEGRITY of data within a database ie all of the relationships make sense, and all of the data is current and can be found quickly with the right searches.
No duplication of data etc.

1st Normal Form

    One field should hold One item of data only eg mobile phone field should not hold
    			2 mobile numbers
    
    Atomic : as small as possible ie 1 unit of data per cell

2nd Normal Form

    All keys depend on PRIMARY KEY

3rd Normal Form

    No keys should have any inter-dependent relationships with each other 
    
    	Name, Address, Postcode, City, County.
    
    		In theory the City and County actually are related
    
    	Name, Address, Postcode, City
    
    	County
    		City1
    		City2

# top

    select top 10 * from customers

# select where ... and ...

    select * from products where unitsinstock < 10 and discontinued=0 
    order by unitsinstock desc

# operators

    AND OR   
    
    <>    or    !=       (NOT EQUAL TO)
    
    >    <    >=    <=

# SELECT DISTINCT

    select country from customers order by country 
    select distinct country from customers order by country

# CONTAINS ==> SQL 'like' keyword

    # contains 'abc'
    like '%abc%' 
    # start
    like 'abc%'
    # end
    like '%abc'
    # does not contain
    like %[^abc]%
    select * from products where ProductName not like 'ch%'

# MULTIPLE EXACT HITS - USE 'IN' KEYWORD

    # same as 'region = wa and region = bc and region = ..'
    
    select * from employees where region IN ('wa','bc')

# BETWEEN A AND B

    select * from products where unitprice between 10 and 20

# CUMULATIVE FUNCTIONS

    SUM, COUNT, AVERAGE, MIN, MAX

    /* COUNT CITY, COUNTRY */
    select count(distinct city) as 'cities', count(distinct country) as 'countries' from customers
    select count(distinct country) from customers
    
    /* AVERAGE PRICE, MIN PRICE, MAX PRICE */
    select avg(unitprice) as 'averageprice', 
    min(unitprice) as 'minprice',
    max(unitprice) as 'maxprice',
    count(*) as 'count' from products
    select min(unitprice) as 'minprice' from products
    select max(unitprice) as 'maxprice' from products
    /* SUM OF UNITS ON STOCK */
    select sum(UnitsInStock) as 'Stock Total' from products

# as select ... as ...

# Maths

Easy to do mathematical operations inside the query

EG Product discount

    £100 with 10% discount ==> sell for £90
    
    // Get product, price, discount, price including discount from ORDER DETAILS
    
    // customer ==> place order with OrderID
    
    // order ==> details with Order_DetailId
    
    // Get total of (quantity*unitprice) as 'ordervalue'
    // get total of (1-discount)* 'ordervalue'

    select * from orders
    select * from [Order Details]
    -- Get product, price, discount, price including discount from ORDER DETAILS
    select ProductName, Quantity, [Order Details].UnitPrice, Discount, 
    ([order details].UnitPrice*(1-Discount)) as 'Discount Price' from [Order Details]
    inner join Products on products.productid = [order details].productid
    order by 'Discount Price' desc
    -- Get total of (quantity*unitprice) as 'ordervalue'
    select sum(unitprice*quantity) from [order details]
    -- get total of (1-discount)* 'ordervalue'
    select sum(unitprice*quantity*(1-discount)) from [Order Details]
    -- difference
    select
    sum(unitprice*quantity) as 'gross sales',
    sum(unitprice*quantity*(1-discount)) as 'discounted sales',
    (sum(unitprice*quantity) - sum(unitprice*quantity*(1-discount))) as 'discount given'
    from [order details]

# substring

    substring(string, startindex, length)
    substring('cheese',,2) returns 'he'

# charindex

charindex(' ','BR23 4AZ') returns 5 the index of the space

LTRIM removes leading spaces

Replace('some text','text','cheese') returns 'some cheese'

UPPER

Lower

# case .. when .. else

case
when (x>10) then 'old'
else 'young'
end
as 'are you old?'

# group by .. having

Order by ONLY WORKS FOR FIELDS WHICH EXIST INITIALLY BUT NOT ON CUMULATIVE FIELDS

    so we can find the sum of all units in stock per product category but this field
    does not exist initially so we can't order by this field.
    
    Cumulative fields ie SUM/MAX/MIN/AVG/COUNT
    Group By    (selecting into batches)
    Having .... (same as order by)

Order matters
SELECT (unitprice*discount) DISTINCT FROM WHERE .....
GROUP BY ... HAVING ....
ORDER BY ...

    select 'GROUP BY'
    select supplierid, sum(unitsonorder) as 'Total Units On Order' from products
    group by supplierid
    having sum(unitsonorder) = 0
    order by 'total units on order' desc
    
    select 'GROUP BY'
    select supplierid, sum(unitsonorder) as 'Total Units On Order' from products
    group by supplierid
    having sum(unitsonorder) > 0
    order by 'total units on order' desc

# JOINS

INNER JOIN = LEFT JOIN

    table1        table2
    	table1id    table2id  
    
    All from table1 plus matching from table2 only where there is a match

OUTER JOIN = RIGHT JOIN

    All from table2 plus matching records from table1

FULL JOIN

    All from table1 plus all from table2 and NULL if no matching record in table2

# SUBQUERIES

Query within a query : useful for large, long queries

    // FIND CUSTOMERS WITH NO ORDERS
    select ... from ... where (select ... from ...)
    select * from customers where customerID not in (select customerID from orders)

# Extra terms

IDENTITY(1,1) Autoincrement starting at value 1 and jump by 1 each time
IDENTITY Autoincrement
PRIMARY KEY CLUSTERED : Only one primary key

# Connection Strings And Environment Variables

We can build a connection string

    using System;
    using System.Data.Sql;  // TALK TO SQL DIRECT
    using System.Data.SqlClient;
    
    namespace lab_38_raw_sql
    {
        class Program
        {
            static void Main(string[] args)
            {
                string connectionstring = @"Data Source=localhost;Initial Catalog=Northwind;Persist Security Info=True; User ID=SA;Password=Passw0rd2018";
                using (var connection = new SqlConnection(connectionstring))
                {
                    connection.Open();
                    Console.WriteLine(connection.State);
                }
    
                string connectionstring2 = @"Data Source=(localdb)\\mssqllocaldb;Initial Catalog=Northwind;";
                using (var connection2 = new SqlConnection(connectionstring2)) {
                    connection2.Open();
                    Console.WriteLine(connection2.State);
                }
    
    
    
            }
        }
    }