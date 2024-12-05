[Previous](index_accuracy_query.html) [Next](index_vector_memory_advisor.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR](dbms_vector-vecse.html)
  4. INDEX_ACCURACY_REPORT



## INDEX_ACCURACY_REPORT

Use the `DBMS_VECTOR.INDEX_ACCURACY_REPORT` function to capture from your past workloads, accuracy values achieved by approximate searches using a particular vector index for a certain period of time. 

Syntax
    
    
    DBMS_VECTOR.INDEX_ACCURACY_REPORT (
        OWNER_NAME         IN VARCHAR2,
        INDEX_NAME         IN VARCHAR2,
        START_TIME         IN TIMESTAMP WITH TIME ZONE,
        END_TIME           IN TIMESTAMP WITH TIME ZONE
    ) return NUMBER;

Parameters

Table 12-5 INDEX_ACCURACY_REPORT (IN) Parameters of DBMS_VECTOR

Parameter | Description  
---|---  
owner_name | The name of the vector index owner.  
index_name | The name of the vector index.  
start_time | Specifies from what time to capture query vectors to consider for the accuracy computation. A NULL start_time uses query vectors captured in the last 24 hours.  
end_time | Specifies an end point up until which query vectors are considered for accuracy computation. A NULL end_time uses query vectors captured from start_time until the current time.  
  
For information about determining the accuracy of your vector indexes, see [Index Accuracy Report](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=VECSE-GUID-A084929C-7A04-4764-9E5B-1204E0844CAF) in Oracle Database AI Vector Search User's Guide. 

**Parent topic:** [DBMS_VECTOR](dbms_vector-vecse.html "The DBMS_VECTOR package simplifies common operations with Oracle AI Vector Search, such as extracting chunks or embeddings from user data, generating text for a given prompt or an image, creating a vector index, or reporting on index accuracy.")

[← Previous](index_accuracy_query.md)

[Next →](index_vector_memory_advisor.md)
