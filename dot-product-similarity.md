[Previous](cosine-similarity.md) [Next](manhattan-distance.md) JavaScript
must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.md)
  3. [Vector Distance Functions and Operators](vector-distance-functions-and-operators.md)
  4. [Vector Distance Metrics](vector-distance-metrics.md)
  5. Dot Product Similarity

## Dot Product Similarity

The dot product similarity of two vectors can be viewed as multiplying the
size of each vector by the cosine of their angle. The corresponding
geometrical interpretation of this definition is equivalent to multiplying the
size of one of the vectors by the size of the projection of the second vector
onto the first one, or vice versa.

As illustrated in the following diagram, you project one vector on the other
and multiply the resulting vector sizes.

Incidentally, this is equivalent to the sum of the products of each vector's
coordinate. Often, you do not have access to the cosine of the two vector's
angle, hence this calculation is easier.

Larger dot product values imply that the vectors are more similar, while
smaller values imply that they are less similar. Compared to using Euclidean
distance, using the dot product similarity is especially useful for high-
dimensional vectors.

Note that normalizing vectors and using the dot product similarity is
equivalent to using cosine similarity. There are cases where dot product
similarity is faster to evaluate than cosine similarity, and conversely where
cosine similarity is faster than dot product similarity. A normalized vector
is created by dividing each dimension by the norm (or length) of the vector,
such that the norm of the normalized vector is equal to 1.

  

![Description of dot_product_similarity2.eps
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/dot_product_similarity2.png)  
[Description of the illustration
dot_product_similarity2.eps](img_text/dot_product_similarity2.md)

  

**Parent topic:** [Vector Distance Metrics](vector-distance-metrics.md
"Measuring distances in a vector space is at the heart of identifying the most
relevant results for a given query vector. That process is very different from
the well-known keyword filtering in the relational database world.")


[← Previous](cosine-similarity.md)

[Next →](manhattan-distance.md)
