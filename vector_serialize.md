[Previous](from_vector.html) [Next](vector_norm.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Use SQL Functions for Vector Operations](use-sql-functions-vector-operations.html)
  3. [Constructors, Converters, and Descriptors](constructors-converters-descriptors-and-arithmetic-functions.html)4. [Vector Serializers](vector-serializers.html)
  5. VECTOR_SERIALIZE



## VECTOR_SERIALIZE

`VECTOR_SERIALIZE` is synonymous with `FROM_VECTOR.`

Syntax

  


![Description of vector_serialize.eps follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/vector_serialize.gif)[Descriptionof the illustration vector_serialize.eps](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img_text/vector_serialize.html)

  


Purpose

See [FROM_VECTOR](from_vector.html#GUID-AA60B3CB-FCB7-4944-9E06-976C272855B1 "FROM_VECTOR takes a vector as input and returns a string of type VARCHAR2 or CLOB as output.") for semantics and examples. 

Examples
    
    
    SELECT VECTOR_SERIALIZE(VECTOR('[1.1,2.2,3.3]',3,FLOAT32));
    
    
    VECTOR_SERIALIZE(VECTOR('[1.1,2.2,3.3]',3,FLOAT32))
    ---------------------------------------------------------------
    [1.10000002E+000,2.20000005E+000,3.29999995E+000]
    
    1 row selected.
    
    
    
    SELECT VECTOR_SERIALIZE(VECTOR('[1.1, 2.2, 3.3]',3,FLOAT32) RETURNING VARCHAR2(1000));
    
    
    VECTOR_SERIALIZE(VECTOR('[...]',3,FLOAT32)RETURNINGVARCHAR2(1000))
    ------------------------------------------------------------------
    [1.10000002E+000,2.20000005E+000,3.29999995E+000]
    
    1 row selected.
    
    
    SELECT VECTOR_SERIALIZE(VECTOR('[1.1, 2.2, 3.3]',3,FLOAT32) RETURNING CLOB);
    
    
    VECTOR_SERIALIZE(VECTOR('[1.1, 2.2, 3.3]',3,FLOAT32)RETURNINGCLOB)
    --------------------------------------------------------
    [1.10000002E+000,2.20000005E+000,3.29999995E+000] 
    
    1 row selected.
    
    
    
    SELECT VECTOR_SERIALIZE(TO_VECTOR('[5,[2,4],[1.0,2.0]]', 5, FLOAT64, SPARSE) RETURNING CLOB FORMAT SPARSE);
    
    VECTOR_SERIALIZE(TO_VECTOR('[5,[2,4],[1.0,2.0]]',5,FLOAT64,SPARSE)RETURNINGCLOBF
    --------------------------------------------------------------------------------
    [5,[2,4],[1.0E+000,2.0E+000]]
    
    1 row selected.
    
    
    SELECT VECTOR_SERIALIZE(TO_VECTOR('[5,[2,4],[1.0,2.0]]', 5, FLOAT64, SPARSE) RETURNING CLOB FORMAT DENSE);
    
    VECTOR_SERIALIZE(TO_VECTOR('[5,[2,4],[1.0,2.0]]',5,FLOAT64,SPARSE)RETURNINGCLOBF
    --------------------------------------------------------------------------------
    [0,1.0E+000,0,2.0E+000,0]
    
    1 row selected.

**Parent topic:** [Vector Serializers](vector-serializers.html "FROM_VECTOR\(\) and VECTOR_SERIALIZE\(\) are synonymous serializers of vectors. The functions take a vector as input and return a string of type VARCHAR2 or CLOB as output.")

[← Previous](from_vector.md)

[Next →](vector_norm.md)
