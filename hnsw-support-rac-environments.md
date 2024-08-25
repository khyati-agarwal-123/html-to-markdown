[Previous](hierarchical-navigable-small-world-index-syntax-and-
parameters.md) [Next](neighbor-partition-vector-index.md) JavaScript must
be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Create Vector Indexes](create-vector-indexes.md)
  3. [Manage the Different Categories of Vector Indexes](manage-different-categories-vector-indexes.md)
  4. [In-Memory Neighbor Graph Vector Index](memory-neighbor-graph-vector-index.md)
  5. HNSW Support in RAC Environments

## HNSW Support in RAC Environments

In a RAC environment using Autonomous Database Serverless (ADB-S) services, it
is possible to use Hierarchical Navigable Small World (HNSW) indexes with
`SELECT` statements to run approximate similarity searches.

Note:

Currently only supported with Autonomous Database.

The RAC instance that creates the HNSW index is responsible for creating the
HNSW ROWID-to-VID mapping table on the disk. This table is needed by the
optimizer to solve approximate similarity searches using the HNSW index. For
more information, see [Optimizer Plans for HNSW Vector Indexes](optimizer-
plans-hnsw-vector-indexes.md#GUID-7D6B60D4-5A0C-4E9F-963E-81E244F2847A "A
Hierarchical Navigable Small World Graph \(HNSW\) is a form of In-Memory
Neighbor Graph vector index. It is a very efficient index for vector
approximate similarity search.").

Once created, all RAC instances start the HNSW In-Memory Graph creation
concurrently by duplicating all the vectors found in the HNSW ROW-to-VID
mapping table on disk. The building mechanism uses the HNSW background reload
framework, which is enabled by the `VECTOR_INDEX_NEIGHBOR_GRAPH_RELOAD`
initialization parameter set to `RESTART` (default value).

Note:

DML statements on tables with HNSW indexes are not supported.

Figure 6-6 HNSW Support in RAC Environments

  

![Description of Figure 6-6
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/hnsw-support-rac-environments.png)  
[Description of "Figure 6-6 HNSW Support in RAC Environments"](img_text/hnsw-
support-rac-environments.md)

  

Note:

Although each RAC instance shares the same ROWID-to-VID mapping table, each
instance may end up with a different HNSW In-Memory Graph meaning it's
possible to get different results depending on which RAC instance the query
lands on.

Note:

Instances that don't have the In-Memory HNSW Graph cannot participate in a
parallel RAC-wide HNSW index plan.

**Parent topic:** [In-Memory Neighbor Graph Vector Index](memory-neighbor-
graph-vector-index.md "Hierarchical Navigable Small World \(HNSW\) is the
only type of In-Memory Neighbor Graph vector index supported. HNSW graphs are
very efficient indexes for vector approximate similarity search. HNSW graphs
are structured using principles from small world networks along with layered
hierarchical organization.")


[← Previous](hierarchical-navigable-small-world-index-syntax-and-parameters.md)

[Next →](neighbor-partition-vector-index.md)
