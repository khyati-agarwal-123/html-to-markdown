[Previous](inverted-file-flat-index-syntax-and-parameters.md) [Next](index-
accuracy-report.md) JavaScript must be enabled to correctly display this
content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Create Vector Indexes](create-vector-indexes.md)
  3. [Manage the Different Categories of Vector Indexes](manage-different-categories-vector-indexes.md)
  4. Guidelines for Using Vector Indexes

## Guidelines for Using Vector Indexes

Use these guidelines to create and use Hierarchical Navigable Small World
(HNSW) or Inverted File Flat (IVF) vector indexes.

Create Index Guidelines

The minimum information required to create a vector index is to specify one
VECTOR data type table column and a vector index type: `INMEMORY NEIGHBOR
GRAPH` for HNSW and `NEIGHBOR PARTITIONS` for IVF. However, you also have the
possibility to specify more information, such as the following:

  * You can optionally provide more information including the distance metric to use. Supported metrics are `EUCLIDEAN SQUARED`, `EUCLIDEAN`, `COSINE`, `DOT`, `MANHATTAN`, and `HAMMING`. If not specified, `COSINE` is used by default. 
  * Specific parameters that impact the accuracy of index creation and approximate searches. A target accuracy percentage value and, `NEIGHBORS` (or M) and `EFCONSTRUCTION` for HNSW and `NEIGHBOR PARTITIONS` for IVF. 
  * You can create globally partitioned vector indexes.
  * You can also specify the degree of parallelism to use for index creation.

You cannot currently define a VECTOR index on:

  * External tables
  * IOTs
  * Clusters/Cluster tables
  * Global Temp tables
  * Blockchain tables
  * Materialized views
  * Non-vector columns (`VARCHAR`, `NUMBER`, and so on.) 
  * Function-based vector index
  * Sharded tables

You can find information about your vector indexes by looking at
`ALL_INDEXES`, `DBA_INDEXES`, and `USER_INDEXES` family of views. The columns
of interest are `INDEX_TYPE` (`VECTOR`) and `INDEX_SUBTYPE`
(`INMEMORY_NEIGHBOR_GRAPH_HNSW` or `NEIGHBOR_PARTITIONS_IVF`). In the case the
index is not a vector index, `INDEX_SUBTYPE` is `NULL`.

See [VECSYS.VECTOR$INDEX](vecsys-vectorindex.md#GUID-
FA5183EA-3C60-470D-9C91-8215BE4FF138 "This dictionary table contains detailed
information about vector indexes.") for detailed information about vector
indexes.

Note:

  * The `VECTOR` column is designed to be extremely flexible to support vectors of any number of dimensions and any format for the vector dimensions. However, you can create a vector index only on a `VECTOR` column containing vectors that all have the same number of dimensions. This is required as you can't compute distances over vectors with different dimensions. For example, if a `VECTOR` column is defined as `VECTOR(*, FLOAT32)`, and two vectors with different dimensions (128 and 256 respectively) are inserted in that column. When you try to create the vector index on that column, you will get an error. 
  * You can only create one type of vector index per vector column.
  * Oracle recommends that you allocate larger, temporary tablespaces for proper Inverted File Flat (IVF) vector index creation with big vector spaces and vector sizes. In such cases, the system internally makes extensive use of temporary space.
  * If you are running your Oracle Database on a RAC environment, you cannot create HNSW indexes. On a non-RAC single instance environment, you can create both HNSW and IVF indexes. Using HNSW is the preferred type if it fits entirely into memory.
  * On a RAC environment you can set up a vector pool on each instance for the best performance of IVF indexes.

Use Index Guidelines

For the Oracle Database Optimizer to consider a vector index, you must ensure
to verify these conditions in your SQL statements:

  * The similarity search SQL query must include the `APPROX` or `APPROXIMATE` keyword. 
  * The vector index must exist.
  * The distance function for the index must be the same as the distance function used in the `vector_distance()` function. 
  * If the vector index DDL does not specify the distance function and the `vector_distance()` function uses `COSINE`, `DOT`, `MANHATTAN` or `HAMMING`, then the vector index is not used. 
  * If the vector index DDL uses the `DOT` distance function and the `vector_distance()` function uses the default distance function `[COSINE]`, then the vector index is not used. 
  * The `vector_distance()` must not be encased in another SQL function. 
  * If using the partition row-limiting clause, then the vector index is not used.
  * Index accuracy with an IVF index may diminish over time due to DML operations being performed on the underlying table. You can check for this by using the `INDEX_ACCURACY_QUERY` function provided by the `DBMS_VECTOR` package. In such a case, the index can be rebuild using the `REBUILD_INDEX` function also provided by the `DBMS_VECTOR` package. See [Oracle Database PL/SQL Packages and Types Reference](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-111D54BC-B2E5-4134-BBE0-ACE0F121B991) for more information about `DBMS_VECTOR` and its subprograms. 
  * After an HNSW vector index is created, DML operations are not permitted on the indexed table. DML operations are supported when using IVF indexes.

Note:

When the database instance is restarted, the existing HNSW indexes must be
rebuilt as these structures are inmemory-only structures. There are three
options for you to recreate an HNSW vector index after a restart:

  * Manually drop the index and create it again. This requires you to remember and provide the original index creation parameters.
  * `DBMS_VECTOR.REBUILD_INDEX`: This procedure uses the `DBMS_METADATA.GET_DDL` function to get all of the index creation parameters. You may override the parameters by passing their values into the procedure. For more information about the `DBMS_VECTOR.REBUILD` procedure, see [Oracle Database PL/SQL Packages and Types Reference](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-7A7B63F6-97E3-44C6-8CD4-C84376F06F14). 
  * Automatic reload: The `VECTOR_INDEX_NEIGHBOR_GRAPH_RELOAD` initialization parameter is set to `OFF` by default. If set to `RESTART`, the system automatically loads the HNSW indexes one by one through a background task. It will use the same parallelism and the index creation parameters that you had specified during the original HNSW index creation. 

Note:

Except for `ALTER TABLE tab SUBPARTITION`/`PARTITION` (`RANGE`/`LIST`) with or
without Update Global Indexes, global vector indexes are marked as unusable as
part of other Partition Management Operations on a partitioned table. In those
cases you must manually rebuild the global vector indexes.

**Parent topic:** [Manage the Different Categories of Vector Indexes](manage-
different-categories-vector-indexes.md "Learn how vector indexing methods
make vector searches faster and how to enable vector indexes creation.")


[← Previous](inverted-file-flat-index-syntax-and-parameters.md)

[Next →](index-accuracy-report.md)
