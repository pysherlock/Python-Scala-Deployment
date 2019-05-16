# Serilization Problem of SparkContext&StreamingContext


## Stateful Streaming

2. Key value pairs in the DStream
A common mistake is to wonder why we’re not seeing stateful transformation methods (updateStateByKey and mapWithState as we’ll soon see) when working with a DStream. Stateful transformations require that we operate on a DStream which encapsulates a key value pair, in the form of DStream[(K, V)] where K is the type of the key and V is type the value. Working with such a stream allows Spark to shuffle data based on the key, so all data for a given key can be available on the same worker node and allow you to do meaningful aggregations.
