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
