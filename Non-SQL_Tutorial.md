
# What is a Non-SQL Database? 

A non-SQL database is a database that:
- can store and handle data that doesn't fit into rows and columns
- can handle data that is not uniform, or in different formats
- typically stores data in a single structure, such as a json

Below is an example of a non-sql database on MongoDB, in the MongoDB Compass UI. The data consists of public metrics from Twitter - pseudoanonymised and preprocessed.

![Sample Image](https://github.com/DCS-training/IntroToDatabases/blob/main/images/Markdown%20file.png)

In the above example, you can also see an example of nested data under sentiment_scores. This is the result of a sentiment analysis operation performed using VADER in Python. The scores have been stored within the document, and can be opened using the drop down arrow in the MongoDB Compass UI. Nested data is standard in a Json format, but allows your object to include its own Rows/Columns structured data. This is very handy if you have associated strucutred data, such as image metadata, or comments to social media posts for example.


## MongoDB

MongoDB is a database provider with different tools for their operation. We will be stting up a database, and installing the MongoDB Compass, to easily develop and navigate a database. 
MongoDB is cloud based, and the creation of a database requires registration. 

*The Setup*

Follow this link: https://www.mongodb.com/

Sign in using either gmail or github account.
Follow the instructions verify your email address and setup Multi factor authentication.

Below the the menu system is a toolbar with four options; New Database, Open Database, Write Changes and Revert Changes. Below the toolbar is a 4-tabbed pane for; Database Structure, Browse Data, Edit Proagmas and Execute SQL. Initially theese will be quite empty as we haven't created ort opened a database yet. In general we will see how each of these are used as we go through the lesson with the exception of the Edit Pragmas tab which deals with system wide parameters which we won't want to change.

When accepted, there are a series of questions which will shape you experience of the system

![Sample Image](https://github.com/DCS-training/IntroToDatabases/blob/main/images/mongo%20getting%20to%20know%20you.png)

Under "Getting to know your project", select the appropriate answers for your needs. If you are unsure or do not know yet, input the below:
What programming language are you primarily building on MongoDB with?
- Python

What type(s) of data will your project use?
- Not sure / None

Will your application include any of the following architectural models?
- Not sure / None

In the following screen 'Deploy your cluster', select 'Free'. Unless storing large multi-media files on the cloud, the free version is more than enough to train and learn with Mongo, and more so to create a referential database to larger datasets stored elsewhere.

Click Create Deployment

*Creating the Cluster*
A MongoDB cluster is a group of connected MongoDB instances (nodes). This faciliates multiple data access points and sharing of the database across teams.

Connect to Cluster0
On the next screen, click 'Choose a Collection Method', then click 'Compass'.

Select the following:
Connecting with MongoDB Compass
- I don't have MongoDB Compass Installed

1. Select your operating system and download MongoDB Compass
- [select appropriate system]
- Download and install Compass

2. Copy the connection string, then open MongoDB Compass
- You must copy the Connection String and save this somewhere secure and accessible. Such as Evernote, or in an encrypted drive.

Click done.

### MongoDB Compass
Open the compass on your OS. On the UI there is a + next to Connections, click this and copy the saved connection string into the URL box. Name your database, and click Save and Connect.
If you even need your string again, you can find it on the Project Overview Page. Note that you will need to insert your password into the string when copying, as below:
mongodb+srv://alexwarrencrest_db_user:<db_password>@cluster0.bnjltc7.mongodb.net/?appName=Cluster0

To create a database, load your cluster and click the + next to the CLuster name in the left hand panel. In mongo, databases are formed of multiple collections, each of which stores searchable data.
Name the Database 'SD_Mongo', and then name the collection 'SIMD_Ranks'.

For this session, we will be using the Scottish Index of Multiple Deprivation Dataset, you can download it here:https://github.com/DCS-training/IntroToDatabases/blob/main/SIMD%20Ranks.csv 

Save this file locally to your device or appropriate directory. To load this data into your database, click the green plus, and import JSON or CSV file. 
Note that each row is now an individual document, stored and displayed in a JSON format. 

We will be exploring only the Documents and Aggregations tabs today. 

The Documents tab allows you to view and scroll through the documents. It is useful to quickly asses whether the data looks as expected, and to identify features and commonalities across the large dataset.
This tab also allows basic queries to return results through the compass using Mongo Query Language. For example:
{Council_area: "Aberdeen City"}
This will return all results where the value of Council_area is Aberdeen City.

The Query generator also generates queries from simple English. The results with differ so be specific and use known terms in the database. Try the below:
find the top 10 Data_zones by population
find the top 10 Data_zones by population, and return full documents

The Explain tab provides an exact breakdown of the operations that the compass has undertaken. 

### The Aggregations Tab

The aggregations tab faciliates more complex operations. To create a new aggregation, click the tab and insert this query:
find the highest 5% of zones by Housing_Domain_Rank, and save as new collection


Then click Run

Try this with other perametres, and build your database through coolections of aggregated data. 
You will notice that different operations appear at different stages. 


`Stage 1 $setWindowFields
{
  sortBy: {
    SIMD2020_Housing_Domain_Rank: -1
  },
  output: {
    percentile: {
      $percentRank: {}
    }
  }
}`

`Stage 2 $match
{
  percentile: {
    $gte: 0.95
  }
}`

`Stage 3 '$Out'
"Top5Percent_Housing_Domain_Rank"`

Much like programmes, Mongo completes each operation iteratively.
'Out' for example is similar to export in other programmes, and writes a new collection with the results of the aggregation. It is usually in the final stage. 
'Match' is a function useful for searching based on specific variables. It is maleable enough to take handle a range, mean or other distribtuions of numerical data, and also exact strings.
'Count' is similarly useful for summarising groups of documents.

Click the drop down menu for the operations in each stage to scroll through the operations and read their descriptions.


All new collections will be saved as they are created. When you end and return to the session, the data will remain and there is no need to save it again.
However, there is no 'undo' button in the compass. So it is a good idea to create duplicate backups of the raw data and at different stages, incase of an error.  You can create a backup in a number of ways. The easiest is to create an aggregation that duplicates the data:
Create a duplicate of this collection called Backup_SIMD_Ranks
or create a stage manually 
$out
"Backup_SIMD_Ranks"

This sort of practice provides you with a set of stored collections that can be reloaded if needed. They are also stored together in the UI and are therefor legible.


## Import and Export

Data can be exported in the UI to both json and csv formats. An entire collection can be exported, or the results of a specific aggregation.
Export the collection Top5Percent_Housing_Domain_Rank to CSV, and to JSON. 

### In Python and R

Both Python and R have dedicated packages to work with a mongoDB database. 

In python we use PyMongo.

#### Python
`pip install pymongo`

`from pymongo import MongoClient` 

#A clean way to load data into Python
Connection_String = [Your Connection String]
client = MongoClient(Connection_String)
db = client["SD_Mongo"]
collection = db["SIMD_Ranks"]
data = collection.find()

#or a compressed version
Connection_String = [Your Connection String]
client = MongoClient(Connection_String)
data = client["SD_Mongo"]["SIMD_Ranks"].find()

#an operation to transform data

#Upload new data to replace a collection
conn$drop()        # deletes collection
conn$insert(data)  # uploads fresh data

#Warning. Be sure to upload data to either a new collection, or have a backup other wise it with either upend or overright what is already stored there.

#Create a new collection
new_conn <- mongo(
  collection = "New_Collection_Name",
  db = "SD_Mongo",
  url = connection_string
)
#Replace a collection
new_conn$drop()        # deletes collection
new_conn$insert(data)  # uploads fresh data

#Upload a single Document
new_conn$insert('{"Col1": "value", "Col2": value}')

#### R 
In R we use mongolite

`install.packages("mongolite")
library(mongolite)

connection_string <- "[Your Connection String]"

conn <- mongo(
  collection = "SIMD_Ranks",
  db = "SD_Mongo",
  url = connection_string
)

data <- conn$find()` 

#Point to a NEW collection name
conn <- mongo(
  collection = "new_collection_name",
  db = "SD_Mongo",
  url = connection_string
)

#Insert data → this creates the collection
conn$insert(data)


## Resources
https://learn.mongodb.com/ 
https://www.mongodb.com/resources/languages/pymongo-tutorial
https://cran.r-project.org/web/packages/mongolite/mongolite.pdf

