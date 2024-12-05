[Previous](index_accuracy_report.html) [Next](load_onnx_model-procedure.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR](dbms_vector-vecse.html)
  4. INDEX_VECTOR_MEMORY_ADVISOR



## INDEX_VECTOR_MEMORY_ADVISOR

Use the `INDEX_VECTOR_MEMORY_ADVISOR` procedure to determine the vector memory size needed for a particular vector index. This helps you evaluate the number of indexes that can fit for each simulated vector memory size. 

Syntax

  * Using the number and type of vector dimensions that you want to store in your vector index. 
    
        DBMS_VECTOR.INDEX_VECTOR_MEMORY_ADVISOR(
        INDEX_TYPE, 
        NUM_VECTORS, 
        DIM_COUNT, 
        DIM_TYPE, 
        PARAMETER_JSON, 
        RESPONSE_JSON);

  * Using the table and vector column on which you want to create your vector index: 
    
        DBMS_VECTOR.INDEX_VECTOR_MEMORY_ADVISOR(
        TABLE_OWNER, 
        TABLE_NAME, 
        COLUMN_NAME, 
        INDEX_TYPE, 
        PARAMETER_JSON, 
        RESPONSE_JSON);




Table 12-6 Syntax Details: INDEX_VECTOR_MEMORY_ADVISOR

Parameter | Description  
---|---  
INDEX_TYPE | Type of vector index: IVF for Inverted File Flat (IVF) vector indexes HNSW for Hierarchical Navigable Small World (HNSW) vector indexes  
NUM_VECTORS | Number of vectors that you plan to create the vector index with.  
DIM_COUNT | Number of dimensions of a vector as a NUMBER.  
DIM_TYPE | Type of dimensions of a vector. Possible values are: FLOAT16 FLOAT32 FLOAT64 INT8  
TABLE_OWNER | Owner name of the table on which to create the vector index.  
TABLE_NAME | Table name on which to create the vector index.  
COLUMN_NAME | Name of the vector column on which to create the vector index.  
PARAMETER_JSON | Input parameter in JSON format. You can specify only one of the following form: PARAMTER_JSON=>{"accuracy":value} INDEX_TYPE=>IVF, parameter_json=>{"neighbor_partitions":value} INDEX_TYPE=>HNSW, parameter_json=>{"neighbors":value} Note: You cannot specify values for accuracy along with neighbor_partitions or neighbors.  
RESPONSE_JSON | JSON-formatted response string.  
  
Examples

  * Using neighbors in the parameters list: 
    
        exec DBMS_VECTOR.INDEX_VECTOR_MEMORY_ADVISOR(
        INDEX_TYPE=>'HNSW', 
        NUM_VECTORS=>10000, 
        DIM_COUNT=>768, 
        DIM_TYPE=>'FLOAT32', 
        PARAMETER_JSON=>'{"neighbors":128}', 
        RESPONSE_JSON=>:response_json); 
    
    Suggested vector memory pool size: 59918628 Bytes

  * Using accuracy in the parameters list:
    
        exec DBMS_VECTOR.INDEX_VECTOR_MEMORY_ADVISOR(
        INDEX_TYPE=>'HNSW', 
        NUM_VECTORS=>10000, 
        DIM_COUNT=>768, 
        DIM_TYPE=>'FLOAT32', 
        PARAMETER_JSON=>'{"accuracy":90}', 
        RESPONSE_JSON=>:response_json); 
    
    Suggested vector memory pool size: 53926765 Bytes

  * Using the table and vector column on which you want to create the vector index:
    
        exec DBMS_VECTOR.INDEX_VECTOR_MEMORY_ADVISOR(
        'VECTOR_USER', 
        'VECTAB', 
        'DATA_VECTOR', 
        'HNSW', 
        RESPONSE_JSON=>:response_json); 
    
    Using default accuracy: 90% 
    Suggested vector memory pool size: 76396251 Bytes




**Related Topics**

  * [Oracle Database AI Vector Search User's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=VECSE-GUID-5D9B6B92-C62C-4927-9FB2-7A4437F24A19)**Parent topic:** [DBMS_VECTOR](dbms_vector-vecse.html "The DBMS_VECTOR package simplifies common operations with Oracle AI Vector Search, such as extracting chunks or embeddings from user data, generating text for a given prompt or an image, creating a vector index, or reporting on index accuracy.")

[← Previous](index_accuracy_report.md)

[Next →](load_onnx_model-procedure.md)
