[Previous](vector-search-pl-sql-packages-node.md) [Next](summary-
dbms_vector_chain-subprograms.md) JavaScript must be enabled to correctly
display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.md)
  3. Summary of DBMS_VECTOR Subprograms

## Summary of DBMS_VECTOR Subprograms

The `DBMS_VECTOR` package simplifies common operations with Oracle AI Vector
Search, such as extracting chunks or embeddings from user data, generating
text for a given prompt, and reporting on index accuracy.

This table lists the `DBMS_VECTOR` subprograms and briefly describes them.

Table 12-1 DBMS_VECTOR Package Subprograms

Subprogram | Description  
---|---  
ONNX Model Related Procedures:  These procedures enable you to load an ONNX
model into Oracle Database and drop the ONNX model.  
[LOAD_ONNX_MODEL](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-7F1D7992-D8F7-4AD9-9BF6-6EFFC1B0617A) |  Loads an ONNX model into the database  
[DROP_ONNX_MODEL](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-8031CBC3-3B94-4780-9647-C7D55C0B3331) |  Drops the ONNX model  
Chainable Utility (UTL) Functions:  These functions are a set of modular and
flexible functions within vector utility PL/SQL packages. You can chain these
together to automate end-to-end data transformation and similarity search
operations.  
[UTL_TO_CHUNKS](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-4D96238E-2ABD-450D-8A9A-65E16A33481A) |  Splits data into smaller pieces or chunks  
[UTL_TO_EMBEDDING and UTL_TO_EMBEDDINGS](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-8E615832-F6C0-4435-8F43-3FAF80692D5B) |  Converts data to one or more vector embeddings  
[UTL_TO_GENERATE_TEXT](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-EA78DFB6-D951-43D1-8ECB-DD6D21C6F6A6) |  Generates text for a prompt (input string)  
Credential Helper Procedures:  These procedures enable you to securely manage
authentication credentials in the database. You require these credentials to
enable access to third-party service providers for making REST calls.  
[CREATE_CREDENTIAL](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-4BBCBF46-3903-4EBB-8BE8-A7690151CF25) |  Creates a credential name  
[DROP_CREDENTIAL](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-9F5DA186-6F2E-471F-9CEC-B32D502A1695) |  Drops an existing credential name  
Data Access Functions:  These functions enable you to retrieve data, create
index, and perform simple similarity search operations.  
[CREATE_INDEX](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-33B844C5-CF57-4213-B2C8-31D82D2E02F6) |  Creates a vector index  
[REBUILD_INDEX](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-7A7B63F6-97E3-44C6-8CD4-C84376F06F14) |  Rebuilds a vector index  
[QUERY](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-BCB1DEE6-E8E0-43EA-9E5F-E346C981BC05) |  Perform a similarity search query  
Accuracy Reporting Function:  These functions enable you to determine the
accuracy of existing search indexes and to capture accuracy values achieved by
approximate searches performed by past workloads.  
[INDEX_ACCURACY_QUERY](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-4DC6EDAD-659E-4093-B1CE-D116E0EC6A1D) |  Verifies the accuracy of a vector index  
[INDEX_ACCURACY_REPORT](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-E4360384-B882-4D5C-BC7F-332BB5E54516) | Captures accuracy values achieved by approximate searches  
  
Note:

`DBMS_VECTOR` is a lightweight package that does not support text processing
or summarization operations. Therefore, the `UTL_TO_TEXT` and `UTL_TO_SUMMARY`
chainable utility functions and all the chunker helper procedures are
available only in the advanced `DBMS_VECTOR_CHAIN` package.

**Parent topic:** [Vector Search PL/SQL Packages](vector-search-pl-sql-
packages-node.md "The DBMS_VECTOR and DBMS_VECTOR_CHAIN PL/SQL APIs are
available to support Oracle AI Vector Search capabilities.")


[← Previous](vector-search-pl-sql-packages-node.md)

[Next →](summary-dbms_vector_chain-subprograms.md)
