[Previous](l2_distance.html) [Next](inner_product.html) JavaScript must be
enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.html)
  3. [Vector Distance Functions and Operators](vector-distance-functions-and-operators.html)
  4. COSINE_DISTANCE

## COSINE_DISTANCE

`COSINE_DISTANCE` is a shorthand version of the `VECTOR_DISTANCE` function
that calculates the distance between two vectors. It takes two vectors as
input and returns the distance between them as a `BINARY_DOUBLE`.

Syntax

  

![Description of cosine_distance.eps
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/cosine_distance.gif)[Description of the illustration
cosine_distance.eps](https://docs.oracle.com/en/database/oracle/oracle-
database/23/vecse/img_text/cosine_distance.html)

  

Parameters

  * `expr1` and `expr2` must evaluate to vectors that have the same format and number of dimensions. 

  * `COSINE_DISTANCE` returns NULL, if either `expr1` or `expr2` is NULL. 

**Parent topic:** [Vector Distance Functions and Operators](vector-distance-
functions-and-operators.html "A vector distance function takes in two vector
operands and a distance metric to compute a mathematical distance between
those two vectors, based on the distance metric provided. You can optionally
use shorthand distance functions and operators instead of their corresponding
distance functions.")


[← Previous](l2_distance.md)

[Next →](inner_product.md)
