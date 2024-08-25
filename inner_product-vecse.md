[Previous](cosine_distance-vecse.md) [Next](chunking-and-vector-generation-
functions.md) JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.md)
  3. [Vector Distance Functions and Operators](vector-distance-functions-and-operators.md)
  4. INNER_PRODUCT

## INNER_PRODUCT

`INNER_PRODUCT` is a shorthand version of the `VECTOR_DISTANCE` function that
calculates the distance between two vectors. It takes two vectors as input and
returns the distance between them as a `BINARY_DOUBLE`.

Syntax

  

![Description of inner_product.eps
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/inner_product.gif)  
[Description of the illustration
inner_product.eps](img_text/inner_product.md)

  

Parameters

  * `expr1` and `expr2` must evaluate to vectors and have the same number of dimensions. 

  * `INNER_PRODUCT` returns NULL, if either `expr1` or `expr2` is NULL, or if the dimensions between the two vectors do not match up. 

**Parent topic:** [Vector Distance Functions and Operators](vector-distance-
functions-and-operators.md "A vector distance function takes in two vector
operands and a distance metric to compute a mathematical distance between
those two vectors, based on the distance metric provided. You can optionally
use shorthand distance functions and operators instead of their corresponding
distance functions.")


[← Previous](cosine_distance-vecse.md)

[Next →](chunking-and-vector-generation-functions.md)
