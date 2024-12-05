[Previous](vvector_partitions_index.html) [Next](indexnamevectors.html)
JavaScript must be enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Vector Diagnostics](vector-diagnostics-node.html)
  3. [Oracle AI Vector Search Views](oracle-ai-vector-search-views.html)4. [Vector Index and Hybrid Vector Index Views](vector-index-and-hybrid-vector-index-views.html)
  5. VECSYS.VECTOR$INDEX$CHECKPOINTS

## VECSYS.VECTOR$INDEX$CHECKPOINTS

This dictionary table provides detailed information about Hierarchical
Navigable Small World (HNSW) full checkpoints at the database level.

Column Name | Data Type | Description  
---|---|---  
INDEX_OBJN | NUMBER | The index object number to uniquely identify the HNSW index.  
INDEX_OWNER_ID | NUMBER | The owner id for the vector index.  
CHECKPOINT_ID | NUMBER | A monotonically increasing ID tracking various checkpoints for this HNSW index.  
CHECKPOINT_SCN | NUMBER | The SCN as of which the HNSW checkpoint is taken.  
CHECKPOINT_TYPE | NUMBER | Full Checkpoint is the only checkpoint type supported.  
VERSION_NUMBER | NUMBER | The checkpoint format may change in between releases. Thus, you can use a version number to decide whether to reload the HNSW index using a particular checkpoint.  
TABLESPACE_NUMBER | NUMBER | The tablespace number. You can view a tablespace number to decide whether to store full checkpoints of your HNSW graphs in the same tablespace or in a different one.  
  
**Related Topics**

  * [Understand HNSW Index Population Mechanisms in Oracle RAC or Single Instance](understand-hnsw-index-population-mechanisms-oracle-rac-and-single-instance.html#GUID-8604A7A5-3C96-4B55-85BC-BCF44562BDBB "Learn how Hierarchical Navigable Small World \(HNSW\) indexes are populated during index creation, index repopulation, or instance startup in an Oracle Real Application Clusters \(Oracle RAC\) or a non-RAC environment.")

**Parent topic:** [Vector Index and Hybrid Vector Index Views](vector-index-
and-hybrid-vector-index-views.html "These views allow you to query tables
related to vector indexes and hybrid vector indexes.")


[← Previous](vvector_partitions_index.md)

[Next →](indexnamevectors.md)
