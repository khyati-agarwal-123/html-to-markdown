[Previous](chainable-utility-functions-and-common-use-cases.html) [Next](supplied-vector-utility-pl-sql-packages.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Generate Vector Embeddings](generate-vector-embeddings-node.html)
  3. [About Vector Generation](vector-generation.html)4. [About PL/SQL Packages to Generate Embeddings](pl-sql-packages-generate-embeddings.html)
  5. About Vector Helper Procedures



## About Vector Helper Procedures

Vector helper procedures let you configure authentication credentials, preferences, and language-specific data for use in chainable utility functions.

At a high level, the supplied vector helper procedures include:

  * **Credential helper procedures** to securely manage authentication credentials, which are used to access third-party providers when making REST API calls. 

Function | Description  
---|---  
CREATE_CREDENTIAL | Creates a credential name for securely storing user authentication credentials in Oracle Database.  
DROP_CREDENTIAL | Drops an existing credential name.  
  
  * **Preference helper procedures** to manage vectorizer preferences, which are used when creating or altering hybrid vector indexes. 

Function | Description  
---|---  
CREATE_PREFERENCE | Creates a vectorizer preference in the database.  
DROP_PREFERENCE | Drops an existing vectorizer preference from the database.  
  
  * **Chunker helper procedures** to manage custom vocabulary and language data, which are used when chunking user data. 

Function | Description  
---|---  
CREATE_VOCABULARY | Loads your own vocabulary file into the database.  
DROP_VOCABULARY | Removes the specified vocabulary data from the database.  
CREATE_LANG_DATA | Loads your own language data file (abbreviation tokens) into the database.  
DROP_LANG_DATA | Removes abbreviation data for a given language from the database.  
  



**Related Topics**

  * [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html#GUID-04ACF179-957C-4F03-AC1D-4DA44B3E12A2 "The DBMS_VECTOR, DBMS_VECTOR_CHAIN, and DBMS_HYBRID_VECTOR PL/SQL APIs are available to support Oracle AI Vector Search capabilities.")
  * [Text Processing Views](text-processing-views.html#GUID-E2B9F02C-E2A6-439B-9A2E-177FF7FA6EE0 "These views display language-specific data \(abbreviation token details\) and vocabulary data related to the Oracle AI Vector Search SQL and PL/SQL utilities.")



**Parent topic:** [About PL/SQL Packages to Generate Embeddings](pl-sql-packages-generate-embeddings.html "Choose to implement Vector Utility PL/SQL packages to perform chunking, embedding, and text generation operations along with text processing and similarity search, both within and outside the database. You can schedule these operations as end-to-end pipelines. The supplied PL/SQL packages for vector generation are DBMS_VECTOR and DBMS_VECTOR_CHAIN.")

[← Previous](chainable-utility-functions-and-common-use-cases.md)

[Next →](supplied-vector-utility-pl-sql-packages.md)
