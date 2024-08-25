[Previous](manhattan-distance.md) [Next](vector_distance-vecse.md)
JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.md)
  3. [Vector Distance Functions and Operators](vector-distance-functions-and-operators.md)
  4. [Vector Distance Metrics](vector-distance-metrics.md)
  5. Hamming Similarity

## Hamming Similarity

The Hamming distance between two vectors represents the number of dimensions
where they differ.

For example, when using binary vectors, the Hamming distance between two
vectors is the number of bits you must change to change one vector into the
other. To compute the Hamming distance between two vectors, you need to
compare the position of each bit in the sequence. You can do this by using
`exclusive or` (also called the XOR bit operation), which outputs 1 if the
bits in the sequence do not match, and 0 otherwise. It's important to note
that the bit strings need to be of equal length for the comparison to make
sense.

The Hamming metric is mainly used with binary vectors for error detection over
networks.

  

![Description of hamming_similarity2.png
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/hamming_similarity2.png)  
[Description of the illustration
hamming_similarity2.png](img_text/hamming_similarity2.md)

  

**Parent topic:** [Vector Distance Metrics](vector-distance-metrics.md
"Measuring distances in a vector space is at the heart of identifying the most
relevant results for a given query vector. That process is very different from
the well-known keyword filtering in the relational database world.")


[← Previous](manhattan-distance.md)

[Next →](vector_distance-vecse.md)
