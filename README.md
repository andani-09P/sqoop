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

<h3>Import Subset of Table Data</h3>

We can import a subset of a table using the ‘where’ clause in Sqoop import tool. It executes the corresponding SQL query in the respective database server and stores the result in a target directory in HDFS.


```
sqoop import 
--connect jdbc:mysql://localhost/userdb 
--username root 
--table emp_add 
--m 1 
--where “city =’sec-bad’” 
--target-dir /query
```

<h3>Incremental Import</h3>
It is required to add ‘incremental’, ‘check-column’, and ‘last-value’ options to perform the incremental import.


like if data is being updated and we need to in update data in hdfs also

```
--incremental <mode>
--check-column <column name>
--last value <last check column value>
```


command


```
sqoop import \
--connect jdbc:mysql://localhost/userdb \
--username root \
--table emp \
--m 1 \
--incremental append \
--check-column id \
-last value 1205
```

<h4>The following syntax is used to import all tables.</h4>


```
$ sqoop import-all-tables (generic-args) (import-args) 
```


command

```
sqoop import-all-tables \
--connect jdbc:mysql://localhost/userdb \
--username root
```



<h4> export data back from the HDFS to the RDBMS database</h4>

```
 sqoop-export (generic-args) (export-args)
 ```
 command

```
 sqoop export \
--connect jdbc:mysql://localhost/db \
--username root \
--table employee \ 
--export-dir /emp/emp_data
```


<h4>Create Job (--create)</h4>

```
sqoop-job (generic-args) (job-args)
   [-- [subtool-name] (subtool-args)]
```

command

```
sqoop job --create myjob \
--import \
--connect jdbc:mysql://localhost/db \
--username root \
--table employee --m 1
```

<h4>Verify Job (--list)</h4>

```
sqoop job --list
```

<h4>Execute Job (--exec)</h4>

```
sqoop job --exec myjob
```

