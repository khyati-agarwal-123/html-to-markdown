[Previous](understand-approximate-similarity-search-using-vector-indexes.html)[Next](optimizer-plans-hnsw-vector-indexes.html) JavaScript must be enabled to
correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Query Data With Similarity and Hybrid Searches](query-data-similarity-and-hybrid-searches.html)
  3. [Perform Approximate Similarity Search Using Vector Indexes](perform-approximate-similarity-search-using-vector-indexes.html)
  4. Optimizer Plans for Vector Indexes

## Optimizer Plans for Vector Indexes

Optimizer plans for HNSW and IVF indexes are described in the following
sections.

  * [Optimizer Plans for HNSW Vector Indexes](optimizer-plans-hnsw-vector-indexes.html)  
A Hierarchical Navigable Small World Graph (HNSW) is a form of In-Memory
Neighbor Graph vector index. It is a very efficient index for vector
approximate similarity search.

  * [Optimizer Plans for IVF Vector Indexes](optimizer-plans-ivf-vector-indexes.html)  
Inverted File Flat (IVF) is a form of Neighbor Partition Vector index. It is a
partition-based index that achieves search efficiency by narrowing the search
area through the use of neighbor partitions or clusters.

  * [Vector Index Hints](vector-index-hints.html)  
If the optimizer does not choose your existing index while running your query
and you still want that index to be used, you can rewrite your SQL statement
to include vector index hints.

**Parent topic:** [Perform Approximate Similarity Search Using Vector
Indexes](perform-approximate-similarity-search-using-vector-indexes.html "For
a vector search to be useful, it needs to be fast and accurate. Approximate
similarity searches seek a balance between these goals.")


[← Previous](understand-approximate-similarity-search-using-vector-indexes.md)

[Next →](optimizer-plans-hnsw-vector-indexes.md)
