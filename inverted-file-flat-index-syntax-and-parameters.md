[Previous](understand-inverted-file-flat-vector-indexes.md)
[Next](guidelines-using-vector-indexes.md) JavaScript must be enabled to
correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Create Vector Indexes](create-vector-indexes.md)
  3. [Manage the Different Categories of Vector Indexes](manage-different-categories-vector-indexes.md)
  4. [Neighbor Partition Vector Index](neighbor-partition-vector-index.md)
  5. Inverted File Flat Index Syntax and Parameters

## Inverted File Flat Index Syntax and Parameters

Syntax for Inverted File Flat Index

Syntax

    
    
    CREATE VECTOR INDEX <vector index name>
    ON <table name> ( <vector column> )
    [GLOBAL] ORGANIZATION [NEIGHBOR] PARTITIONS
    [WITH] [DISTANCE <metric name>]
    [WITH TARGET ACCURACY <percentage value> 
    [PARAMETERS ( TYPE IVF, { NEIGHBOR PARTITIONS <number of partitions> | SAMPLES_PER_PARTITION
        <number of samples> | MIN_VECTORS_PER_PARTITION <minimum number of vectors per partition>
    })]]
    [PARALLEL <degree of parallelism>];

IVF Parameters

NEIGHBOR PARTITIONS determines the target number of centroid partitions that
are created by the index.

SAMPLES_PER_PARTITION decides the total number of vectors that are passed to
the clustering algorithm (samples_per_partition * neighbor_partitions).
Passing all the vectors could significantly increase the total index creation
time. The goal is to pass in a subset of vectors that can capture the data
distribution.

MIN_VECTORS_PER_PARTITION represents the target minimum number of vectors per
partition. The goal is to trim out any partition that can end up with few
vectors (<= 100).

The valid range for IVF vector index parameters are:

  * `ACCURACY`: > 0 and <= 100 
  * `DISTANCE`: `EUCLIDEAN`, `L2_SQUARED` (aka `EUCLIDEAN_SQUARED`), `COSINE`, `DOT`, `MANHATTAN`, `HAMMING`
  * `TYPE`: `IVF`
  * `NEIGHBOR PARTITIONS`: >0 and <= 10000000 
  * `SAMPLES_PER_PARTITION`: from 1 to (num_vectors/neighbor_partitions) 
  * `MIN_VECTORS_PER_PARTITION`: from 0 (no trimming of centroid partitions) to total number of vectors (would result in 1 centroid partition) 

Examples

    
    
    CREATE VECTOR INDEX galaxies_ivf_idx ON galaxies (embedding) ORGANIZATION NEIGHBOR PARTITIONS
    DISTANCE COSINE
    WITH TARGET ACCURACY 95;
    
    CREATE VECTOR INDEX galaxies_ivf_idx ON galaxies (embedding) ORGANIZATION NEIGHBOR PARTITIONS
    DISTANCE COSINE
    WITH TARGET ACCURACY 90 PARAMETERS (type IVF, neighbor partitions 10);
    

For detailed information, see [CREATE VECTOR
INDEX](/pls/topic/lookup?ctx=en/database/oracle/oracle-
database/23/vecse&id=SQLRF-GUID-B396C369-54BB-4098-A0DD-7C54B3A0D66F) in
Oracle Database SQL Language Reference .

**Parent topic:** [Neighbor Partition Vector Index](neighbor-partition-vector-
index.md "Inverted File Flat \(IVF\) index is the only type of Neighbor
Partition vector index supported. Inverted File Flat Index \(IVF Flat or
simply IVF\) is a partitioned-based index which balance high search quality
with reasonable speed.")


[← Previous](understand-inverted-file-flat-vector-indexes.md)

[Next →](guidelines-using-vector-indexes.md)
