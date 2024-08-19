[Previous](oracle-machine-learning-static-dictionary-views.md)
[Next](vector-search-pl-sql-packages-node.md) JavaScript must be enabled to
correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Vector Diagnostics](vector-diagnostics-node.md)
  3. Oracle AI Vector Search Parameters

## Oracle AI Vector Search Parameters

This is a set of parameters related to Oracle AI Vector Search.

  * `VECTOR_MEMORY_SIZE`

Syntax: `vector_memory_size = [ON | OFF]` (default `ON`) 

The initialization parameter `VECTOR_MEMORY_SIZE` specifies either the current
size of the Vector Pool (at CDB level) or the maximum Vector Pool usage
allowed by a PDB (at PDB level). The possible For more information about this
parameter, see [Size the Vector Pool](size-vector-
pool.md#GUID-1815E227-56C9-4E62-977F-0FDA282C9D83 "To allow vector index
creation, you must enable a new memory area stored in the SGA called the
Vector Pool.").

  * `VECTOR_INDEX_NEIGHBOR_GRAPH_RELOAD`

Syntax: `vector_index_neighbor_graph_reload = [RESTART | OFF]` (default `OFF`) 

The initialization parameter `VECTOR_INDEX_NEIGHBOR_GRAPH_RELOAD`
automatically loads HNSW indexes one by one after instance restart through a
background task. For more information about this parameter, see [Guidelines
for Using Vector Indexes](guidelines-using-vector-
indexes.md#GUID-F77D534C-2467-47A7-A5A0-70AE0957213A "Use these guidelines
to create and use Hierarchical Navigable Small World \(HNSW\) or Inverted File
Flat \(IVF\) vector indexes.").

  * `VECTOR_QUERY_CAPTURE`

Syntax: `vector_query_capture = [ON | OFF]` (default `ON`) 

The initialization parameter `VECTOR_QUERY_CAPTURE` is used to enable and
disable capture of query vectors. For more information about this parameter
and about capturing query vectors, see [Index Accuracy Report](index-accuracy-
report.md#GUID-A084929C-7A04-4764-9E5B-1204E0844CAF "The index accuracy
reporting feature lets you determine the accuracy of your vector indexes.").

**Parent topic:** [Vector Diagnostics](vector-diagnostics-node.md "AI Vector
Search includes several views, statistics, and parameters that can be used to
help understand how vector search is performing for your workload.")


[← Previous](oracle-machine-learning-static-dictionary-views.md)

[Next →](vector-search-pl-sql-packages-node.md)
