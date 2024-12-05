[Previous](cosine_distance.html) [Next](hamming_distance-vecse.html)
JavaScript must be enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.html)
  3. [Vector Distance Functions and Operators](vector-distance-functions-and-operators.html)
  4. INNER_PRODUCT

## INNER_PRODUCT

`INNER_PRODUCT` calculates the inner product of two vectors. It takes two
vectors as input and returns the inner product as a `BINARY_DOUBLE`.
`INNER_PRODUCT(<expr1>, <expr2>)` is equivalent to `-1 *
VECTOR_DISTANCE(<expr1>, <expr2>, DOT)`.

Syntax

  

![Description of inner_product.eps
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/inner_product.gif)[Description of the illustration
inner_product.eps](https://docs.oracle.com/en/database/oracle/oracle-
database/23/vecse/img_text/inner_product.html)

  

Parameters

  * `expr1` and `expr2` must evaluate to vectors that have the same format and number of dimensions. 

  * `INNER_PRODUCT` returns NULL, if either `expr1` or `expr2` is NULL. 

**Parent topic:** [Vector Distance Functions and Operators](vector-distance-
functions-and-operators.html "A vector distance function takes in two vector
operands and a distance metric to compute a mathematical distance between
those two vectors, based on the distance metric provided. You can optionally
use shorthand distance functions and operators instead of their corresponding
distance functions.")


[← Previous](cosine_distance.md)

[Next →](hamming_distance-vecse.md)
