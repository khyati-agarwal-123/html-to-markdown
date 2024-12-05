[Previous](create_credential-dbms_vector.html) [Next](disable_checkpoint.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR](dbms_vector-vecse.html)
  4. CREATE_INDEX



## CREATE_INDEX

Use the `DBMS_VECTOR.CREATE_INDEX` procedure to create a vector index. 

Purpose

To create a vector index such as Hierarchical Navigable Small World (HNSW) vector index or Inverted File Flat (IVF) vector index.

Syntax
    
    
    DBMS_VECTOR.CREATE_INDEX (
        idx_name                    IN VARCHAR2,
        table_name                  IN VARCHAR2,
        idx_vector_col              IN VARCHAR2,
        idx_include_cols            IN VARCHAR2 DEFAULT NULL,
        idx_partitioning_scheme     IN VARCHAR2 default 'LOCAL',
        idx_organization            IN VARCHAR2,
        idx_distance_metric         IN VARCHAR2 DEFAULT COSINE,
        idx_accuracy                IN NUMBER DEFAULT 90,
        idx_parameters              IN CLOB,
        idx_parallel_creation       IN NUMBER DEFAULT 1
    );

Parameters

Parameter | Description  
---|---  
idx_name | Name of the index to create.  
table_name | Table on which to create the index.  
idx_vector_col | Vector column on which to create the index.  
idx_include_cols | This parameter is currently unused.  
idx_partitioning_scheme | Partitioning scheme for IVF indexes: GLOBAL LOCAL IVF indexes support both global and local indexes on partitioned tables. By default, these indexes are globally partitioned by centroid. You can choose to create a local IVF index, which provides a one-to-one relationship between the base table partitions or subpartitions and the index partitions. For detailed information on these partitioning schemes, see Inverted File Flat Vector Indexes Partitioning Schemes.  
idx_organization | Index organization: NEIGHBOR PARTITIONS INMEMORY NEIGHBOR GRAPH For detailed information on these organization types, see Manage the Different Categories of Vector Indexes.  
idx_distance_metric | Distance metric or mathematical function used to compute the distance between vectors: COSINE (default) MANHATTAN HAMMING JACCARD DOT EUCLIDEAN L2_SQUARED EUCLIDEAN_SQUARED For detailed information on each of these metrics, see Vector Distance Functions and Operators.  
idx_accuracy | Target accuracy at which the approximate search should be performed when running an approximate search query. As explained in Understand Approximate Similarity Search Using Vector Indexes, you can specify non-default target accuracy values either by specifying a percentage value or by specifying internal parameters values, depending on the index type you are using. For an HNSW approximate search: In the case of an HNSW approximate search, you can specify a target accuracy percentage value to influence the number of candidates considered to probe the search. This is automatically calculated by the algorithm. A value of 100 will tend to impose a similar result as an exact search, although the system may still use the index and will not perform an exact search. The optimizer may choose to still use an index as it may be faster to do so given the predicates in the query. Instead of specifying a target accuracy percentage value, you can specify the EFSEARCH parameter to impose a certain maximum number of candidates to be considered while probing the index. The higher that number, the higher the accuracy. For detailed information, see Understand Hierarchical Navigable Small World Indexes. For an IVF approximate search: In the case of an IVF approximate search, you can specify a target accuracy percentage value to influence the number of partitions used to probe the search. This is automatically calculated by the algorithm. A value of 100 will tend to impose an exact search, although the system may still use the index and will not perform an exact search. The optimizer may choose to still use an index as it may be faster to do so given the predicates in the query. Instead of specifying a target accuracy percentage value, you can specify the NEIGHBOR PARTITION PROBES parameter to impose a certain maximum number of partitions to be probed by the search. The higher that number, the higher the accuracy. For detailed information, see Understand Inverted File Flat Vector Indexes.  
idx_parameters | Type of vector index and associated parameters. Specify the indexing parameters in JSON format: For HNSW indexes: type: Type of vector index to create, that is, HNSW neighbors: Maximum number of connections permitted per vector in the HNSW graph efConstruction: Maximum number of closest vector candidates considered at each step of the search during insertion For example:{ "type" : "HNSW", "neighbors" : 3, "efConstruction" : 4 }For detailed information on these parameters, see Hierarchical Navigable Small World Index Syntax and Parameters. For IVF indexes: type: Type of vector index to create, that is, IVF partitions: Neighbor partition or cluster in which you want to divide your vector space For example:{ "type" : "IVF", "partitions" : 5 }For detailed information on these parameters, see Inverted File Flat Index Syntax and Parameters.  
idx_parallel_creation | Number of parallel threads used for index construction.  
  
Examples

  * Specify neighbors and efConstruction for HNSW indexes:
    
        dbms_vector.create_index(
        'v_hnsw_01', 
        'vpt01', 
        'EMBEDDING', 
         NULL, 
         NULL, 
        'INMEMORY NEIGHBOR GRAPH', 
        'EUCLIDEAN', 
         95, 
        '{"type" : "HNSW", "neighbors" : 3, "efConstruction" : 4}');

  * Specify the number of partitions for IVF indexes:
    
        dbms_vector.create_index(
        'V_IVF_01', 
        'vpt01', 
        'EMBEDDING', 
         NULL,
         NULL, 
        'NEIGHBOR PARTITIONS', 
        'EUCLIDEAN', 
         95, 
        '{"type" : "IVF", "partitions" : 5}');




**Parent topic:** [DBMS_VECTOR](dbms_vector-vecse.html "The DBMS_VECTOR package simplifies common operations with Oracle AI Vector Search, such as extracting chunks or embeddings from user data, generating text for a given prompt or an image, creating a vector index, or reporting on index accuracy.")

[← Previous](create_credential-dbms_vector.md)

[Next →](disable_checkpoint.md)
