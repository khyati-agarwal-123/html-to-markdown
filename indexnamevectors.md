[Previous](vecsys-vectorindexcheckpoints.html) [Next](oracle-ai-vector-search-statistics.html) JavaScript must be enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Vector Diagnostics](vector-diagnostics-node.html)
  3. [Oracle AI Vector Search Views](oracle-ai-vector-search-views.html)4. [Vector Index and Hybrid Vector Index Views](vector-index-and-hybrid-vector-index-views.html)
  5. <index name>$VECTORS

## <index name>$VECTORS

This dictionary table provides information about the vector index part of a
hybrid vector index, showing the contents of the `$VR` table with row ids,
chunks, and embeddings.

Note:

The `<index name>$VECTORS` view resides in a user's schema. Therefore, if a
hybrid vector index is named `IDX`, then the view name is `IDX$VECTORS`.

Column Name | Data Type | Description  
---|---|---  
DOC_ROWID | ROWID | Document table's row ID, excluding lazy deletes  
DOC_CHUNK_ID | NUMBER | ID for each chunk text  
DOC_CHUNK_COUNT | NUMBER | Number of chunks into which each document is split  
DOC_CHUNK_OFFSET | NUMBER | Original position of each chunk in the source document, relative to the start of document (which has a position of 1)  
DOC_CHUNK_LENGTH | NUMBER | Character length of each chunk text  
DOC_CHUNK_TEXT | VARCHAR2(4000) | Human-readable content in each chunk  
DOC_CHUNK_EMBEDDING | VECTOR(*, *) | Generated vector embedding for each chunk  
  
**Related Topics**

  * [Manage Hybrid Vector Indexes](manage-hybrid-vector-indexes.html#GUID-F2493927-23F8-4231-862B-6EDFA5A12299 "Learn how to manage a hybrid vector index, which is a single index for searching by similarity and keywords, to enhance the accuracy of your search results.")

**Parent topic:** [Vector Index and Hybrid Vector Index Views](vector-index-
and-hybrid-vector-index-views.html "These views allow you to query tables
related to vector indexes and hybrid vector indexes.")


[← Previous](vecsys-vectorindexcheckpoints.md)

[Next →](oracle-ai-vector-search-statistics.md)
