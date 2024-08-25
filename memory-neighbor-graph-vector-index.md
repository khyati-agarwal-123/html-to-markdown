[Previous](manage-different-categories-vector-indexes.md) [Next](understand-
hierarchical-navigable-small-world-indexes.md) JavaScript must be enabled to
correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Create Vector Indexes](create-vector-indexes.md)
  3. [Manage the Different Categories of Vector Indexes](manage-different-categories-vector-indexes.md)
  4. In-Memory Neighbor Graph Vector Index

## In-Memory Neighbor Graph Vector Index

Hierarchical Navigable Small World (HNSW) is the only type of In-Memory
Neighbor Graph vector index supported. HNSW graphs are very efficient indexes
for vector approximate similarity search. HNSW graphs are structured using
principles from small world networks along with layered hierarchical
organization.

  * [Understand Hierarchical Navigable Small World Indexes](understand-hierarchical-navigable-small-world-indexes.md)  
The default type of index created for an In-Memory Neighbor Graph vector index
is Hierarchical Navigable Small World (HNSW). Use these examples to understand
how to create HNSW indexes for vector approximate similarity searches.

  * [Hierarchical Navigable Small World Index Syntax and Parameters](hierarchical-navigable-small-world-index-syntax-and-parameters.md)  
Syntax for Hierarchical Navigable Small World Index

  * [HNSW Support in RAC Environments](hnsw-support-rac-environments.md)  
In a RAC environment using Autonomous Database Serverless (ADB-S) services, it
is possible to use Hierarchical Navigable Small World (HNSW) indexes with
`SELECT` statements to run approximate similarity searches.

**Parent topic:** [Manage the Different Categories of Vector Indexes](manage-
different-categories-vector-indexes.md "Learn how vector indexing methods
make vector searches faster and how to enable vector indexes creation.")


[← Previous](manage-different-categories-vector-indexes.md)

[Next →](understand-hierarchical-navigable-small-world-indexes.md)
