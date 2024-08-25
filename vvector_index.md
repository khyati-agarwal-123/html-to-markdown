[Previous](vecsys-vectorindex.md) [Next](vvector_graph_index.md)
JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Vector Diagnostics](vector-diagnostics-node.md)
  3. [Oracle AI Vector Search Views](oracle-ai-vector-search-views.md)
  4. [Vector Index Views](vector-index-views.md)
  5. V$VECTOR_INDEX

## V$VECTOR_INDEX

This fixed view provides diagnostic information about vector indexes and is
available with Autonomous Database Serverless (ADB-S).

Column Name | Data Type | Description  
---|---|---  
`OWNER` |  `VARCHAR(129)` |  User name of the vector index owner  
`INDEX_NAME` |  `VARCHAR(129)` |  Name of the vector index  
`PARTITION_NAME` |  `VARCHAR(129)` |  Object partition name (set to `NULL` for non-partitioned objects)   
`INDEX_ORGANIZATION` |  `VARCHAR(129)` |  The vector index organization. The value can be one of the following: 

  * `NEIGHBOR PARTITIONS`
  * `INMEMORY NEIGHBOR GRAPH`

  
`INDEX_OBJN` |  `NUMBER` |  Index object number  
`ALLOCATED_BYTES` |  `NUMBER` |  Total amount of memory allocated to this vector index, in bytes. When the vector index is an IVF index, the value is `0`.   
`USED_BYTES` |  `NUMBER` |  Total amount of memory currently used by the vector index, in bytes. When the vector index is an IVF index, the value is `0`.   
`NUM_VECTORS` |  `NUMBER` |  The number of vectors currently indexed in the main-memory storage of the index as of the latest snapshot  
`NUM_REPOP` |  `NUMBER` |  Number of times this index has been repopulated  
`INDEX_USED_COUNT` |  `NUMBER` |  Number of times this vector index has been used by queries  
`DISTANCE_TYPE` |  `VARCHAR2(129)` |  Possible distance values: 

  * `EUCLIDEAN`
  * `EUCLIDEAN_SQUARED`
  * `COSINE`
  * `DOT`
  * `MANHATTAN`
  * `HAMMING`

  
`INDEX_DIMENSIONS` |  `NUMBER` |  Number of dimensions of the indexed vector  
`INDEX_DIM_TYPE` |  `VARCHAR2(129)` |  Type of the dimensions of the index vector. Possible values: 

  * `FLOAT16`
  * `FLOAT32`
  * `FLOAT64`
  * `INT8`

  
`DEFAULT_ACCURACY` |  `NUMBER` |  The accuracy to achieve when performing approximate search on this vector index if a target query accuracy is not provided  
`CON_ID` |  `NUMBER` |  The ID of the container to which the data pertains. Possible values include the following: 

  * `0`: This value is used for rows containing data that pertain to the entire multitenant container database (CDB). This value is also used for rows in non-CDBs. 
  * `1`: This value is used for rows containing data that pertain to only the root. 
  * `n`: Where `n` is the applicable container ID for the rows containing data. 

  
  
**Parent topic:** [Vector Index Views](vector-index-views.md "Review the
vector index views.")


[← Previous](vecsys-vectorindex.md)

[Next →](vvector_graph_index.md)
