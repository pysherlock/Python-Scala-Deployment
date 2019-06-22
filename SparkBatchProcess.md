# Spark Big data process
This document is to summarize important knowledge, interesting use cases, and how to be high-performance of Spark Big data process

## Use Parquet in Spark
***Parquet*** is a columnar format that is supported by many other data processing systems. 
Spark SQL provides support for both reading and writing Parquet files that automatically preserves the schema of the original data.

Because parquet file has preserved schema, it could really improve the performance and reduce disk space by parsing original data (ex: text) to parquet file.
And also, parquet supports snappy compression. 

  ### Split big job into several steps
  Use case: A batch with 3 months data which has 200GB per day
  

## Dealing with unbalance data
  Partition, Partitioner
