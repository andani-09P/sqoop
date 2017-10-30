# sqoop
Sqoop: Import Data From MySQL to Hive


This chapter describes how to import data from MySQL database to Hadoop HDFS. 
The ‘Import tool’ imports individual tables from RDBMS to HDFS.
Each row in a table is treated as a record in HDFS.
All records are stored as text data in the text files or as binary data in Avro and Sequence files.

<h4> Syntax </h4>
The following syntax is used to import data into HDFS.
```
sqoop import (generic-args) (import-args) </br>
```

With the generic arguments, you point to your MySQL database and provide the necessary login information, just as you did with the preceding list-tables tool. 
In the import arguments, you (the user) have the ability to specify what you want to import and how you want the import to be performed.


Importing a Table
Sqoop tool ‘import’ is used to import table data from the table to the Hadoop file system as a text file or a binary file.

The following command is used to import the emp table from MySQL database server to HDFS.
```
sqoop import --connect jdbc:mysql://localhost/sqoop --username root -P --table customer --m 1 --target-dir /sqoop
```

list tables in mysql using sqoop command
```
sqoop list-tables --connect jdbc:mysql://localhost/<database_name> --username root -P
```

Import Subset of Table Data
We can import a subset of a table using the ‘where’ clause in Sqoop import tool. It executes the corresponding SQL query in the respective database server and stores the result in a target directory in HDFS.

The syntax for where clause is as follows.
```
--where <condition>
```
The following command is used to import a subset of emp_add table data. The subset query is to retrieve the employee id and address, who lives in Secunderabad city.
```
 sqoop import \
--connect jdbc:mysql://localhost/userdb \
--username root \
--table emp_add \
--m 1 \
--where “city =’sec-bad’” \
--target-dir /wherequery
```
