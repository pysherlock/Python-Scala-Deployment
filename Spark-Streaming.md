# Spark Streaming


## Stateful Streaming


2. Key value pairs in the DStream

When working with a DStream. Stateful transformations require that we operate on a DStream which encapsulates a key value pair, in the form of DStream[(K, V)] where K is the type of the key and V is type the value. Working with such a stream allows Spark to shuffle data based on the key, so all data for a given key can be available on the same worker node and allow you to do meaningful aggregations.

Be careful, the key-value pair in DStream[(K, V)] should have unique key per micro-batch. So before output the DStream[(K, V)], a "reduceByKey" is necessary. (TBC: what is the side impact of replica keys)

### transient keyword

**transient** is a Java keyword which marks a member variable not to be serialized when it is persisted to streams of bytes. When an object is transferred through the network, the object needs to be 'serialized'. Serialization converts the object state to serial bytes. Those bytes are sent over the network and the object is recreated from those bytes. Member variables marked by the java transient keyword are not transferred; they are lost intentionally. It means when JVM comes across transient keyword, it ignores original value of the variable and save default value of that variable data type.

We can avoid some cases of SparkContext serilization problem By using the transient keyword, since SparkContext is not serilizable.


### Difference between batch interval, sliding interval and window size in spark streaming

1. ***batch interval*** - it is time in seconds how long data will be collected before dispatching processing on it. For example if you set batch interval 5 seconds - Spark Streaming will collect data for 5 seconds and then kick out calculation on RDD with that data.

2. ***window size*** - it is interval of time in seconds for how much historical data shall be contained in RDD before processing. For example you have 1 second batch interval and window size of 2 - in that case you will have calculation kicked out each second for 2 previous batches. E.g at time=3 you will have data from batch at time=2 and time=3.

3. ***sliding interval*** - is amount of time in seconds for how much the window will shift. For example in previous example sliding interval is 1 (since calculation is kicked out each second) e.g. at time=1, time=2, time=3... if you set sliding interval=2, you will get calculation at time=1, time=3, time=5...



Possible exception cases:
  
  1. SparkException: org.apache.spark.streaming.dstream.MappedDStream@****** has not been initialized
  
  https://www.waitingforcode.com/apache-spark-streaming/sparkexception-org.apache.spark.streaming.dstream.MappedDStream-has-not-been-initialized/read#explaining_mappeddstream_has_not_been_initialized_exception
