[Previous](vector_embedding-vecse.md) [Next](vector-constructors.md)
JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.md)
  3. Constructors, Converters, and Descriptors

## Constructors, Converters, and Descriptors

Other basic vector operations for Oracle AI Vector Search involve creating,
converting, and describing vectors.

  * [Vector Constructors](vector-constructors.md)  
`TO_VECTOR()` and `VECTOR()` are synonymous constructors of vectors. The
functions take a string of type `VARCHAR2` or `CLOB` as input and return a
vector as output.

  * [Vector Serializers](vector-serializers.md)  
`FROM_VECTOR()` and `VECTOR_SERIALIZE()` are synonymous serializers of
vectors. The functions take a vector as input and return a string of type
`VARCHAR2` or `CLOB` as output.

  * [VECTOR_NORM](vector_norm-vecse.md)  
`VECTOR_NORM` returns the Euclidean norm of a vector `(SQRT(SUM((xi-yi)2)))`
as a `BINARY_DOUBLE`. This value is also called magnitude or size and
represents the Euclidean distance between the vector and the origin.

  * [VECTOR_DIMENSION_COUNT](vector_dimension_count-vecse.md)  
`VECTOR_DIMENSION_COUNT` returns the number of dimensions of a vector as a
`NUMBER`.

  * [VECTOR_DIMS](vector_dims-vecse.md)  
`VECTOR_DIMS` returns the number of dimensions of a vector as a `NUMBER`.
`VECTOR_DIMS` is synonymous with `VECTOR_DIMENSION_COUNT`.

  * [VECTOR_DIMENSION_FORMAT](vector_dimension_format-vecse.md)  
`VECTOR_DIMENSION_FORMAT` returns the storage format of the vector. It returns
a `VARCHAR2`, which can be one of the following values: `INT8`, `FLOAT32`, or
`FLOAT64`.

**Parent topic:** [Use SQL Functions for Vector Operations](use-sql-functions-
vector-operations.md "There are a number of SQL functions and operators that
you can use with vectors in Oracle AI Vector Search.")


[← Previous](vector_embedding-vecse.md)

[Next →](vector-constructors.md)
