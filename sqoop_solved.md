<h2>Snappy Compression</h2>
Snappy is supported for all CDH components. How you specify compression depends on the component.

Continue reading:

Using Snappy with HBase</br>
Using Snappy with Hive or Impala</br>
Using Snappy with MapReduce</br>
Using Snappy with Pig</br>
Using Snappy with Spark SQL</br>
Using Snappy Compression with Sqoop 1 and Sqoop 2 Imports</br>



<h3>Using Snappy Compression with Sqoop 1 and Sqoop 2 Imports</h3>
Sqoop 1 - On the command line, use the following option to enable Snappy compression:</br>

```
--compression-codec org.apache.hadoop.io.compress.SnappyCodec
```

Cloudera recommends using the --as-sequencefile option with this compression option.</br>


Sqoop 2 - When you create a job (sqoop:000> create job), choose 7 (SNAPPY) as the compression format.
