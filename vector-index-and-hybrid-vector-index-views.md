[Previous](vvector_memory_pool.html) [Next](vecsys-vectorindex.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Diagnostics](vector-diagnostics-node.html)
  3. [Oracle AI Vector Search Views](oracle-ai-vector-search-views.html)
  4. Vector Index and Hybrid Vector Index Views



## Vector Index and Hybrid Vector Index Views

These views allow you to query tables related to vector indexes and hybrid vector indexes.

  * [VECSYS.VECTOR$INDEX](vecsys-vectorindex.html)  
This dictionary table contains detailed information about vector indexes. 
  * [V$VECTOR_INDEX](vvector_index.html)  
This fixed view provides diagnostic information about vector indexes and is available with Autonomous Database Serverless (ADB-S). 
  * [V$VECTOR_GRAPH_INDEX](vvector_graph_index.html)  
This fixed view provides diagnostic information about In-Memory Neighbor Graph vector indexes and is available with Autonomous Database Serverless (ADB-S). 
  * [V$VECTOR_PARTITIONS_INDEX](vvector_partitions_index.html)  
This fixed view provides diagnostic information about Inverted File Flat indexes and is available with Autonomous Database Serverless (ADB-S). 
  * [VECSYS.VECTOR$INDEX$CHECKPOINTS](vecsys-vectorindexcheckpoints.html)  
This dictionary table provides detailed information about Hierarchical Navigable Small World (HNSW) full checkpoints at the database level. 
  * [<index name>$VECTORS](indexnamevectors.html)  
This dictionary table provides information about the vector index part of a hybrid vector index, showing the contents of the `$VR` table with row ids, chunks, and embeddings. 



**Parent topic:** [Oracle AI Vector Search Views](oracle-ai-vector-search-views.html "These are a set of data dictionary views related to Oracle AI Vector Search.")

[← Previous](vvector_memory_pool.md)

[Next →](vecsys-vectorindex.md)
