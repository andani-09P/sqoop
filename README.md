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
sqoop-import (generic-args) (import-args)
```


Importing a Table
Sqoop tool ‘import’ is used to import table data from the table to the Hadoop file system as a text file or a binary file.

The following command is used to import the emp table from MySQL database server to HDFS.
```
sqoop import --connect jdbc:mysql://localhost/sqoop/ --username root -p --table customer --m 1
```

list tables in mysql using sqoop command
```
sqoop list-tables --connect jdbc:mysql://localhost/<database_name> --username root -P
```

