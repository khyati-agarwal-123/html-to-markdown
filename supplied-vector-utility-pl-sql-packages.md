[Previous](vector-helper-procedures.md) [Next](supported-third-party-
provider-operations.md) JavaScript must be enabled to correctly display this
content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Generate Vector Embeddings](generate-vector-embeddings-node.md)
  3. [About Vector Generation](vector-generation.md)
  4. [About PL/SQL Packages to Generate Embeddings](pl-sql-packages-generate-embeddings.md)
  5. Supplied Vector Utility PL/SQL Packages

## Supplied Vector Utility PL/SQL Packages

Use either a lightweight `DBMS_VECTOR` package or a more advanced
`DBMS_VECTOR_CHAIN` package with full capabilities.

  * `DBMS_VECTOR`: 

This package simplifies common operations with Oracle AI Vector Search, such
as chunking text into smaller segments, extracting vector embeddings from user
data, or generating text for a given prompt.

Subprogram | Operation | Provider | Implementation  
---|---|---|---  
Chainable Utility Functions |  `UTL_TO_CHUNKS` to perform chunking  |  Oracle Database  |  Calls the `VECTOR_CHUNKS` SQL function under the hood   
`UTL_TO_EMBEDDING` and `UTL_TO_EMBEDDINGS` to generate one or more embeddings  |  Oracle Database |  Calls the embedding model in ONNX format stored in the database  
Third-party REST providers |  Calls the specified third-party embedding model  
`UTL_TO_GENERATE_TEXT` to generate text for prompts  |  Third-party REST providers |  Calls the specified third-party text generation model  
Credential Helper Procedures |  `CREATE_CREDENTIAL` and `DROP_CREDENTIAL` to manage credentials for third-party service providers  |  Oracle Database  |  Stores credentials securely for use in Chainable Utility Functions  
  
For detailed information on this package, see
[DBMS_VECTOR](/pls/topic/lookup?ctx=en/database/oracle/oracle-
database/23/vecse&id=ARPLS-GUID-F9FCB225-821A-4CCA-92B5-58B9927234FA) in
Oracle Database PL/SQL Packages and Types Reference.

  * `DBMS_VECTOR_CHAIN`: 

This package provides chunking and embedding functions along with some text
generation and summarization capabilities. It is more suitable for text
processing with similarity search, using functionality that can be pipelined
together for an end-to-end search.

Subprogram | Operation | Provider | Implementation  
---|---|---|---  
Chainable Utility Functions |  `UTL_TO_TEXT` to extract plain text data from documents  |  Oracle Database  |  Uses the Oracle Text component (`CONTEXT`) of Oracle Database   
`UTL_TO_CHUNKS` to perform chunking  |  Oracle Database  |  Calls the `VECTOR_CHUNKS` SQL function under the hood   
`UTL_TO_EMBEDDING` and `UTL_TO_EMBEDDINGS` to generate one or more embeddings  |  Oracle Database  |  Calls the embedding model in ONNX format stored in the database  
Third-party REST providers |  Calls the specified third-party embedding model  
`UTL_TO_SUMMARY` to generate summaries  |  Oracle Database |  Uses Oracle Text  
Third-party REST providers |  Calls the specified third-party text summarization model  
`UTL_TO_GENERATE_TEXT` to generate text for prompts  |  Third-party REST providers |  Calls the specified third-party text generation model  
Credential Helper Procedures |  `CREATE_CREDENTIAL` and `DROP_CREDENTIAL` to manage credentials for third-party service providers  |  Oracle Database  |  Stores credentials securely for use in Chainable Utility Functions  
Chunker Helper Procedures |  `CREATE_VOCABULARY` and `DROP_VOCABULARY` to manage custom token vocabularies  |  Oracle Database  |  Uses Oracle Text  
`CREATE_LANG_DATA` and `DROP_LANG_DATA` to manage language-specific data (abbreviation tokens)  |  Oracle Database  |  Uses Oracle Text  
  
Note:

The `DBMS_VECTOR_CHAIN` package requires you to install the `CONTEXT`
component of Oracle Text, an Oracle Database technology that provides
indexing, term extraction, text analysis, text summarization, word and theme
searching, and other utilities.

Due to underlying dependance on the text processing capabilities of Oracle
Text, note that both the `UTL_TO_TEXT` and `UTL_TO_SUMMARY` chainable utility
functions and all the chunker helper procedures are available only in this
package through Oracle Text.

For detailed information on this package, see
[DBMS_VECTOR_CHAIN](/pls/topic/lookup?ctx=en/database/oracle/oracle-
database/23/vecse&id=ARPLS-GUID-D80DDBEF-F1A9-4267-9D3C-A54D237D95C1) in
Oracle Database PL/SQL Packages and Types Reference.

**Related Topics**

  * [Supported Third-Party Provider Operations](supported-third-party-provider-operations.md#GUID-BE3EE403-CD10-4708-A15F-EFB1FA69DF09 "Review a list of both the public and local, third-party REST providers that are supported for vector generation, summarization, and text generation operations.")

**Parent topic:** [About PL/SQL Packages to Generate Embeddings](pl-sql-
packages-generate-embeddings.md "Choose to implement Vector Utility PL/SQL
packages to perform chunking, embedding, and text generation operations along
with text processing and similarity search, both within and outside the
database. The supplied PL/SQL packages for vector generation are DBMS_VECTOR
and DBMS_VECTOR_CHAIN.")


[← Previous](vector-helper-procedures.md)

[Next →](supported-third-party-provider-operations.md)
