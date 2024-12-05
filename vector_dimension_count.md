[Previous](vector_norm.html) [Next](vector_dims.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.html)
  3. [Constructors, Converters, and Descriptors](constructors-converters-descriptors-and-arithmetic-functions.html)
  4. VECTOR_DIMENSION_COUNT



## VECTOR_DIMENSION_COUNT

`VECTOR_DIMENSION_COUNT` returns the number of dimensions of a vector as a `NUMBER`. 

Syntax

  


![Description of vector_dimension_count.eps follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/vector_dimension_count.gif)[Descriptionof the illustration vector_dimension_count.eps](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img_text/vector_dimension_count.html)

  


Purpose

`VECTOR_DIMENSION_COUNT` is synonymous with [VECTOR_DIMS](vector_dims.html#GUID-010349D7-190D-430B-A798-ACC486E1036A "VECTOR_DIMS returns the number of dimensions of a vector as a NUMBER. VECTOR_DIMS is synonymous with VECTOR_DIMENSION_COUNT."). 

Parameters

`expr` must evaluate to a vector. 

If `expr` is NULL, NULL is returned. 

Example
    
    
    SELECT VECTOR_DIMENSION_COUNT( TO_VECTOR('[34.6, 77.8]', 2, FLOAT64) );
    
    VECTOR_DIMENSION_COUNT(TO_VECTOR('[34.6,77.8]',2,FLOAT64))
    ----------------------------------------------------------
    2                          
    

**Parent topic:** [Constructors, Converters, and Descriptors](constructors-converters-descriptors-and-arithmetic-functions.html "Other basic vector operations for Oracle AI Vector Search involve creating, converting, and describing vectors.")

[← Previous](vector_norm.md)

[Next →](vector_dims.md)
