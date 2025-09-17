# Lesson-14: Date and time Functions,Practice

> **Notes before doing the tasks:**
> - Tasks should be solved using **SQL Server**.
> - Case insensitivity applies.
> - Alias names do not affect the score.
> - Scoring is based on the **correct output**.
> - One correct solution is sufficient.

---

# Easy Tasks
1. Write a SQL query to split the Name column by a comma into two separate columns: Name and Surname.(TestMultipleColumns)
2. Write a SQL query to find strings from a table where the string itself contains the % character.(TestPercent)
3. Split a string based on dot(.).(Splitter)
4. Write a SQL query to replace all integers (digits) in the string with 'X'.(1234ABC123456XYZ1234567890ADS)
5. Write a SQL query to return all rows where the value in the Vals column contains more than two dots (.).(testDots)
6. Write a SQL query to count the spaces present in the string.(CountSpaces)
7. write a SQL query that finds out employees who earn more than their managers.(Employee)
8. Find the employees who have been with the company for more than 10 years, but less than 15 years. Display their Employee ID, First Name, Last Name, Hire Date, and the Years of Service (calculated as the number of years between the current date and the hire date).(Employees)

# Medium Tasks
1. Write a SQL query to separate the integer values and the character values into two different columns.(rtcfvty34redt)
2. write a SQL query to find all dates' Ids with higher temperature compared to its previous (yesterday's) dates.(weather)
3. Write an SQL query that reports the first login date for each player.(Activity)
4. Your task is to return the third item from that list.(fruits)
5. Write a SQL query to create a table where each character from the string will be converted into a row.(sdgfhsdgfhs@121313131)
6. You are given two tables: p1 and p2. Join these tables on the id column. The catch is: when the value of p1.code is 0, replace it with the value of p2.code.(p1,p2)
7. Write an SQL query to determine the Employment Stage for each employee based on their HIRE_DATE. The stages are defined as follows:

> - If the employee has worked for less than 1 year → 'New Hire'

> - If the employee has worked for 1 to 5 years → 'Junior'

> -  If the employee has worked for 5 to 10 years → 'Mid-Level'

> -  If the employee has worked for 10 to 20 years → 'Senior'

> - If the employee has worked for more than 20 years → 'Veteran'(Employees)
8. Write a SQL query to extract the integer value that appears at the start of the string in a column named Vals.(GetIntegers)


# Difficult Tasks
1. In this puzzle you have to swap the first two letters of the comma separated string.(MultipleVals)
2. Write a SQL query that reports the device that is first logged in for each player.(Activity)
3. You are given a sales table. Calculate the week-on-week percentage of sales per area for each financial week. For each week, the total sales will be considered 100%, and the percentage sales for each day of the week should be calculated based on the area sales for that week.(WeekPercentagePuzzle)


