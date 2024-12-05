[Previous](enable_checkpoint.html) [Next](index_accuracy_query.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR](dbms_vector-vecse.html)
  4. GET_INDEX_STATUS



## GET_INDEX_STATUS

Use the `GET_INDEX_STATUS` procedure to query the status of a vector index creation. 

Syntax
    
    
    DBMS_VECTOR.GET_INDEX_STATUS ('USER_NAME','INDEX_NAME');

USER_NAME

Specify the user name of the vector index owner.

INDEX_NAME

Specify the name of the vector index. You can query the index creation status for both Hierarchical Navigable Small World (HNSW) indexes and Inverted File Flat (IVF) indexes.

Usage Notes

  * You can use the `GET_INDEX_STATUS` procedure only during a vector index creation. 

  * The `Percentage` value is shown in the output only for Hierarchical Navigable Small World (HNSW) indexes (and not for Inverted File Flat (IVF) indexes). 

  * Along with the `DB_DEVELOPER_ROLE` privilege, you must have read access to the `VECSYS.VECTOR$INDEX$BUILD$` table. 

  * You can use the following query to view all auxiliary tables: 
    
        select IDX_AUXILIARY_TABLES from vecsys.vector$index;

    * For HNSW indexes: 

`rowid_vid_map` stores the mapping between a row ID and vector ID. `shared_journal_change_log` stores the DML changes that are yet to be incorporated into an HNSW graph. 

    * For IVF indexes: 

`centroids` stores the location for each centroid. `centroid_partitions` stores the best centroid for each vector. 

  * The possible values of `Stage` for HNSW vector indexes are: 

Value | Description  
---|---  
HNSW Index Initialization | Initialization phase for the HNSW vector index creation  
HNSW Index Auxiliary Tables Creation | Creation of the internal auxiliary tables for the HNSW Neighbor Graph vector index  
HNSW Index Graph Allocation | Allocation of memory from the vector memory pool for the HNSW graph  
HNSW Index Loading Vectors | Loading of the base table vectors into the vector pool memory  
HNSW Index Graph Construction | Creation of the multi-layered HNSW graph with the previously loaded vectors  
HNSW Index Creation Completed | HNSW vector index creation finished  
  
  * The possible values of `Stage` for IVF vector indexes are: 

Value | Description  
---|---  
IVF Index Initialization | Initialization phase for the IVF vector index creation  
IVF Index Centroids Creation | The K-means clustering phase that computes the cluster centroids on a sample of base table vectors  
IVF Index Centroid Partitions Creation | Centroids assignment phase for the base table vectors  
IVF Index Creation Completed | IVF vector index creation completed  
  



Example
    
    
    exec DBMS_VECTOR.GET_INDEX_STATUS('VECTOR_USER','VIDX_HNSW');
    
    Index objn: 74745 
    Stage: HNSW Index Loading Vectors 
    Percentage: 80%

**Parent topic:** [DBMS_VECTOR](dbms_vector-vecse.html "The DBMS_VECTOR package simplifies common operations with Oracle AI Vector Search, such as extracting chunks or embeddings from user data, generating text for a given prompt or an image, creating a vector index, or reporting on index accuracy.")

[← Previous](enable_checkpoint.md)

[Next →](index_accuracy_query.md)
