[Previous](drop_lang_data.html) [Next](drop_vocabulary.html) JavaScript must
be enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html)
  4. DROP_PREFERENCE

## DROP_PREFERENCE

Use the `DBMS_VECTOR_CHAIN.DROP_PREFERENCE` preference helper procedure to
remove an existing Vectorizer preference.

Syntax

    
    
    DBMS_VECTOR_CHAIN.DROP_PREFERENCE (PREF_NAME);

PREF_NAME

Name of the Vectorizer preference to drop.

Example

    
    
    DBMS_VECTOR_CHAIN.DROP_PREFERENCE ('scott_vectorizer');

**Parent topic:** [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html "The
DBMS_VECTOR_CHAIN package enables advanced operations with Oracle AI Vector
Search, such as chunking and embedding data along with text generation and
summarization capabilities. It is more suitable for text processing with
similarity search and hybrid search, using functionality that can be pipelined
together for an end-to-end search.")


[← Previous](drop_lang_data.md)

[Next →](drop_vocabulary.md)
