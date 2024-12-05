[Previous](json-metadata-parameters-onnx-models.html) [Next](query.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR](dbms_vector-vecse.html)
  4. LOAD_ONNX_MODEL_CLOUD



## LOAD_ONNX_MODEL_CLOUD

This procedure enables you to load an ONNX model from object storage into the Database.

Syntax
    
    
    DBMS_VECTOR.LOAD_ONNX_MODEL_CLOUD (
         model_name  IN  VARCHAR2,
         credential  IN  VARCHAR2,
         uri         IN  VARCHAR2,
         metadata    IN  JSON DEFAULT JSON('{"function" : "embedding", '|| 
                              '"embeddingOutput" : "embedding", "input": {"input":["DATA"]}}')
    );

Parameters

Table 12-8 LOAD_ONNX_MODEL_CLOUD Procedure Parameters

Parameter  |  Description   
---|---  
model_name | The name of the model in the form [schema_name.]model_name. If you do not specify a schema, then your own schema is used.  
credential | The name of the credential to be used to access Object Store.  
uri | The URI of the ONNX model.  
metadata | A JSON description of the metadata describing the model. The metadata at minimum must describe the machine learning function supported by the model. The model's metadata parameters are described in JSON Metadata Parameters for ONNX Models.  
  
Examples

The following example includes a code snippet of using the `DBMS_VECTOR.LOAD_ONNX_MODEL_CLOUD` procedure. 
    
    
    EXECUTE DBMS_VECTOR.LOAD_ONNX_MODEL_CLOUD(
        model_name => 'database',
        credential => 'MYCRED', 
        uri => 'https://objectstorage.us-phoenix-1.oraclecloud.com/n/namespace-string/b/bucketname/o/all-MiniLM-L6-v2.onnx',
        metadata => JSON('{"function" : "embedding", "embeddingOutput" : "embedding" , "input": {"input": ["DATA"]}}')
    );

Usage Notes

The name of the model follows the same restrictions as those used for other machine learning models, namely:

  * The schema name, if provided, is limited to 128 characters.
  * The model name is limited to 123 characters and must follow the rules of unquoted identifiers: they contain only alphanumeric characters, the underscore (_), dollar sign ($), and pound sign (#). The initial character must be alphabetic.
  * The model size is limited to 1 gigabyte.
  * The model must not depend on external initializers. To know more about initializers and other ONNX concepts, see <https://onnx.ai/onnx/intro/concepts.md>. 
  * There are default input and output names for input and output attributes for models that are prepared by the Python utility. You can load those models without the JSON parameters. For example: 
    
        EXECUTE DBMS_VECTOR.LOAD_ONNX_MODEL_CLOUD(
        'database', 
        'MYCRED',
        'https://objectstorage.us-phoenix-1.oraclecloud.com/n/namespace-string/b/bucketname/o/all-MiniLM-L6-v2.onnx'
    );




See Also:

[Oracle Machine Learning for SQL Userâs Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=DMPRG-GUID-A39EB438-4FAE-45C4-9E6B-FBEC7FA84BE8) for examples of using ONNX models for machine learning tasks 

**Parent topic:** [DBMS_VECTOR](dbms_vector-vecse.html "The DBMS_VECTOR package simplifies common operations with Oracle AI Vector Search, such as extracting chunks or embeddings from user data, generating text for a given prompt or an image, creating a vector index, or reporting on index accuracy.")

[← Previous](json-metadata-parameters-onnx-models.md)

[Next →](query.md)
