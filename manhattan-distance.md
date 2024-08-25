[Previous](dot-product-similarity.md) [Next](hamming-similarity.md)
JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.md)
  3. [Vector Distance Functions and Operators](vector-distance-functions-and-operators.md)
  4. [Vector Distance Metrics](vector-distance-metrics.md)
  5. Manhattan Distance

## Manhattan Distance

This metric is calculated by summing the distance between the dimensions of
the two vectors that you want to compare.

Imagine yourself in the streets of Manhattan trying to go from point A to
point B. A straight line is not possible.

This metric is most useful for vectors describing objects on a uniform grid,
such as city blocks, power grids, or a chessboard. It can be useful for higher
dimensional vector spaces too. Compared to the Euclidean metric, the Manhattan
metric is faster for calculations and you can use it advantageously for higher
dimensional vector spaces.

  

![Description of manhattan_similarity2.png
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/manhattan_similarity2.png)  
[Description of the illustration
manhattan_similarity2.png](img_text/manhattan_similarity2.md)

  

**Parent topic:** [Vector Distance Metrics](vector-distance-metrics.md
"Measuring distances in a vector space is at the heart of identifying the most
relevant results for a given query vector. That process is very different from
the well-known keyword filtering in the relational database world.")


[← Previous](dot-product-similarity.md)

[Next →](hamming-similarity.md)
