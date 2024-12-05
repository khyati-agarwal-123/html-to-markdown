[Previous](drop_credential-dbms_vector.html) [Next](enable_checkpoint.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR](dbms_vector-vecse.html)
  4. DROP_ONNX_MODEL Procedure



## DROP_ONNX_MODEL Procedure

This procedure deletes the specified ONNX model.

Syntax
    
    
    DBMS_VECTOR.DROP_ONNX_MODEL (model_name IN VARCHAR2,
                                      force      IN BOOLEAN DEFAULT FALSE);

Parameters

Table 12-3 DROP_ONNX_MODEL Procedure Parameters

Parameter | Description  
---|---  
model_name | Name of the machine learning ONNX model in the form [schema_name.]model_name. If you do not specify a schema, then your own schema is used.  
force | Forces the machine learning ONNX model to be dropped even if it is invalid. An ONNX model may be invalid if a serious system error interrupted the model build process.  
  
Usage Note

To drop an ONNX model, you must be the owner or you must have the `DB_DEVELOPER_ROLE`. 

Example

You can use the following command to delete a valid ONNX model named `doc_model` that exists in your schema. 
    
    
    BEGIN
      DBMS_VECTOR.DROP_ONNX_MODEL(model_name => 'doc_model');
    END;
    /

**Parent topic:** [DBMS_VECTOR](dbms_vector-vecse.html "The DBMS_VECTOR package simplifies common operations with Oracle AI Vector Search, such as extracting chunks or embeddings from user data, generating text for a given prompt or an image, creating a vector index, or reporting on index accuracy.")

[← Previous](drop_credential-dbms_vector.md)

[Next →](enable_checkpoint.md)
