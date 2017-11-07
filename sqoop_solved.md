<h2>Snappy Compression</h2>

Snappy (previously known as Zippy) is a fast data compression and decompression library written in C++ by Google based on ideas from LZ77 and open-sourced in 2011.

It does not aim for maximum compression, or compatibility with any other compression library;

instead, it aims for very high speeds and reasonable compression. Compression speed is 250 MB/s and decompression speed is 500 MB/s using a single core of a Core i7

Snappy is widely used in Google projects like BigTable, MapReduce and in compression data in Google's internal RPC systems. It can be used in open-source projects like MariaDB ColumnStore,Cassandra, Hadoop, LevelDB, MongoDB, RocksDB, Lucene. Decompression is tested to detect any errors in the compressed stream. Snappy does not use inline assembler (except some optimizations and is portable.




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
