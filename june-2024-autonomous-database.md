[Previous](whats-new-oracle-ai-vector-search.md) [Next](july-2024-oracle-
database-23ai-release-update-23.5.md) JavaScript must be enabled to
correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [What's New for Oracle AI Vector Search](whats-new-oracle-ai-vector-search.md)
  3. June 2024 Autonomous Database

## June 2024 Autonomous Database

Included are some notable Oracle AI Vector Search updates with the Autonomous
Database, June 2024 release.

Feature | Description  
---|---  
HNSW Index Support in RAC Environments |  It is possible to use Hierarchical Navigable Small World (HNSW) indexes with `SELECT` statements in RAC environments. For more information, see [HNSW Support in RAC Environments](hnsw-support-rac-environments.md#GUID-50EC36FA-94A1-41BE-9BB3-15B43408BECC "In a RAC environment using Autonomous Database Serverless \(ADB-S\) services, it is possible to use Hierarchical Navigable Small World \(HNSW\) indexes with SELECT statements to run approximate similarity searches.").   
Sizing the Vector Pool with ADB-S |  With Autonomous Database Serverless (ADB-S) services, the vector pool dynamically grows and shrinks. It cannot be explicitly set. For more information, see [Size the Vector Pool](size-vector-pool.md#GUID-1815E227-56C9-4E62-977F-0FDA282C9D83 "To allow vector index creation, you must enable a new memory area stored in the SGA called the Vector Pool.").   
SQL Quick Start with Vector Generator |  A SQL scenario is provided to get you started using Oracle AI Vector Search. The quick start includes a PL/SQL program that creates a vector generator, offering a simple alternative to using a vector embedding model. For the full tutorial, see [SQL Quick Start Using a FLOAT32 Vector Generator](sql-quick-start-using-float32-vector-generator.md#GUID-1AA9AA2B-F3A6-481B-9EE3-8B08A4CE200D "A PL/SQL program that creates a vector generator is included along with example queries and results, providing a simple way to get started with Oracle AI Vector Search without a vector embedding model.").   
Similarity Search and Index Creation Syntax | 

  * The `APPROX` and `APPROXIMATE` keywords are now optional. If omitted while connected to an ADB-S instance, an approximate search using a vector index is attempted if one exists.  For more information about approximate search with indexes, see [Approximate Search Using HNSW](approximate-search-using-hnsw.md#GUID-3D072E54-00AC-4C73-AECF-2B9113A58F4A "This example shows how you can create the Hierarchical Navigable Small World \(HNSW\) index and run an approximate search using that index.") and [Approximate Search Using IVF](approximate-search-using-ivf.md#GUID-AB45B8A4-26D2-49CC-B807-C1B009B6644B "This example shows how you can create the Inverted File Flat \(IVF\) index and run an approximate search using that index."). 
  * The `NEIGHBOR` keyword in the `ORGANIZATION` clause of `CREATE VECTOR INDEX` is now optional.  For the full syntax to create HNSW and IVF indexes, see [Hierarchical Navigable Small World Index Syntax and Parameters](hierarchical-navigable-small-world-index-syntax-and-parameters.md#GUID-0D538811-D59F-46FB-9453-1A6BD822EEED "Syntax for Hierarchical Navigable Small World Index") and [Inverted File Flat Index Syntax and Parameters](inverted-file-flat-index-syntax-and-parameters.md#GUID-FC314C40-1018-46B9-9F1C-660BBE28FBE9 "Syntax for Inverted File Flat Index"). 

  
  
**Parent topic:** [What's New for Oracle AI Vector Search](whats-new-oracle-
ai-vector-search.md)


[← Previous](whats-new-oracle-ai-vector-search.md)

[Next →](july-2024-oracle-database-23ai-release-update-23.5.md)
