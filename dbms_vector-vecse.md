[Previous](vector-search-pl-sql-packages-node.html) [Next](create_credential-dbms_vector.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. DBMS_VECTOR



## DBMS_VECTOR

The `DBMS_VECTOR` package simplifies common operations with Oracle AI Vector Search, such as extracting chunks or embeddings from user data, generating text for a given prompt or an image, creating a vector index, or reporting on index accuracy. 

This table lists the `DBMS_VECTOR` subprograms and briefly describes them. 

Table 12-1 DBMS_VECTOR Package Subprograms

Subprogram | Description  
---|---  
ONNX Model Related Procedures: These procedures enable you to load an ONNX model into Oracle Database and drop the ONNX model.  
LOAD_ONNX_MODEL | Loads an ONNX model into the database  
LOAD_ONNX_MODEL_CLOUD | Loads an ONNX model from object storage into the database  
DROP_ONNX_MODEL Procedure | Drops the ONNX model  
Chainable Utility (UTL) Functions: These functions are a set of modular and flexible functions within vector utility PL/SQL packages. You can chain these together to automate end-to-end data transformation and similarity search operations.  
UTL_TO_CHUNKS | Splits data into smaller pieces or chunks  
UTL_TO_EMBEDDING and UTL_TO_EMBEDDINGS | Converts text or an image to one or more vector embeddings  
UTL_TO_GENERATE_TEXT | Generates text for a prompt (input string) or an image  
Credential Helper Procedures: These procedures enable you to securely manage authentication credentials in the database. You require these credentials to enable access to third-party service providers for making REST calls.  
CREATE_CREDENTIAL | Creates a credential name  
DROP_CREDENTIAL | Drops an existing credential name  
Data Access Functions: These functions enable you to retrieve data, create index, and perform simple similarity search operations.  
CREATE_INDEX | Creates a vector index  
REBUILD_INDEX | Rebuilds a vector index  
GET_INDEX_STATUS | Describes the status of a vector index creation  
ENABLE_CHECKPOINT | Enables the Checkpoint feature for a vector index user and index name  
DISABLE_CHECKPOINT | Disables the Checkpoint feature for a vector index user and index name  
INDEX_VECTOR_MEMORY_ADVISOR | Determines the vector memory size that is needed for a vector index  
QUERY | Performs a similarity search query  
RERANK | Reorders search results for a more relevant output  
Accuracy Reporting Function: These functions enable you to determine the accuracy of existing search indexes and to capture accuracy values achieved by approximate searches performed by past workloads.  
INDEX_ACCURACY_QUERY | Verifies the accuracy of a vector index  
INDEX_ACCURACY_REPORT | Captures accuracy values achieved by approximate searches  
  
Note:

`DBMS_VECTOR` is a lightweight package that does not support text processing or summarization operations. Therefore, the `UTL_TO_TEXT` and `UTL_TO_SUMMARY` chainable utility functions and all the chunker helper procedures are available only in the advanced `DBMS_VECTOR_CHAIN` package. 

  * [CREATE_CREDENTIAL](create_credential-dbms_vector.html)  
Use the `DBMS_VECTOR.CREATE_CREDENTIAL` credential helper procedure to create a credential name for storing user authentication details in Oracle Database. 
  * [CREATE_INDEX](create_index.html)  
Use the `DBMS_VECTOR.CREATE_INDEX` procedure to create a vector index. 
  * [DISABLE_CHECKPOINT](disable_checkpoint.html)  
Use the `DISABLE_CHECKPOINT` procedure to disable the Checkpoint feature for a given Hierarchical Navigable Small World (HNSW) index user and HNSW index name. This operation purges all older checkpoints for the HNSW index. It also disables the creation of future checkpoints as part of the HNSW graph refresh. 
  * [DROP_CREDENTIAL](drop_credential-dbms_vector.html)  
Use the `DBMS_VECTOR.DROP_CREDENTIAL` credential helper procedure to drop an existing credential name from the data dictionary. 
  * [DROP_ONNX_MODEL Procedure](drop_onnx_model-procedure-dbms_vector.html)  
This procedure deletes the specified ONNX model. 
  * [ENABLE_CHECKPOINT](enable_checkpoint.html)  
Use the `ENABLE_CHECKPOINT` procedure to enable the Checkpoint feature for a given Hierarchical Navigable Small World (HNSW) index user and HNSW index name. 
  * [GET_INDEX_STATUS](get_index_status.html)  
Use the `GET_INDEX_STATUS` procedure to query the status of a vector index creation. 
  * [INDEX_ACCURACY_QUERY](index_accuracy_query.html)  
Use the `DBMS_VECTOR.INDEX_ACCURACY_QUERY` function to verify the accuracy of a vector index for a given query vector, top-K, and target accuracy. 
  * [INDEX_ACCURACY_REPORT](index_accuracy_report.html)  
Use the `DBMS_VECTOR.INDEX_ACCURACY_REPORT` function to capture from your past workloads, accuracy values achieved by approximate searches using a particular vector index for a certain period of time. 
  * [INDEX_VECTOR_MEMORY_ADVISOR](index_vector_memory_advisor.html)  
Use the `INDEX_VECTOR_MEMORY_ADVISOR` procedure to determine the vector memory size needed for a particular vector index. This helps you evaluate the number of indexes that can fit for each simulated vector memory size. 
  * [LOAD_ONNX_MODEL](load_onnx_model-procedure.html)  
This procedure enables you to load an ONNX model into the Database. 
  * [LOAD_ONNX_MODEL_CLOUD](load_onnx_model_cloud.html)  
This procedure enables you to load an ONNX model from object storage into the Database. 
  * [QUERY](query.html)  
Use the `DBMS_VECTOR.QUERY` function to perform a similarity search operation which returns the top-k results as a JSON array. 
  * [REBUILD_INDEX](rebuild_index.html)  
Use the `DBMS_VECTOR.REBUILD_INDEX` function to rebuild a vector index. 
  * [RERANK](rerank-dbms_vector.html)  
Use the `DBMS_VECTOR.RERANK` function to reassess and reorder an initial set of results to retrieve more relevant search output. 
  * [UTL_TO_CHUNKS](utl_to_chunks-dbms_vector.html)  
Use the `DBMS_VECTOR.UTL_TO_CHUNKS` chainable utility function to split a large plain text document into smaller chunks of text. 
  * [UTL_TO_EMBEDDING and UTL_TO_EMBEDDINGS](utl_to_embedding-and-utl_to_embeddings-dbms_vector.html)  
Use the `DBMS_VECTOR.UTL_TO_EMBEDDING` and `DBMS_VECTOR.UTL_TO_EMBEDDINGS` chainable utility functions to generate one or more vector embeddings from textual documents and images. 
  * [UTL_TO_GENERATE_TEXT](utl_to_generate_text-dbms_vector.html)  
Use the `DBMS_VECTOR.UTL_TO_GENERATE_TEXT` chainable utility function to generate a text response for a given prompt or an image, by accessing third-party text generation models. 



**Parent topic:** [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html "The DBMS_VECTOR, DBMS_VECTOR_CHAIN, and DBMS_HYBRID_VECTOR PL/SQL APIs are available to support Oracle AI Vector Search capabilities.")

[← Previous](vector-search-pl-sql-packages-node.md)

[Next →](create_credential-dbms_vector.md)
