[Previous](optimizer-plans-hnsw-vector-indexes.md) [Next](approximate-
similarity-search-examples.md) JavaScript must be enabled to correctly
display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Query Data with Similarity Searches](query-data-similarity-and-hybrid-searches.md)
  3. [Perform Approximate Similarity Search Using Vector Indexes](perform-approximate-similarity-search-using-vector-indexes.md)
  4. [Optimizer Plans for Vector Indexes](optimizer-plans-vector-indexes.md)
  5. Optimizer Plans for IVF Vector Indexes

## Optimizer Plans for IVF Vector Indexes

Inverted File Flat (IVF) is a form of Neighbor Partition Vector index. It is a
partition-based index that achieves search efficiency by narrowing the search
area through the use of neighbor partitions or clusters.

Consider the following query:

    
    
    SELECT chunk_id, chunk_data,
    FROM doc_chunks
    WHERE doc_id=1
    ORDER BY VECTOR_DISTANCE( chunk_embedding, :query_vector, COSINE )
    FETCH APPROX FIRST 4 ROWS ONLY WITH TARGET ACCURACY 80;

The preceding query can lead to the following execution plan:

  * Plan line ids 5 to 9: This part happens first. The optimizer chooses the centroid `ids` that are closest to the query vector. 
  * Plan line ids 10 to 13: With these lines, the base table is joined to the identified centroid partitions. The base table is scanned to look for all the rows that pass the `WHERE` clause filter. 
  * Plan line id 4: Once both sets are identified, the rows are joined to extract only the relevant ones.
  * Plan line id 3: This step extracts the top-K rows.

    
    
    -------------------------------------------------------------------------------------------------------------------
    | Id  | Operation                               | Name                                                            |
    -------------------------------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT                        |                                                                 |
    |*  1 |  COUNT STOPKEY                          |                                                                 |
    |   2 |   VIEW                                  |                                                                 |
    |*  3 |    SORT ORDER BY STOPKEY                |                                                                 |
    |*  4 |     HASH JOIN                           |                                                                 |
    |   5 |      VIEW                               | VW_IVCR_2D77159E                                                |
    |*  6 |       COUNT STOPKEY                     |                                                                 |
    |   7 |        VIEW                             | VW_IVCN_9A1D2119                                                |
    |*  8 |         SORT ORDER BY STOPKEY           |                                                                 |
    |   9 |          TABLE ACCESS FULL              | VECTOR$DOCS_IVF_IDX2$81357_82648_0$IVF_FLAT_CENTROIDS           |
    |  10 |      NESTED LOOPS                       |                                                                 |
    |* 11 |       TABLE ACCESS FULL                 | DOC_CHUNKS                                                      |
    |  12 |       TABLE ACCESS BY GLOBAL INDEX ROWID| VECTOR$DOCS_IVF_IDX2$81357_82648_0$IVF_FLAT_CENTROID_PARTITIONS |
    |* 13 |        INDEX UNIQUE SCAN                | SYS_C008661                                                     |
    -------------------------------------------------------------------------------------------------------------------
    

IVF Indexes in the Optimizer Plan

If the IVF index is used by the optimizer, the plan contains the names of the
centroids and centroid partitions tables accessed as well as corresponding
indexes.

The value displayed in the `Options` column for tables accessed via IVF
indexes depends upon whether the table scan is for a regular table or Exadata
table.

Table 8-2 Centroids and Centroid Partition Table Options

Operation | Options | Object_name  
---|---|---  
TABLE ACCESS | FULL |  `VECTOR$<vector-index-name>$<id>$IVF_FLAT_CENTROIDS` `VECTOR$DOCS_IVF_IDX2$<id>$IVF_FLAT_CENTROID_PARTITIONS`  
TABLE ACCESS | STORAGE FULL |  `VECTOR$<vector-index-name>$<id>$IVF_FLAT_CENTROIDS` `VECTOR$DOCS_IVF_IDX2$<id>$IVF_FLAT_CENTROID_PARTITIONS`  
  
**Parent topic:** [Optimizer Plans for Vector Indexes](optimizer-plans-vector-
indexes.md "Optimizer plans for HNSW and IVF indexes are described in the
following sections.")


[← Previous](optimizer-plans-hnsw-vector-indexes.md)

[Next →](approximate-similarity-search-examples.md)
