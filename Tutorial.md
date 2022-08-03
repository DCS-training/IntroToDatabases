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