```sql
CREATE TABLE Employee (
    Id INT,
    Name VARCHAR(50),
    Salary INT,
    ManagerId INT
);

INSERT INTO Employee (Id, Name, Salary, ManagerId) VALUES
(1, 'Joe', 70000, 3),
(2, 'Henry', 80000, 4),
(3, 'Sam', 60000, NULL),
(4, 'Max', 90000, NULL);

CREATE TABLE weather (
    Id INT,
    RecordDate DATE,
    Temperature INT
);

INSERT INTO weather (Id, RecordDate, Temperature) VALUES
(1, '2015-01-01', 10),
(2, '2015-01-02', 25),
(3, '2015-01-03', 20),
(4, '2015-01-04', 30);

CREATE TABLE Activity (
    player_id INT,
    device_id INT,
    event_date DATE,
    games_played INT
);

INSERT INTO Activity (player_id, device_id, event_date, games_played) VALUES
(1, 2, '2016-03-01', 5),
(1, 2, '2016-05-02', 6),
(2, 3, '2017-06-25', 1),
(3, 1, '2016-03-02', 0),
(3, 4, '2018-07-03', 5);

CREATE TABLE MultipleVals 
(
     Id INT
    ,[Vals] VARCHAR(100)
)

 
 
Insert Into MultipleVals values
 (1,'a,b,c')
,(2,'x,y,z')


CREATE TABLE fruits (
    fruit_list VARCHAR(100)
);

INSERT INTO fruits (fruit_list)
VALUES ('apple,banana,orange,grape');

CREATE TABLE RemoveLastComma
(
     Id INT
    ,Val VARCHAR(100)
)

 
INSERT INTO RemoveLastComma VALUES
(1,'Pawan'),
(2,'Pawan,Avtaar,'),
(3,','),
(4,'Hello,'),
(5,'a,a,b,c,'),
(6,NULL),
(7,'')

CREATE TABLE Splitter
(
     Id INT
    ,Vals VARCHAR(100)
)
 
INSERT INTO Splitter VALUES
(1,'P.K'),
(2,'a.b'),
(3,'c.d'),
(4,'e.J'),
(5,'t.u.b')


CREATE TABLE testDots
(
     ID INT
    ,Vals VARCHAR(100)
)
 
INSERT INTO testDots VALUES
(1,'0.0'),
(2,'2.3.1.1'),
(3,'4.1.a.3.9'),
(4,'1.1.'),
(5,'a.b.b.b.b.b..b..b'),
(6,'6.')

CREATE TABLE GetIntegers
(
     Id INT
    ,VALS VARCHAR(100)
)
 
INSERT INTO GetIntegers VALUES
 (1,'P1')
,(2,'1 - Hero')
,(3,'2 - Ramesh')
,(4,'3 - KrishnaKANT')
,(5,'21 - Avtaar')
,(6,'5Laila')
,(7,'6  MMT')
,(8,'7#7#')
,(9,'#')
,(10,'8')
,(11,'98')
,(12,'111')
,(13,NULL)


CREATE TABLE TestPercent
(
    Strs VARCHAR(100)
)
 
INSERT INTO TestPercent
SELECT 'Pawan'
UNION ALL
SELECT 'Pawan%'
UNION ALL
SELECT 'Pawan%Kumar'
UNION ALL
SELECT '%'

CREATE TABLE [dbo].[TestMultipleColumns]
(
[Id] [int] NULL,
[Name] [varchar](20) NULL
)
 
INSERT INTO [TestMultipleColumns] VALUES
(1,    'Pawan,Kumar'),
(2,    'Sandeep,Goyal'),
(3,    'Isha,Mattoo'),
(4,    'Gopal,Ranjan'),
(5,    'Neeraj,Garg'),
(6,    'Deepak,Sharma'),
(7,    ' Mayank,Tripathi')
 

CREATE TABLE CountSpaces
(
texts VARCHAR(100)
)

 
INSERT INTO CountSpaces VALUES
('P Q R S '),
(' L M N O 0 0     '),
('I  am here only '),
(' Welcome to the new world '),
(' Hello world program'),
(' Are u nuts ')

create table p1 (id int, code int)
create table p2 (id int, code int)
insert into p1 select 1,0
insert into p1 select 2,1
insert into p2 select 1,5
insert into p2 select 2,5

CREATE TABLE WeekPercentagePuzzle
(
      Area INT
    , [Date] DATE
    , SalesLocal INT
    , SalesRemote INT
    , [DayName] VARCHAR(4)
    , [DayOfWeek] SMALLINT
    , FinancialWeek TINYINT
    , [MonthName] VARCHAR(15)
    , FinancialYear INT
)

 
INSERT INTO WeekPercentagePuzzle VALUES
(1,'2015-04-01',0,50,'Wed',4,1,'April',2015),
(2,'2015-04-01',null,null,'Wed',4,1,'April',2015),
(3,'2015-04-01',100,0,'Wed',4,1,'April',2015),
(3,'2015-04-01',50,100,'Wed',4,1,'April',2015),
(3,'2015-04-04',50,50,'Sat',7,1,'April',2015);


create table Employees (EMPLOYEE_ID int, FIRST_NAME varchar(50), LAST_NAME varchar(50),EMAIL varchar(255), PHONE_NUMBER varchar(50),HIRE_DATE date,JOB_ID varchar(50),SALARY float,COMMISSION_PCT float, MANAGER_ID int, DEPARTMENT_ID int)

insert into Employees values
(         100,trim('Steven      '),trim('King        '), trim('SKING    '),trim('515.123.4567       '),'2000-06-17',trim('AD_PRES    '),24000.00,0.00,   0,90)
,(         101,trim('Neena       '),trim('Kochhar     '), trim('NKOCHHAR '),trim('515.123.4568       '),'1987-06-18',trim('AD_VP      '),17000.00,0.00, 100,     90)
,(         102,trim('Lex         '),trim('De Haan     '), trim('LDEHAAN  '),trim('515.123.4569       '),'1987-06-19',trim('AD_VP      '),17000.00,0.00, 100,     90)
,(         103,trim('Alexander   '),trim('Hunold      '), trim('AHUNOLD  '),trim('590.423.4567       '),'2015-06-20',trim('IT_PROG    '), 9000.00,0.00, 102,     60)
,(         104,trim('Bruce       '),trim('Ernst       '), trim('BERNST   '),trim('590.423.4568       '),'1987-06-21',trim('IT_PROG    '), 6000.00,0.00, 103,     60)
,(         105,trim('David       '),trim('Austin      '), trim('DAUSTIN  '),trim('590.423.4569       '),'1987-06-22',trim('IT_PROG    '), 4800.00,0.00, 103,     60)
,(         106,trim('Valli       '),trim('Pataballa   '), trim('VPATABAL '),trim('590.423.4560       '),'1987-06-23',trim('IT_PROG    '), 4800.00,0.00, 103,     60)
,(         107,trim('Diana       '),trim('Lorentz     '), trim('DLORENTZ '),trim('590.423.5567       '),'1987-06-24',trim('IT_PROG    '), 4200.00,0.00, 103,     60)
,(         108,trim('Nancy       '),trim('Greenberg   '), trim('NGREENBE '),trim('515.124.4569       '),'1987-06-25',trim('FI_MGR     '),12000.00,0.00, 101,    100)
,(         109,trim('Daniel      '),trim('Faviet      '), trim('DFAVIET  '),trim('515.124.4169       '),'2010-06-26',trim('FI_ACCOUNT '), 9000.00,0.00, 108,    100)
,(         110,trim('John        '),trim('Chen        '), trim('JCHEN    '),trim('515.124.4269       '),'1987-06-27',trim('FI_ACCOUNT '), 8200.00,0.00, 108,    100)
,(         111,trim('Ismael      '),trim('Sciarra     '), trim('ISCIARRA '),trim('515.124.4369       '),'1987-06-28',trim('FI_ACCOUNT '), 7700.00,0.00, 108,    100)
,(         112,trim('Jose Manuel '),trim('Urman       '), trim('JMURMAN  '),trim('515.124.4469       '),'1987-06-29',trim('FI_ACCOUNT '), 7800.00,0.00, 108,    100)
,(         113,trim('Luis        '),trim('Popp        '), trim('LPOPP    '),trim('515.124.4567       '),'1987-06-30',trim('FI_ACCOUNT '), 6900.00,0.00, 108,    100)
,(         114,trim('Den         '),trim('Raphaely    '), trim('DRAPHEAL '),trim('515.127.4561       '),'1987-07-01',trim('PU_MAN     '),11000.00,0.00, 100,     30)
,(         115,trim('Alexander   '),trim('Khoo        '), trim('AKHOO    '),trim('515.127.4562       '),'1987-07-02',trim('PU_CLERK   '), 3100.00,0.00, 114,     30)
,(         116,trim('Shelli      '),trim('Baida       '), trim('SBAIDA   '),trim('515.127.4563       '),'2008-07-03',trim('PU_CLERK   '), 2900.00,0.00, 114,     30)
,(         117,trim('Sigal       '),trim('Tobias      '), trim('STOBIAS  '),trim('515.127.4564       '),'1987-07-04',trim('PU_CLERK   '), 2800.00,0.00, 114,     30)
,(         118,trim('Guy         '),trim('Himuro      '), trim('GHIMURO  '),trim('515.127.4565       '),'1987-07-05',trim('PU_CLERK   '), 2600.00,0.00, 114,     30)
,(         119,trim('Karen       '),trim('Colmenares  '), trim('KCOLMENA '),trim('515.127.4566       '),'1987-07-06',trim('PU_CLERK   '), 2500.00,0.00, 114,     30)
,(         120,trim('Matthew     '),trim('Weiss       '), trim('MWEISS   '),trim('650.123.1234       '),'1987-07-07',trim('ST_MAN     '), 8000.00,0.00, 100,     50)
,(         121,trim('Adam        '),trim('Fripp       '), trim('AFRIPP   '),trim('650.123.2234       '),'2011-07-08',trim('ST_MAN     '), 8200.00,0.00, 100,     50)
,(         122,trim('Payam       '),trim('Kaufling    '), trim('PKAUFLIN '),trim('650.123.3234       '),'2015-07-09',trim('ST_MAN     '), 7900.00,0.00, 100,     50)
,(         123,trim('Shanta      '),trim('Vollman     '), trim('SVOLLMAN '),trim('650.123.4234       '),'1987-07-10',trim('ST_MAN     '), 6500.00,0.00, 100,     50)
,(         124,trim('Kevin       '),trim('Mourgos     '), trim('KMOURGOS '),trim('650.123.5234       '),'1987-07-11',trim('ST_MAN     '), 5800.00,0.00, 100,     50)
,(         125,trim('Julia       '),trim('Nayer       '), trim('JNAYER   '),trim('650.124.1214       '),'1987-07-12',trim('ST_CLERK   '), 3200.00,0.00, 120,     50)
,(         126,trim('Irene       '),trim('Mikkilineni '), trim('IMIKKILI '),trim('650.124.1224       '),'1987-07-13',trim('ST_CLERK   '), 2700.00,0.00, 120,     50)
,(         127,trim('James       '),trim('Landry      '), trim('JLANDRY  '),trim('650.124.1334       '),'2013-07-14',trim('ST_CLERK   '), 2400.00,0.00, 120,     50)
,(         128,trim('Steven      '),trim('Markle      '), trim('SMARKLE  '),trim('650.124.1434       '),'2013-07-15',trim('ST_CLERK   '), 2200.00,0.00, 120,     50)
,(         129,trim('Laura       '),trim('Bissot      '), trim('LBISSOT  '),trim('650.124.5234       '),'2013-07-16',trim('ST_CLERK   '), 3300.00,0.00, 121,     50)
,(         130,trim('Mozhe       '),trim('Atkinson    '), trim('MATKINSO '),trim('650.124.6234       '),'2013-07-17',trim('ST_CLERK   '), 2800.00,0.00, 121,     50)
,(         131,trim('James       '),trim('Marlow      '), trim('JAMRLOW  '),trim('650.124.7234       '),'2013-07-18',trim('ST_CLERK   '), 2500.00,0.00, 121,     50)
,(         132,trim('TJ          '),trim('Olson       '), trim('TJOLSON  '),trim('650.124.8234       '),'2013-07-19',trim('ST_CLERK   '), 2100.00,0.00, 121,     50)
,(         133,trim('Jason       '),trim('Mallin      '), trim('JMALLIN  '),trim('650.127.1934       '),'2013-07-20',trim('ST_CLERK   '), 3300.00,0.00, 122,     50)
,(         134,trim('Michael     '),trim('Rogers      '), trim('MROGERS  '),trim('650.127.1834       '),'2013-07-21',trim('ST_CLERK   '), 2900.00,0.00, 122,     50)
,(         135,trim('Ki          '),trim('Gee         '), trim('KGEE     '),trim('650.127.1734       '),'1987-07-22',trim('ST_CLERK   '), 2400.00,0.00, 122,     50)
,(         136,trim('Hazel       '),trim('Philtanker  '), trim('HPHILTAN '),trim('650.127.1634       '),'1987-07-23',trim('ST_CLERK   '), 2200.00,0.00, 122,     50)
,(         137,trim('Renske      '),trim('Ladwig      '), trim('RLADWIG  '),trim('650.121.1234       '),'1987-07-24',trim('ST_CLERK   '), 3600.00,0.00, 123,     50)
,(         138,trim('Stephen     '),trim('Stiles      '), trim('SSTILES  '),trim('650.121.2034       '),'1987-07-25',trim('ST_CLERK   '), 3200.00,0.00, 123,     50)
,(         139,trim('John        '),trim('Seo         '), trim('JSEO     '),trim('650.121.2019       '),'1987-07-26',trim('ST_CLERK   '), 2700.00,0.00, 123,     50)
,(         140,trim('Joshua      '),trim('Patel       '), trim('JPATEL   '),trim('650.121.1834       '),'1987-07-27',trim('ST_CLERK   '), 2500.00,0.00, 123,     50)
,(         141,trim('Trenna      '),trim('Rajs        '), trim('TRAJS    '),trim('650.121.8009       '),'1987-07-28',trim('ST_CLERK   '), 3500.00,0.00, 124,     50)
,(         142,trim('Curtis      '),trim('Davies      '), trim('CDAVIES  '),trim('650.121.2994       '),'1987-07-29',trim('ST_CLERK   '), 3100.00,0.00, 124,     50)
,(         143,trim('Randall     '),trim('Matos       '), trim('RMATOS   '),trim('650.121.2874       '),'1987-07-30',trim('ST_CLERK   '), 2600.00,0.00, 124,     50)
,(         144,trim('Peter       '),trim('Vargas      '), trim('PVARGAS  '),trim('650.121.2004       '),'1987-07-31',trim('ST_CLERK   '), 2500.00,0.00, 124,     50)
,(         145,trim('John        '),trim('Russell     '), trim('JRUSSEL  '),trim('011.44.1344.429268 '),'1987-08-01',trim('SA_MAN     '),14000.00,0.40, 100,     80)
,(         146,trim('Karen       '),trim('Partners    '), trim('KPARTNER '),trim('011.44.1344.467268 '),'1987-08-02',trim('SA_MAN     '),13500.00,0.30, 100,     80)
,(         147,trim('Alberto     '),trim('Errazuriz   '), trim('AERRAZUR '),trim('011.44.1344.429278 '),'1987-08-03',trim('SA_MAN     '),12000.00,0.30, 100,     80)
,(         148,trim('Gerald      '),trim('Cambrault   '), trim('GCAMBRAU '),trim('011.44.1344.619268 '),'1987-08-04',trim('SA_MAN     '),11000.00,0.30, 100,     80)
,(         149,trim('Eleni       '),trim('Zlotkey     '), trim('EZLOTKEY '),trim('011.44.1344.429018 '),'1987-08-05',trim('SA_MAN     '),10500.00,0.20, 100,     80)
,(         150,trim('Peter       '),trim('Tucker      '), trim('PTUCKER  '),trim('011.44.1344.129268 '),'1987-08-06',trim('SA_REP     '),10000.00,0.30, 145,     80)
,(         151,trim('David       '),trim('Bernstein   '), trim('DBERNSTE '),trim('011.44.1344.345268 '),'1987-08-07',trim('SA_REP     '), 9500.00,0.25, 145,     80)
,(         152,trim('Peter       '),trim('Hall        '), trim('PHALL    '),trim('011.44.1344.478968 '),'1987-08-08',trim('SA_REP     '), 9000.00,0.25, 145,     80)
,(         153,trim('Christopher '),trim('Olsen       '), trim('COLSEN   '),trim('011.44.1344.498718 '),'1987-08-09',trim('SA_REP     '), 8000.00,0.20, 145,     80)
,(         154,trim('Nanette     '),trim('Cambrault   '), trim('NCAMBRAU '),trim('011.44.1344.987668 '),'1987-08-10',trim('SA_REP     '), 7500.00,0.20, 145,     80)
,(         155,trim('Oliver      '),trim('Tuvault     '), trim('OTUVAULT '),trim('011.44.1344.486508 '),'1987-08-11',trim('SA_REP     '), 7000.00,0.15, 145,     80)
,(         156,trim('Janette     '),trim('King        '), trim('JKING    '),trim('011.44.1345.429268 '),'1987-08-12',trim('SA_REP     '),10000.00,0.35, 146,     80)
,(         157,trim('Patrick     '),trim('Sully       '), trim('PSULLY   '),trim('011.44.1345.929268 '),'1987-08-13',trim('SA_REP     '), 9500.00,0.35, 146,     80)
,(         158,trim('Allan       '),trim('McEwen      '), trim('AMCEWEN  '),trim('011.44.1345.829268 '),'1987-08-14',trim('SA_REP     '), 9000.00,0.35, 146,     80)
,(         159,trim('Lindsey     '),trim('Smith       '), trim('LSMITH   '),trim('011.44.1345.729268 '),'1987-08-15',trim('SA_REP     '), 8000.00,0.30, 146,     80)
,(         160,trim('Louise      '),trim('Doran       '), trim('LDORAN   '),trim('011.44.1345.629268 '),'1987-08-16',trim('SA_REP     '), 7500.00,0.30, 146,     80)
,(         161,trim('Sarath      '),trim('Sewall      '), trim('SSEWALL  '),trim('011.44.1345.529268 '),'1987-08-17',trim('SA_REP     '), 7000.00,0.25, 146,     80)
,(         162,trim('Clara       '),trim('Vishney     '), trim('CVISHNEY '),trim('011.44.1346.129268 '),'1987-08-18',trim('SA_REP     '),10500.00,0.25, 147,     80)
,(         163,trim('Danielle    '),trim('Greene      '), trim('DGREENE  '),trim('011.44.1346.229268 '),'1987-08-19',trim('SA_REP     '), 9500.00,0.15, 147,     80)
,(         164,trim('Mattea      '),trim('Marvins     '), trim('MMARVINS '),trim('011.44.1346.329268 '),'1987-08-20',trim('SA_REP     '), 7200.00,0.10, 147,     80)
,(         165,trim('David       '),trim('Lee         '), trim('DLEE     '),trim('011.44.1346.529268 '),'1987-08-21',trim('SA_REP     '), 6800.00,0.10, 147,     80)
,(         166,trim('Sundar      '),trim('Ande        '), trim('SANDE    '),trim('011.44.1346.629268 '),'1987-08-22',trim('SA_REP     '), 6400.00,0.10, 147,     80)
,(         167,trim('Amit        '),trim('Banda       '), trim('ABANDA   '),trim('011.44.1346.729268 '),'1987-08-23',trim('SA_REP     '), 6200.00,0.10, 147,     80)
,(         168,trim('Lisa        '),trim('Ozer        '), trim('LOZER    '),trim('011.44.1343.929268 '),'1987-08-24',trim('SA_REP     '),11500.00,0.25, 148,     80)
,(         169,trim('Harrison    '),trim('Bloom       '), trim('HBLOOM   '),trim('011.44.1343.829268 '),'1987-08-25',trim('SA_REP     '),10000.00,0.20, 148,     80)
,(         170,trim('Tayler      '),trim('Fox         '), trim('TFOX     '),trim('011.44.1343.729268 '),'1987-08-26',trim('SA_REP     '), 9600.00,0.20, 148,     80)
,(         171,trim('William     '),trim('Smith       '), trim('WSMITH   '),trim('011.44.1343.629268 '),'1987-08-27',trim('SA_REP     '), 7400.00,0.15, 148,     80)
,(         172,trim('Elizabeth   '),trim('Bates       '), trim('EBATES   '),trim('011.44.1343.529268 '),'1987-08-28',trim('SA_REP     '), 7300.00,0.15, 148,     80)
,(         173,trim('Sundita     '),trim('Kumar       '), trim('SKUMAR   '),trim('011.44.1343.329268 '),'1987-08-29',trim('SA_REP     '), 6100.00,0.10, 148,     80)
,(         174,trim('Ellen       '),trim('Abel        '), trim('EABEL    '),trim('011.44.1644.429267 '),'1987-08-30',trim('SA_REP     '),11000.00,0.30, 149,     80)
,(         175,trim('Alyssa      '),trim('Hutton      '), trim('AHUTTON  '),trim('011.44.1644.429266 '),'1987-08-31',trim('SA_REP     '), 8800.00,0.25, 149,     80)
,(         176,trim('Jonathon    '),trim('Taylor      '), trim('JTAYLOR  '),trim('011.44.1644.429265 '),'1987-09-01',trim('SA_REP     '), 8600.00,0.20, 149,     80)
,(         177,trim('Jack        '),trim('Livingston  '), trim('JLIVINGS '),trim('011.44.1644.429264 '),'1987-09-02',trim('SA_REP     '), 8400.00,0.20, 149,     80)
,(         178,trim('Kimberely   '),trim('Grant       '), trim('KGRANT   '),trim('011.44.1644.429263 '),'1987-09-03',trim('SA_REP     '), 7000.00,0.15, 149,      0)
,(         179,trim('Charles     '),trim('Johnson     '), trim('CJOHNSON '),trim('011.44.1644.429262 '),'1987-09-04',trim('SA_REP     '), 6200.00,0.10, 149,     80)
,(         180,trim('Winston     '),trim('Taylor      '), trim('WTAYLOR  '),trim('650.507.9876       '),'1987-09-05',trim('SH_CLERK   '), 3200.00,0.00, 120,     50)
,(         181,trim('Jean        '),trim('Fleaur      '), trim('JFLEAUR  '),trim('650.507.9877       '),'1987-09-06',trim('SH_CLERK   '), 3100.00,0.00, 120,     50)
,(         182,trim('Martha      '),trim('Sullivan    '), trim('MSULLIVA '),trim('650.507.9878       '),'1987-09-07',trim('SH_CLERK   '), 2500.00,0.00, 120,     50)
,(         183,trim('Girard      '),trim('Geoni       '), trim('GGEONI   '),trim('650.507.9879       '),'1987-09-08',trim('SH_CLERK   '), 2800.00,0.00, 120,     50)
,(         184,trim('Nandita     '),trim('Sarchand    '), trim('NSARCHAN '),trim('650.509.1876       '),'1987-09-09',trim('SH_CLERK   '), 4200.00,0.00, 121,     50)
,(         185,trim('Alexis      '),trim('Bull        '), trim('ABULL    '),trim('650.509.2876       '),'1987-09-10',trim('SH_CLERK   '), 4100.00,0.00, 121,     50)
,(         186,trim('Julia       '),trim('Dellinger   '), trim('JDELLING '),trim('650.509.3876       '),'1987-09-11',trim('SH_CLERK   '), 3400.00,0.00, 121,     50)
,(         187,trim('Anthony     '),trim('Cabrio      '), trim('ACABRIO  '),trim('650.509.4876       '),'1987-09-12',trim('SH_CLERK   '), 3000.00,0.00, 121,     50)
,(         188,trim('Kelly       '),trim('Chung       '), trim('KCHUNG   '),trim('650.505.1876       '),'1987-09-13',trim('SH_CLERK   '), 3800.00,0.00, 122,     50)
,(         189,trim('Jennifer    '),trim('Dilly       '), trim('JDILLY   '),trim('650.505.2876       '),'1987-09-14',trim('SH_CLERK   '), 3600.00,0.00, 122,     50)
,(         190,trim('Timothy     '),trim('Gates       '), trim('TGATES   '),trim('650.505.3876       '),'1987-09-15',trim('SH_CLERK   '), 2900.00,0.00, 122,     50)
,(         191,trim('Randall     '),trim('Perkins     '), trim('RPERKINS '),trim('650.505.4876       '),'2015-09-16',trim('SH_CLERK   '), 2500.00,0.00, 122,     50)
,(         192,trim('Sarah       '),trim('Bell        '), trim('SBELL    '),trim('650.501.1876       '),'2020-09-17',trim('SH_CLERK   '), 4000.00,0.00, 123,     50)
,(         193,trim('Britney     '),trim('Everett     '), trim('BEVERETT '),trim('650.501.2876       '),'2020-09-18',trim('SH_CLERK   '), 3900.00,0.00, 123,     50)
,(         194,trim('Samuel      '),trim('McCain      '), trim('SMCCAIN  '),trim('650.501.3876       '),'2014-09-19',trim('SH_CLERK   '), 3200.00,0.00, 123,     50)
,(         195,trim('Vance       '),trim('Jones       '), trim('VJONES   '),trim('650.501.4876       '),'2014-09-20',trim('SH_CLERK   '), 2800.00,0.00, 123,     50)
,(         196,trim('Alana       '),trim('Walsh       '), trim('AWALSH   '),trim('650.507.9811       '),'2014-09-21',trim('SH_CLERK   '), 3100.00,0.00, 124,     50)
,(         197,trim('Kevin       '),trim('Feeney      '), trim('KFEENEY  '),trim('650.507.9822       '),'2014-09-22',trim('SH_CLERK   '), 3000.00,0.00, 124,     50)
,(         198,trim('Donald      '),trim('OConnell    '), trim('DOCONNEL '),trim('650.507.9833       '),'2014-09-23',trim('SH_CLERK   '), 2600.00,0.00, 124,     50)
,(         199,trim('Douglas     '),trim('Grant       '), trim('DGRANT   '),trim('650.507.9844       '),'2014-09-24',trim('SH_CLERK   '), 2600.00,0.00, 124,     50)
,(         200,trim('Jennifer    '),trim('Whalen      '), trim('JWHALEN  '),trim('515.123.4444       '),'2014-09-25',trim('AD_ASST    '), 4400.00,0.00, 101,     10)
,(         201,trim('Michael     '),trim('Hartstein   '), trim('MHARTSTE '),trim('515.123.5555       '),'1987-09-26',trim('MK_MAN     '),13000.00,0.00, 100,     20)
,(         202,trim('Pat         '),trim('Fay         '), trim('PFAY     '),trim('603.123.6666       '),'1987-09-27',trim('MK_REP     '), 6000.00,0.00, 201,     20)
,(         203,trim('Susan       '),trim('Mavris      '), trim('SMAVRIS  '),trim('515.123.7777       '),'2024-09-28',trim('HR_REP     '), 6500.00,0.00, 101,     40)
,(         204,trim('Hermann     '),trim('Baer        '), trim('HBAER    '),trim('515.123.8888       '),'2024-09-29',trim('PR_REP     '),10000.00,0.00, 101,     70)
,(         205,trim('Shelley     '),trim('Higgins     '), trim('SHIGGINS '),trim('515.123.8080       '),'2024-09-30',trim('AC_MGR     '),12000.00,0.00, 101,    110)
,(         206,trim('William     '),trim('Gietz       '), trim('WGIETZ   '),trim('515.123.8181       '),'2024-10-01',trim('AC_ACCOUNT '), 8300.00,0.00, 205,    110)



```
