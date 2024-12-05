[Previous](inner_product.html) [Next](jaccard_distance-vecse.html) JavaScript
must be enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.html)
  3. [Vector Distance Functions and Operators](vector-distance-functions-and-operators.html)
  4. HAMMING_DISTANCE

## HAMMING_DISTANCE

`HAMMING_DISTANCE` is a shorthand version of the `VECTOR_DISTANCE` function
that calculates the distance between two vectors. It takes two vectors as
input and returns the distance between them as a `BINARY_DOUBLE`.

Syntax

  

![Description of hamming_distance_syntax.eps
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/hamming_distance_syntax.gif)[Description of the illustration
hamming_distance_syntax.eps](https://docs.oracle.com/en/database/oracle/oracle-
database/23/vecse/img_text/hamming_distance_syntax.html)

  

Parameters

  * `expr1` and `expr2` must evaluate to vectors that have the same format and number of dimensions. 

  * `HAMMING_DISTANCE` returns NULL if either `expr1` or `expr2` is NULL. 

**Parent topic:** [Vector Distance Functions and Operators](vector-distance-
functions-and-operators.html "A vector distance function takes in two vector
operands and a distance metric to compute a mathematical distance between
those two vectors, based on the distance metric provided. You can optionally
use shorthand distance functions and operators instead of their corresponding
distance functions.")


[← Previous](inner_product.md)

[Next →](jaccard_distance-vecse.md)
