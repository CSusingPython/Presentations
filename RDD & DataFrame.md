# RDD and spark data frame

## key concepts
* refer:  https://www.slideshare.net/yongho/rdd-paper-review, https://www.linkedin.com/pulse/apache-spark-rdd-vs-dataframe-dataset-chandan-prakash

### RDD: Resilient Distributed Datasets
* Its building block of spark. No matter which abstraction Dataframe or Dataset we use, internally final computation is done on RDDs. 
* Disadvantage: RDDs involve overhead of Garbage Collection and Java(or little better Kryo) Serialization which are expensive when data grows.
* Immutable(read-only), partitioned collections of records. 
* linearge를 DAG로 design
* Trasformation & action -> lazy-execution
* When memory exhausted -> LRU로 안쓰는 partition 날림 (?)
* Fault -> use another node

### Spark data frame
* DataFrame is an abstraction which gives a schema view of data.
* offers huge performance improvement over RDDs because of 2 powerful features it has: 
  * Custom Memory management(aka Project Tungsten): Data is stored in off-heap memory in binary format. This saves a lot of memory space. Also there is no Garbage Collection overhead involved. By knowing the schema of data in advance and storing efficiently in binary format, expensive java Serialization is also avoided.
  * Optimized Execution Plans(aka Catalyst Optimizer): Query plans are created for execution using Spark catalyst optimiser. After an optimised execution plan is prepared going through some steps, the final execution happens internally on RDDs only but thats completely hidden from the users.
* data frame doesn't support applying UDR(user defined function)
  * -> use rdd instead


## The key difference between Hadoop MapReduce and Spark
* Hadoop MapReduce: read from and and write to a disk (is able to work with far larger data sets)
* Spark RDD: in-memory (100 times faster than MR)

## Tasks which is good for:
### Hadoop
* Linear processing of huge data sets. 
* Economical solution, if no immediate results are expected.  
  -> Good solution if the speed of processing is not critical. 

### RDD
* Fast data processing, iterative processing
* Near real-time processing
* Graph processing, machine learning
* Joining datasets. 
