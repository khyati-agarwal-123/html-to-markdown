[Previous](vector_serialize.html) [Next](vector_dimension_count.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.html)
  3. [Constructors, Converters, and Descriptors](constructors-converters-descriptors-and-arithmetic-functions.html)
  4. VECTOR_NORM



## VECTOR_NORM

`VECTOR_NORM` returns the Euclidean norm of a vector `(SQRT(SUM((xi-yi)2)))` as a `BINARY_DOUBLE`. This value is also called magnitude or size and represents the Euclidean distance between the vector and the origin. 

Syntax

  


![Description of vector_norm.eps follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/vector_norm.gif)[Descriptionof the illustration vector_norm.eps](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img_text/vector_norm.html)

  


Parameters

`expr` must evaluate to a vector. 

If `expr` is NULL, NULL is returned. 

Example
    
    
    SELECT VECTOR_NORM( TO_VECTOR('[4, 3]', 2, FLOAT32) );
    
    VECTOR_NORM(TO_VECTOR('[4,3]',2,FLOAT32))
    -----------------------------------------
    5.0E+000

**Parent topic:** [Constructors, Converters, and Descriptors](constructors-converters-descriptors-and-arithmetic-functions.html "Other basic vector operations for Oracle AI Vector Search involve creating, converting, and describing vectors.")

[← Previous](vector_serialize.md)

[Next →](vector_dimension_count.md)
