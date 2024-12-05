[Previous](utl_to_generate_text-dbms_vector.html) [Next](create_credential-dbms_vector_chain.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. DBMS_VECTOR_CHAIN



## DBMS_VECTOR_CHAIN

The `DBMS_VECTOR_CHAIN` package enables advanced operations with Oracle AI Vector Search, such as chunking and embedding data along with text generation and summarization capabilities. It is more suitable for text processing with similarity search and hybrid search, using functionality that can be pipelined together for an end-to-end search. 

This table lists the `DBMS_VECTOR_CHAIN` subprograms and briefly describes them. 

Table 12-17 DBMS_VECTOR_CHAIN Package Subprograms

Subprogram | Description  
---|---  
Chainable Utility (UTL) Functions: These functions are a set of modular and flexible functions within vector utility PL/SQL packages. You can chain these together to automate end-to-end data transformation and similarity search operations.  
UTL_TO_TEXT | Extracts plain text data from documents  
UTL_TO_CHUNKS | Splits data into smaller pieces or chunks  
UTL_TO_EMBEDDING and UTL_TO_EMBEDDINGS | Converts text or an image to one or more vector embeddings  
UTL_TO_SUMMARY | Extracts a summary from documents  
UTL_TO_GENERATE_TEXT | Generates text for a prompt (input string) or an image  
Credential Helper Procedures: These procedures enable you to securely manage authentication credentials in the database. You require these credentials to enable access to third-party service providers for making REST calls.  
CREATE_CREDENTIAL | Creates a credential name  
DROP_CREDENTIAL | Drops an existing credential name  
Preference Helper Procedures: These procedures enable you to manage vectorizer preferences, to be used with the CREATE_HYBRID_VECTOR_INDEX and ALTER_INDEX SQL statements when creating or managing hybrid vector indexes.  
CREATE_PREFERENCE | Creates a vectorizer preference  
DROP_PREFERENCE | Drops an existing vectorizer preference  
Chunker Helper Procedures: These procedures enable you to configure vocabulary and language data (abbreviations), to be used with the VECTOR_CHUNKS SQL function or UTL_TO_CHUNKS PL/SQL function.  
CREATE_VOCABULARY | Loads your token vocabulary file into the database  
DROP_VOCABULARY | Removes existing vocabulary data  
CREATE_LANG_DATA | Loads your language data file into the database  
DROP_LANG_DATA | Removes existing abbreviation data  
Data Access Function: This function enables you to enhance search operations.  
RERANK | Reorders search results for a more relevant output  
  
Note:

The `DBMS_VECTOR_CHAIN` package requires you to install the `CONTEXT` component of Oracle Text, an Oracle Database technology that provides indexing, term extraction, text analysis, text summarization, word and theme searching, and other utilities. 

Due to underlying dependance on the text processing capabilities of Oracle Text, note that both the `UTL_TO_TEXT` and `UTL_TO_SUMMARY` chainable utility functions and all the chunker helper procedures are available only in this package through Oracle Text. 

  * [CREATE_CREDENTIAL](create_credential-dbms_vector_chain.html)  
Use the `DBMS_VECTOR_CHAIN.CREATE_CREDENTIAL` credential helper procedure to create a credential name for storing user authentication details in Oracle Database. 
  * [CREATE_LANG_DATA](create_lang_data.html)  
Use the `DBMS_VECTOR_CHAIN.CREATE_LANG_DATA` chunker helper procedure to load your own language data file into the database. 
  * [CREATE_PREFERENCE](create_preference.html)  
Use the `DBMS_VECTOR_CHAIN.CREATE_PREFERENCE` preference helper procedure to create a vectorizer preference, to be used when creating or updating hybrid vector indexes. 
  * [CREATE_VOCABULARY](create_vocabulary.html)  
Use the `DBMS_VECTOR_CHAIN.CREATE_VOCABULARY` chunker helper procedure to load your own token vocabulary file into the database. 
  * [DROP_CREDENTIAL](drop_credential-dbms_vector_chain.html)  
Use the `DBMS_VECTOR_CHAIN.DROP_CREDENTIAL` credential helper procedure to drop an existing credential name from the data dictionary. 
  * [DROP_LANG_DATA](drop_lang_data.html)  
Use the `DBMS_VECTOR_CHAIN.DROP_LANG_DATA` chunker helper procedure to remove abbreviation data from the data dictionary. 
  * [DROP_PREFERENCE](drop_preference.html)  
Use the `DBMS_VECTOR_CHAIN.DROP_PREFERENCE` preference helper procedure to remove an existing Vectorizer preference. 
  * [DROP_VOCABULARY](drop_vocabulary.html)  
Use the `DBMS_VECTOR_CHAIN.DROP_VOCABULARY` chunker helper procedure to remove vocabulary data from the data dictionary. 
  * [RERANK](rerank-dbms_vector_chain.html)  
Use the `DBMS_VECTOR_CHAIN.RERANK` function to reassess and reorder an initial set of results to retrieve more relevant search output. 
  * [UTL_TO_CHUNKS](utl_to_chunks-dbms_vector_chain.html)  
Use the `DBMS_VECTOR_CHAIN.UTL_TO_CHUNKS` chainable utility function to split a large plain text document into smaller chunks of text. 
  * [UTL_TO_EMBEDDING and UTL_TO_EMBEDDINGS](utl_to_embedding-and-utl_to_embeddings-dbms_vector_chain.html)  
Use the `DBMS_VECTOR_CHAIN.UTL_TO_EMBEDDING` and `DBMS_VECTOR_CHAIN.UTL_TO_EMBEDDINGS` chainable utility functions to generate one or more vector embeddings from textual documents and images. 
  * [UTL_TO_GENERATE_TEXT](utl_to_generate_text-dbms_vector_chain.html)  
Use the `DBMS_VECTOR_CHAIN.UTL_TO_GENERATE_TEXT` chainable utility function to generate a text response for a given prompt or an image, by accessing third-party text generation models. 
  * [UTL_TO_SUMMARY](utl_to_summary.html)  
Use the `DBMS_VECTOR_CHAIN.UTL_TO_SUMMARY` chainable utility function to generate a summary for textual documents. 
  * [UTL_TO_TEXT](utl_to_text.html)  
Use the `DBMS_VECTOR_CHAIN.UTL_TO_TEXT` chainable utility function to convert an input document (for example, PDF, DOC, JSON, XML, or HTML) to plain text. 
  * [Supported Languages and Data File Locations](supported-languages-and-data-file-locations.html)  
These are the supported languages for which language data files are distributed by default in the specified directories. 



**Parent topic:** [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html "The DBMS_VECTOR, DBMS_VECTOR_CHAIN, and DBMS_HYBRID_VECTOR PL/SQL APIs are available to support Oracle AI Vector Search capabilities.")

[← Previous](utl_to_generate_text-dbms_vector.md)

[Next →](create_credential-dbms_vector_chain.md)
