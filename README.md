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
- A bucket map join is used when the tables are large and all the tables used in the join are bucketed on the join columns. In this type of join, one table should have buckets in multiples of the number of buckets in another table.

For example:

if one table has 2 buckets then the other table must have either 2 buckets or a multiple of 2 buckets (2, 4, 6, and so on). If the preceding condition is satisfied then the joining can be done at the mapper side only, otherwise a normal inner join is performed. This means that only the required buckets are fetched on the mapper side and not the complete table. That is, only the matching buckets of all small tables are replicated onto each mapper. Doing this, the efficiency of the query is improved drastically. In a bucket map join, data is not sorted.

# SMBM Join:
Join is done in Mapper only. The corresponding buckets are joined with each other at the mapper.
- Used When all tables are:
1.Large.
2.Bucketed using the join columns.
3.Sorted using the join columns.
4.All tables have the same number of buckets.


