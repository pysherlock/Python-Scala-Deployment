# Serilization Problem of SparkContext&StreamingContext


## Stateful Streaming

2. Key value pairs in the DStream

When working with a DStream. Stateful transformations require that we operate on a DStream which encapsulates a key value pair, in the form of DStream[(K, V)] where K is the type of the key and V is type the value. Working with such a stream allows Spark to shuffle data based on the key, so all data for a given key can be available on the same worker node and allow you to do meaningful aggregations.

Be careful, the key-value pair in DStream[(K, V)] should have unique key per micro-batch. So before output the DStream[(K, V)], a "reduceByKey" is necessary. (TBC: what is the side impact of replica keys)




### transient keyword

**transient** is a Java keyword which marks a member variable not to be serialized when it is persisted to streams of bytes. When an object is transferred through the network, the object needs to be 'serialized'. Serialization converts the object state to serial bytes. Those bytes are sent over the network and the object is recreated from those bytes. Member variables marked by the java transient keyword are not transferred; they are lost intentionally. It means when JVM comes across transient keyword, it ignores original value of the variable and save default value of that variable data type.
