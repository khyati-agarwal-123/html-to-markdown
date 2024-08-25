[Previous](chainable-utility-functions-and-common-use-cases.md)
[Next](supplied-vector-utility-pl-sql-packages.md) JavaScript must be
enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Generate Vector Embeddings](generate-vector-embeddings-node.md)
  3. [About Vector Generation](vector-generation.md)
  4. [About PL/SQL Packages to Generate Embeddings](pl-sql-packages-generate-embeddings.md)
  5. About Vector Helper Procedures

## About Vector Helper Procedures

Vector helper procedures let you configure authentication credentials and
language-specific data, for use in chainable utility functions.

At a high level, the supplied vector helper procedures include:

  * **Credential helper procedures** to securely manage authentication credentials, which are used to access third-party providers when making REST API calls. 

Function | Description  
---|---  
`CREATE_CREDENTIAL` |  Creates a credential name for securely storing user authentication credentials in the database.   
`DROP_CREDENTIAL` |  Drops an existing credential name.  
  
  * **Chunker helper procedures** to manage custom vocabulary and language data, which are used when chunking user data. 

Function | Description  
---|---  
`CREATE_VOCABULARY` |  Loads your own vocabulary file into the database.   
`DROP_VOCABULARY` |  Removes the specified vocabulary data from the database.  
`CREATE_LANG_DATA` |  Loads your own language data file (abbreviation tokens) into the database.   
`DROP_LANG_DATA` |  Removes abbreviation data for a given language from the database.  
  

**Related Topics**

  * [Vector Utilities-Related Views](vector-utilities-related-views.md#GUID-E2B9F02C-E2A6-439B-9A2E-177FF7FA6EE0 "These views display language-specific data \(abbreviation token details\) and vocabulary data related to the Oracle AI Vector Search SQL and PL/SQL utilities.")

**Parent topic:** [About PL/SQL Packages to Generate Embeddings](pl-sql-
packages-generate-embeddings.md "Choose to implement Vector Utility PL/SQL
packages to perform chunking, embedding, and text generation operations along
with text processing and similarity search, both within and outside the
database. The supplied PL/SQL packages for vector generation are DBMS_VECTOR
and DBMS_VECTOR_CHAIN.")


[← Previous](chainable-utility-functions-and-common-use-cases.md)

[Next →](supplied-vector-utility-pl-sql-packages.md)
