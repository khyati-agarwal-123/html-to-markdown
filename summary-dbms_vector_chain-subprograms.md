[Previous](summary-dbms_vector-subprograms.md) [Next](glossary-list-
topic.md) JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.md)
  3. Summary of DBMS_VECTOR_CHAIN Subprograms

## Summary of DBMS_VECTOR_CHAIN Subprograms

The `DBMS_VECTOR_CHAIN` package enables advanced operations with Oracle AI
Vector Search, such as chunking and embedding data along with text generation
and summarization capabilities. It is more suitable for text processing with
similarity search, using functionality that can be pipelined together for an
end-to-end search.

This table lists the `DBMS_VECTOR_CHAIN` subprograms and briefly describes
them.

Table 12-2 DBMS_VECTOR_CHAIN Package Subprograms

Subprogram | Description  
---|---  
Chainable Utility (UTL) Functions:  These functions are a set of modular and
flexible functions within vector utility PL/SQL packages. You can chain these
together to automate end-to-end data transformation and similarity search
operations.  
[UTL_TO_TEXT](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-73397E89-92FB-48ED-94BB-1AD960C4EA1F) |  Extracts plain text data from documents  
[UTL_TO_CHUNKS](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-4E145629-7098-4C7C-804F-FC85D1F24240) |  Splits data into smaller pieces or chunks  
[UTL_TO_EMBEDDING and UTL_TO_EMBEDDINGS](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-C6439E94-4E86-4ECD-954E-4B73D53579DE) |  Converts data to one or more vector embeddings  
[UTL_TO_SUMMARY](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-EC9DDB58-6A15-4B36-BA66-ECBA20D2CE57) |  Extracts a summary from documents  
[UTL_TO_GENERATE_TEXT](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-017C9002-194C-48E5-B59B-EF5C60BC8405) |  Generates text for a prompt (input string)  
Credential Helper Procedures:  These procedures enable you to securely manage
authentication credentials in the database. You require these credentials to
enable access to third-party service providers for making REST calls.  
[CREATE_CREDENTIAL](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-A6E28402-DC43-44C6-A1B2-75C3F270DD76) |  Creates a credential name  
[DROP_CREDENTIAL](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-FCA739BA-4849-45BF-A860-251D45E31B17) |  Drops an existing credential name  
Chunker Helper Procedures:  These procedures enable you to configure
vocabulary and language data (abbreviations), to be used with the
`VECTOR_CHUNKS` SQL function or `UTL_TO_CHUNKS` PL/SQL function.  
[CREATE_VOCABULARY](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-2D19528E-0F0D-4102-8EC7-E9EA62C66C2D) |  Loads your token vocabulary file into the database  
[DROP_VOCABULARY](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-2CC9EBDB-717F-4AA7-8FDE-7503BE185D87) |  Removes existing vocabulary data  
[CREATE_LANG_DATA](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-C9756FA9-B0B6-4750-8D9C-ADEF8B67C675) |  Loads your language data file into the database  
[DROP_LANG_DATA](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-55F54E07-1026-4021-A194-3E068471426E) |  Removes existing abbreviation data  
  
Note:

The `DBMS_VECTOR_CHAIN` package requires you to install the `CONTEXT`
component of Oracle Text, an Oracle Database technology that provides
indexing, term extraction, text analysis, text summarization, word and theme
searching, and other utilities.

Due to underlying dependance on the text processing capabilities of Oracle
Text, note that both the `UTL_TO_TEXT` and `UTL_TO_SUMMARY` chainable utility
functions and all the chunker helper procedures are available only in this
package through Oracle Text.

**Parent topic:** [Vector Search PL/SQL Packages](vector-search-pl-sql-
packages-node.md "The DBMS_VECTOR and DBMS_VECTOR_CHAIN PL/SQL APIs are
available to support Oracle AI Vector Search capabilities.")


[← Previous](summary-dbms_vector-subprograms.md)

[Next →](glossary-list-topic.html#GUID-CF734304-338A-4776-B75C-EEB2FF7D2E6D)
