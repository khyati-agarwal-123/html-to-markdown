[Previous](vector-distance-metrics.md) [Next](cosine-similarity.md)
JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.md)
  3. [Vector Distance Functions and Operators](vector-distance-functions-and-operators.md)
  4. [Vector Distance Metrics](vector-distance-metrics.md)
  5. Euclidean and Euclidean Squared Distances

## Euclidean and Euclidean Squared Distances

Euclidean distance reflects the distance between each of the vectors'
coordinates being comparedâbasically the straight-line distance between two
vectors. This is calculated using the Pythagorean theorem applied to the
vector's coordinates `(SQRT(SUM((xi-yi)2)))`.

This metric is sensitive to both the vector's size and it's direction.

With Euclidean distances, comparing squared distances is equivalent to
comparing distances. So, when ordering is more important than the distance
values themselves, the Squared Euclidean distance is very useful as it is
faster to calculate than the Euclidean distance (avoiding the square-root
calculation).

  

![Description of euclidian_similarity.png
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/euclidian_similarity.png)  
[Description of the illustration
euclidian_similarity.png](img_text/euclidian_similarity.md)

  

**Parent topic:** [Vector Distance Metrics](vector-distance-metrics.md
"Measuring distances in a vector space is at the heart of identifying the most
relevant results for a given query vector. That process is very different from
the well-known keyword filtering in the relational database world.")


[← Previous](vector-distance-metrics.md)

[Next →](cosine-similarity.md)
