[Previous](manhattan-distance.html) [Next](jaccard-similarity.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.html)
  3. [Vector Distance Functions and Operators](vector-distance-functions-and-operators.html)4. [Vector Distance Metrics](vector-distance-metrics.html)
  5. Hamming Distance



## Hamming Distance

The Hamming distance between two vectors represents the number of dimensions where they differ.

For example, when using binary vectors, the Hamming distance between two vectors is the number of bits you must change to change one vector into the other. To compute the Hamming distance between two vectors A and B, you need to: 

  * Compare the position of each bit in the sequence. You do this by using an `exclusive or` (also called the XOR bit operation) between A and B. This operation outputs 1 if the bits in the sequence do not match, and 0 otherwise. 
  * Count the number of '1's in the resulting vector, the outcome of which is called the Hamming weight or norm of that vector.



It's important to note that the bit strings need to be of equal length for the comparison to make sense. The Hamming metric is mainly used with binary vectors for error detection over networks.

  


![Description of hamming_similarity2.png follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/hamming_similarity2.png)[Descriptionof the illustration hamming_similarity2.png](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img_text/hamming_similarity2.html)**Parent topic:** [Vector Distance Metrics](vector-distance-metrics.html "Measuring distances in a vector space is at the heart of identifying the most relevant results for a given query vector. That process is very different from the well-known keyword filtering in the relational database world.")

[← Previous](manhattan-distance.md)

[Next →](jaccard-similarity.md)
