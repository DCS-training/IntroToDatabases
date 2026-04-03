
# Intro to Databases

This repository host the material connected to a training developed by **Dave Elsmore**, and **Alex Crest**.
Managing data has become increasingly important in the Humanities and Social Sciences. 
Databases provide a powerful tool to allow for the storage, structuring and analysis of large amounts of data. 

There are two workshops: one on relational databases and anothe on non-relational databases. The former uses SQLite, and the latter MongoDB, both of which are flexible open-source programmes, to learn some of the basic concepts of database design and usage. 

In both tutorials you can learn: Basic database design, Importing and exporting data, Querying datasets, Analysing your data.

## Copyright

This repository has a [![License: CC BY-NC 4.0](https://licensebuttons.net/l/by-nc/4.0/80x15.png)](https://creativecommons.org/licenses/by-nc/4.0/) license

## How to use this repository

There are two options:
Follow along the tutorial using the ['SQLTutorial.md'](https://github.com/DCS-training/IntroToDatabases/blob/main/SQL_Tutorial.md) file. 
Or for Non-Sql users ['Non-SQL_Tutorial.md'](https://github.com/DCS-training/IntroToDatabases/blob/main/Non-SQL_Tutorial.md) 

You will also need to install **DBrowser for SQLite**  for the SQL tutorial **MongoDB** for the non SQL tutorial to create and manage the databases.

## Software Installation

**DB Browser for SQLite**  is a high quality, visual, open source tool to create, design, and edit database files compatible with SQLite. It can be installed on both Windows and on Mac operating systems.

### Installing DB Browser for SQLite

The software can be downloaded from the  [DB Browser](http://sqlitebrowser.org/dl/)  site You can select the specific version you require for your operating system. There are downloads for Windows and Mac users. For various Linux distributions there are detailed instructions at the bottom of the page.

#### Installing on Windows.

For a current Windows environment the 64-bit windows download will be most appropriate.

The download is a windows executable file which you can run by double clicking it. It opens an installation wizard. You can default all of the options in the wizard. You will require admin permissions on the PC/Laptop you install on. By default the application is launched automatically when the installation is complete. It does not create an icon on the desktop. To explicitly launch the application after installing it, use the windows button (bottom left of screen) and type in ‘DB Browser’ in the search bar and selecting the application when it appears.

#### Installing on MacOS X

An OSX installer can be found here:

[http://sqlitebrowser.org/dl/](http://sqlitebrowser.org/dl/)

### MongoDB

MongoDB is a popular, open-source, NoSQL database system designed for handling large volumes of unstructured or semi-structured data. It uses a flexible, document-based model (JSON-like format) and is widely used for modern web and cloud applications. MongoDB can be installed on Windows, macOS, and various Linux distributions.

#### Installing MongoDB

The software can be downloaded from the MongoDB official website: https://www.mongodb.com/try/download/community

You can select the appropriate version based on your operating system:

Windows: Download the MSI installer and follow the setup wizard. You can choose between a complete installation or a custom setup.
macOS: Install using the provided .tgz archive or via package managers like Homebrew (brew install mongodb-community).
Linux: Detailed installation instructions are available for different distributions (such as Ubuntu, Debian, and Red Hat) on the download page.

After installation, you can verify that MongoDB is running and connect using the MongoDB shell (mongosh) or a graphical interface like MongoDB Compass.
