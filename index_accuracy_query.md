[Previous](get_index_status.html) [Next](index_accuracy_report.html)
JavaScript must be enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR](dbms_vector-vecse.html)
  4. INDEX_ACCURACY_QUERY

## INDEX_ACCURACY_QUERY

Use the `DBMS_VECTOR.INDEX_ACCURACY_QUERY` function to verify the accuracy of
a vector index for a given query vector, top-K, and target accuracy.

Syntax

    
    
    DBMS_VECTOR.INDEX_ACCURACY_QUERY (
        OWNER_NAME         IN VARCHAR2,
        INDEX_NAME         IN VARCHAR2,
        QV                 IN VECTOR,
        TOP_K              IN NUMBER,
        TARGET_ACCURACY    IN NUMBER
    ) return VARCHAR2;
    
    DBMS_VECTOR.INDEX_ACCURACY_QUERY (
        OWNER_NAME         IN VARCHAR2, 
        INDEX_NAME         IN VARCHAR2,
        QV                 IN VECTOR,
        TOP_K              IN NUMBER,
        QUERY_PARAM        IN JSON
    ) return VARCHAR2;

Parameters

Table 12-4 INDEX_ACCURACY_QUERY (IN) Parameters of DBMS_VECTOR

Parameter | Description  
---|---  
owner_name | The name of the vector index owner.  
index_name | The name of the vector index.  
qv | Specifies the query vector.  
top_k | The top_k value for accuracy computation.  
target_accuracy | The target accuracy value for the vector index.  
  
For information about determining the accuracy of your vector indexes, see
[Index Accuracy Report](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=VECSE-GUID-A084929C-7A04-4764-9E5B-1204E0844CAF) in
Oracle Database AI Vector Search User's Guide.

**Parent topic:** [DBMS_VECTOR](dbms_vector-vecse.html "The DBMS_VECTOR
package simplifies common operations with Oracle AI Vector Search, such as
extracting chunks or embeddings from user data, generating text for a given
prompt or an image, creating a vector index, or reporting on index accuracy.")


[← Previous](get_index_status.md)

[Next →](index_accuracy_report.md)
