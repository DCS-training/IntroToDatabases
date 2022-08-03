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
