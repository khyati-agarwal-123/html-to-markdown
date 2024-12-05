[Previous](disable_checkpoint.html) [Next](drop_onnx_model-procedure-dbms_vector.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR](dbms_vector-vecse.html)
  4. DROP_CREDENTIAL



## DROP_CREDENTIAL

Use the `DBMS_VECTOR.DROP_CREDENTIAL` credential helper procedure to drop an existing credential name from the data dictionary. 

Syntax
    
    
    DBMS_VECTOR.DROP_CREDENTIAL (
        CREDENTIAL_NAME      IN VARCHAR2
    );

CREDENTIAL_NAME

Specify the credential name that you want to drop.

Examples

  * For Generative AI:
    
        exec dbms_vector.drop_credential('OCI_CRED');

  * For Cohere:
    
        exec dbms_vector.drop_credential('COHERE_CRED');




**Parent topic:** [DBMS_VECTOR](dbms_vector-vecse.html "The DBMS_VECTOR package simplifies common operations with Oracle AI Vector Search, such as extracting chunks or embeddings from user data, generating text for a given prompt or an image, creating a vector index, or reporting on index accuracy.")

[← Previous](disable_checkpoint.md)

[Next →](drop_onnx_model-procedure-dbms_vector.md)
