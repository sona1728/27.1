Ques: Explain the following in brief with an example.
● Map side Join
● Reduce side Join
● Bucket Map Join
● SMBM Join

Ans: 

# Map side Join:
- The inputs for to each map must be partitioned and sorted in a specific way. Each input dataset must be divided into the same number of partitions, and it must be sorted by the same key (the join key) in each source.

- All the records for a particular key must reside in the same partition and which is mandatory. A map-side join can be used to join the outputs of several jobs that had the same number of reducers, the same keys and output files that are no bigger than the HDFS block size.

- Using the org.apache.hadoop.mapred.join.CompositeInputFormat class we can achieve this. The join type (Inner or Outer) is configurable using the join expression.

We can achieve following kind of joins using Map-Side techniques,

1) Inner Join
2) Outer Join
3) Override – MultiFilter for a given key, prefered values from the right source

# Reduce side Join:
- Reduce-Side joins are more simple than Map-Side joins since the input datasets need not to be structured. But it is less efficient as both datasets have to go through the MapReduce shuffle phase.
- The records with the same key are brought together in the reducer.
- We can also use the Secondary Sort technique to control the order of the records.

# Bucket Map Join:
- 
