# Introduction

## Some Definitions

### What is a Database?

**A Database is:**

-   a structured set of data held in a computer
    
-   a large collection of data organized especially for rapid search and retrieval
   
-   a collection of information that is organized so that it can be easily accessed, managed and updated

The example below shows a staff database consisting of one table containing a row for each staff member. This is similar to a worksheet in an Excel spreadsheet.

![image](https://github.com/DCS-training/IntroToDatabases/blob/main/images/Image1.png)

However, in the above example you can see that there is two sets of  **related**  information; information about staff members and departmental names. As you can see there is much repitition in the  **dept_name**  column. In cases such as this the two sets of related data can be separated into two separate tables. This will form a basic  **Relational Database**

## What is a Relational Database?

**A Relational Database is:**

A relational database is a collection of data items organised as a set of tables. Relationships can be defined between the data in one table and the data in another or many other tables. The relational database system will provide mechanisms by which you can query the data in the tables, re-assemble the data in various ways without altering the data in the actual tables. This querying is usually done using SQL (Structured Query Language). This is a relatively straight forward language to learn, certainly for simple queries.

To transform our original staff database into a relational database we would create a  **departments**  table to hold the name of each unique department and link it to the  **staff**  table using the dept_id which is common in both fields. The following diagam illustrates this.

![image](https://github.com/DCS-training/IntroToDatabases/blob/main/images/Image2.png)

## DB Browser for SQLite

### Launching DB Browser

The Windows installation of DB Browser does not create a desktop icon. To explicitly launch the application after installing it, use the windows button (bottom left of screen) and type in ‘DB Browser’ in the search bar and selecting the application when it appears.

### The Initial screen

The initial screen of DB Browser will look like this;

![image](https://github.com/DCS-training/IntroToDatabases/blob/main/images/Image3.png)

There is a small menu system consisting of File, Edit, View and Help. Below the the menu system is a toolbar with four options; New Database, Open Database, Write Changes and Revert Changes. Below the toolbar is a 4-tabbed pane for; Database Structure, Browse Data, Edit Proagmas and Execute SQL. Initially theese will be quite empty as we haven't created ort opened a database yet. In general we will see how each of these are used as we go through the lesson with the exception of the Edit Pragmas tab which deals with system wide parameters which we won't want to change.

On the right hand side therte are two further panes, at the top is the Edit Database Cell pane which is al greyed out. Below it is a 3-tabbed pane for DB Schema, SQL log and Remote. We are only really interested in the DB Schema tab.

# Working with a Database

## Opening the staff database

For this exercise we will be using the '**staff**' database. You can download it from [this link](https://github.com/DCS-training/IntroToDatabases/blob/main/staff.db)

Save the file to your Home directory or to another appropriate location on your computer.

To open the database in DB Browser do the following;

1. click on the 'open database' button in the toolbar.
2. Navigate to where you have stored the database file on your local machine, select it and click open.

When you open the database, the 'Database Structure' tab on the left andthe 'DB Schema' pane on the right will look very similar to eachother. However the 'DB Schema' pane is only there to allow you to see the details of the schema for the tables. In particular what tables are in the database and the fields and their types which are in each table.

The 'Database Structure' tab on the left allows you to initiate actions on the tables. If you right click on a table name in the 'DB Schema' pane, nothing happens. However, if you do the same in the 'Database Structure' menu you will be given a set of possible actions. These are the same actions that are available from the toolbar at the top of the tab.

![image](https://github.com/DCS-training/IntroToDatabases/blob/main/images/Image4.png)

If you select 'Browse Table', the data from the table is loaded into the 'Browse Data' pane from where it can be examined or filtered. You can also select ther table you wish to Browse directly from here.


## Creating a Database

As well as opening (connecting) to existing databases it is also possible to create new SQLite databases and tables using DB Browser.

To create a database click the  **New Database**  button from the main toolbar (also available from the File menu). You will initially be asked for a name for the database and where you want to save it. It is saved as a single file. If you do not provide an extension default, then a '.db' extension will be used. Although the new database is empty, in that there are no tables in it, the .db file itself is not empty.

Once you have saved the databae file the Create Table wizard will open allowing you to create a table. You can cancel this for now as we will be going through the create table process in a later episode.


### Write Changes & Revert Changes

During your DB Browser session, if you create or delete any tables the changes are not automatically written to the database file. When you try to end the session (i.e. close the application) you will be asked if you want to save the changes you have made

Alternatively you can explicitly save changes or revert changes during a session by use of the  **Write Changes**  and  **Revert Changes**  buttons on the toolbar.

Once written the changes are permanent (there is no concept of multiple 'undo' like you might have in other programs). Revert Changes will take you back to the last Written copy.

# SQL

## What is SQL?

**SQL**  or  **Structured Query Language**  is an internatinal standard for manipulating data in a relational database. Each Relational Database system like Oracle, MySQL or SQLite implements its own variation of the standard.

Fortunateley for the types of commands and queries that we will want to write, all of the implementations are much in agreement. The relatively straightforward  **Select queries**  we will be writing to access data in our SQLite database will execute un-altered in many of the other environments.

Essentially you only have to learn SQL once.

### SQL and Relational database tables

The strength of SQL is that a single SQL statement or query can request data be returned from one or many of the tables in the database. You can essentially define the relationships between tables on-the-fly as part of your query statement. 

## The Select Statement

### Simple SQL queries using the Select statement

For the rest of this exercise we will be looking at the  **SELECT**  statement.

To follow along, you should open the DB Browser application and connect to the 'staff' database you saved earlier.

If you haven't already done so this can be downloaded from  [this link](https://github.com/DCS-training/IntroToDatabases/blob/main/staff.db)

In SQL, querying data is performed by a SELECT statement. A select statement can have 6 key components;

```
SELECT colnames
FROM tablename
GROUP BY colnames
WHERE conditions
HAVING conditions
ORDER BY colnames
```

In practice very few queries will have all of these clauses in them simplifying many queries. On the other hand, conditions in the WHERE clause can be very complex and if you need to JOIN two or more tables together then more clauses (JOIN and ON) are needed.

All of the clause names above have been written in uppercase for clarity. SQL is not case sensitive. Neither do you need to write each clause on a new line, but it is often clearer to do so for all but the simplest of queries.

In this exercise we will start with the very simple and work our way up to the more complex.

The simplest query is effectively one which returns the contents of the whole table.

With staff database open in DB Browser select the 'Execute SQL Tab'.

In the SQL pane type type following:

```
Select * from employees;

```

The '*' character acts as a wildcard meaning all of the columns

![image](https://github.com/DCS-training/IntroToDatabases/blob/main/images/Image5.png)

Click on the 'Play' arrow above the SQL pane to see the results of your query.

It is better practice and generally more efficient to explicitly list the column names that you want returned. For example:

```
Select first_name, last_name from employees;
```

In addition to limiting the columns returned by a query, you can also limit the rows returned. The simplest case is to say how many rows are wanted using the  **`Limit`**  clause. In the example below only the first ten rows of the result of the query will be returned. This is useful if you just want to get a feel for what the data looks like.

```
Select *
From employees
Limit 10;
```

### Exercise 1

Write a query which returns the  **first 5**  rows from the employees table with only the columns  **first_name**,  **last_name**, and  **gender**.

<details>
<summary>Solution Exercise 1 </summary>
<br>

```
Select first_name, last_name, gender
From employees
Limit 5;
```
</details>

## The Where Clause

Usually you will want to restrict the rows returned based on some criteria. i.e. certain values or ranges within one or more columns.

In this example we are only interested in rows where the value in the gender column column is F.

```
Select first_name, last_name, gender
from employees
Where gender = 'F';
```

In addition to using the '=' we can use many other operators such as <, <=, >, >=, <>

```
Select first_name, last_name, hire_date
from employees
Where hire_date < 1990;
```

### Using more complex logical expressions in the  `Where`  clause

We can also use the AND and OR keywords to build more complex selection criteria.

```
Select first_name, last_name, hire_date
from employees
Where hire_date < 1990 and gender = 'M';
```

The following query returns the rows where the employee number is greater than 10001 and less than 10010

```
Select emp_no, first_name, last_name
from employees Where emp_no > 10001 and emp_no < 10010;
```

The  **BETWEEN**  operator sounds as if it should return the same results but note it will return the lowest and highest values as well.

```
Select emp_no, first_name, last_name
from employees
Where emp_no between 10001 and 10010;
```

#### Using the  `LIKE`  operator

The LIKE operator is used in a  `WHERE`  clause to search for a specified pattern in a column. It uses the Percent sign (%) to represent any value

```
Select first_name, last_name
from employees
Where first_name LIKE 'F%';
```

### Exercise 2

Write a query which returns the  **emp_no**,  **first_name**, and  **last_name**  from the employees table table. The gender should all be Male and the emp_id should be between 10050 and 10060.

<details>
<summary>Solution Exercise 2</summary>
<br>

```

Select emp_no, first_name, last_name
from employees
Where emp_no between 10050 and 10060
And gender = 'M';

                              
```

Note: This query returns results including the lowest and highest emp_no where intuitively you may have expected these to be excluded and only numbers in between the highest and lowest to be returned.
</details>

## Sorting Results

If you want the results of your query to appear in a specific order, you can use the  **ORDER BY**  clause

```
Select first_name, last_name
from employees
Order by last_name;
```

By default the SQL assumes Ascending order. You can make this more explicit by using the ASC or DESC keywords.

```
Select first_name, last_name
from employees
Order  by last_name Desc;
```

You can also order by multiple columns

```
Select first_name, last_name, gender
from employees
Order by gender Desc, last_name Asc;
```
## Aggregation

### Using built-in statistical functions

Aggregate functions are used to perform some kind of mathematical or statistical calculation across a group of rows. The rows in each group are determined by the different values in a specified column or columns. Alternatively you can aggregate across the entire table.

If we wanted to know the minimum, average and maximum dates of birth (birth_date) across the whole employees table we could write a query such as this;

```
SELECT
    min(birth_date),
    avg(birth_date),
    max(birth_date)
FROM employees;

```

This sort of query provides us with a general view of the values for a particular column or field across the whole table.

Another useful function is  `count`. This can be used to return a total of records corresponding to a particular condition. e.g How many employees are female.

```
select count(*) from employees  where gender = 'F';
```

`count`,  `min`  ,  `max`  and  `avg`  are built in aggregate functions in SQLite (and any other SQL database system). There are other such functions avaialable. A complete list can be found in the SQLite documentation  [here](https://sqlite.org/lang_aggfunc.html)

## Joins

### keypoints:

-   Joins are used to combine data from two or more tables.
-   Tables to be joined must have a column in each which represent the same thing.
-   There are several different types of joins.
-   The Inner join is the most commonly use.

### About table joins

In any relational database system, the ability to join tables together is a key querying requirement. Joins are used to combine the rows from two (or more) tables together to form a single table. A join between tables will only be possible if they have at least one column in common. The column doesn’t have to have the same name in each table, and quite often they won’t, but they do have to have a common usage.

If you look at the Schema for the staff database in DB Browser you will see that the  **department**  table and the  **employees**  table both contain a common column 'dept_id'. This means that there is a relationship between the two tables; inserting a dept_id number in the employee record makes details in the department table potentially available. We can use an SQL joining statement to list employees along with their relevant department.

```
select first_name, last_name, dept_name from employees
join departments on employees.dept_id = departments.dept_id;
```

And we can order them by department

```
select first_name, last_name, dept_name from employees
join departments on employees.dept_id = departments.dept_id
order by dept_name;
```

## Views

### Using SQL code to create views

We can create a View to act as a representation of our data in a format that is useful to us. For example, in the last section we ran an SQL query with a join to give us a summary of the employees and their departments.

```
select emp_no, first_name, last_name, gender, birth_date, dept_name, hire_date from employees
join departments on employees.dept_id = departments.dept_id order by last_name;
```

Once this query has been run in DB Browser it can be saved as a View.

Run the above SQL query and in the results screen select the icon indicated in the following image.  
(Note. Depending on your Operating system this icon may be located on the top menu bar).

![image](https://github.com/DCS-training/IntroToDatabases/blob/main/images/Image6.png)

Select 'Save as view' and give the view a name. Now when you select the 'Browse Data' tab this View will be available in addition to the employees and the departments tables.

One advantage of using a View is that any changes to the underlying table will be reflected in the View. For example, changing the name of a department in the departments table will be reflected in every row where that department name appears in the view.

Try changing the name 'Quality Management' to 'Quality Assurance' in the departments table, save the changes by clicking on 'Write Changes' and open the view again to review the changes.

# Import/Export

## Import / Export a Database

### To export a complete database

In DB Browser

-   Select 'File'
-   Hover over 'Export'
-   Select 'Database to SQL file'
-   Select the tables and views you wish to include
-   Click OK and accept the accepted filename or rename it to something else

### To import a complete database

In DB Browser

-   Select 'File'
-   Hover over 'Import'
-   Select 'Database from SQL file'
-   Browser to your database export file and click 'open'

## Export to CSV

### Exporting a table or view to a csv file

In DB Browser

-   Select 'File'
-   Hover over 'Export'
-   Select 'Database as CSV file'
-   Select the table or view you wish to export and click OK

If the file is saved with a .csv extension it can be opened and read by MS Excel

## Create Database from CSV

### Create a new database and populate it with data from a CSV file

For this exercise we will use the [tweets.csv](https://github.com/DCS-training/IntroToDatabases/raw/main/tweets.csv)  file.

Download this file to your home directory (right-click on link and select 'Save Link As')

In DB Browser

-   Select 'New Database' from the top left menu
-   Save the database as trump.db and save it to your home directory
-   When the 'Edit table Definition' box appears select 'Cancel'
-   Select File > Import > Table from CSV file
-   Browse to the 'tweets.csv' file, select it and click 'Open'
-   A preview of the data is displayed; make sure the 'Column Names in Fist Row' checkbox is ticked and click on OK
-   Click 'Write Changes'


## More SQL

Examine the data in the  **tweets**  table that you have imprted into the trump.db

The data in this table is a list of > 50000 tweets by Donald Trump from 2009 to 2019.

Each tweet has been analysed to give it a sentiment score (whether it is positive or negative).

The  **Sentiment**  column indicates the overall sentiment, i.e. Posive, Negative or Neutral

The  **Polarity**  column provides a numerical score ranging from -1 (very negative) through 0 (Neutral) to 1 (very positive)

These scores allow us to perform some analysis of the data using SQL

```
select
min(Polarity),
avg(Polarity),
max(Polarity)
from tweets;

```

This returns the most positve, negative and average sentiments of the tweets. As you can see they vary from very negative to very positive with the average being inclined to positive.

The average Polarity is around 0.18

But what if we change the query to filter the tweet by a particular piece of text.

```
select
avg(Polarity) from tweets
where TweetText LIKE '%Clinton%';
```

Using the wildcard % before and after our term ensures that it finds any reference to it in the tweet text.

You can see from the result of this query that the Polarity of the tweet has dropped significantly to about 0.003

Experiment by editing this query with your own keywords, eg

```
select
avg(Polarity) from tweets
where TweetText LIKE '%Ivanka%';
```

```
select
avg(Polarity) from tweets
where TweetText LIKE '%Obama%';
```

You can also use the % wildcard just to examine tweets containing a specific term

```
select
* from tweets
where TweetText LIKE '%impeach%'
order by created;
```

The results of any of these queries can be easily saved to a CSV file:

Just click on the button we used earlier to save a View, but this time select 'Export to CSV'

![image](https://github.com/DCS-training/IntroToDatabases/blob/main/images/Image7.png)

# Resources

## Useful Links

-   [DB Browser for SQLite](http://sqlitebrowser.org/)
-   [SQL Tutorial](https://www.w3schools.com/sql/)
-   [SQL Quick Reference](https://www.w3schools.com/sql/sql_quickref.asp)

## Tutorial Files

-   [trump-tweet-archive.csv](https://github.com/DCS-training/IntroToDatabases/blob/main/trump-tweet-archive.csv)  - Trump Tweets since 2009
    
-   [tweets.csv](https://github.com/DCS-training/IntroToDatabases/blob/main/tweets.csv)  - Trump Tweets analysed for sentiment
    
-   [trump-tweets.db](https://github.com/DCS-training/IntroToDatabases/blob/main/trump-tweets.db)  - SQLite database of Trump's tweets analysed for sentiment
    
-   [staff.db](https://github.com/DCS-training/IntroToDatabases/blob/main/staff.db)  - Example Staff database

### Additional Datasets

-   [life_expectancy.csv](https://github.com/DCS-training/IntroToDatabases/blob/main/life_expectancy.csv)
    
-   [fertility_rates.csv](https://github.com/DCS-training/IntroToDatabases/blob/main/fertility_rates.csv)

## Further Exercises

### Sinking of the Titanic

RMS Titanic was a British passenger liner operated by the White Star Line that sank in the North Atlantic Ocean on 15 April 1912, after striking an iceberg during her maiden voyage from Southampton to New York City. Of the estimated 2,224 passengers and crew aboard, more than 1,500 died.

One of the reasons that the shipwreck resulted in such loss of life was that there were not enough lifeboats for the passengers and crew. Although there was some element of luck involved in surviving the sinking, some groups of people were more likely to survive than others.

The  [titanic.csv](https://github.com/DCS-training/IntroToDatabases/blob/main/titanic.csv)  file contains data for 887 of the real Titanic passengers. Each row represents one person. The columns describe different attributes about the person including whether they survived, their age, their passenger-class, their sex and the fare they paid.

A usefule exercise to try on your own, using some of the techniques we've explored, would be to compare the survival rate of different groups of passengers, e.g. by gender, passenger class, age, etc.

For example the following shows the average rate of survival by sex (the term 'gender' had not been coined at this stage)

```
select Sex, avg(Survived) from titanic group by Sex;
```

The results seem to suggest that the 'women and children first' convention was generally observed

The following query looks at survival rates by passenger class.

```
select Pclass, avg(Survived) from titanic group by Pclass;
```

The results suggest that chances of survival were dependant on the cost of your ticket. Possibly because the cheaper the ticket the further you were from a lifeboat.
