[Previous](drop_credential-dbms_vector_chain.html)[Next](drop_preference.html) JavaScript must be enabled to correctly display
this content

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html)
  4. DROP_LANG_DATA

## DROP_LANG_DATA

Use the `DBMS_VECTOR_CHAIN.DROP_LANG_DATA` chunker helper procedure to remove
abbreviation data from the data dictionary.

Syntax

    
    
    DBMS_VECTOR_CHAIN.DROP_LANG_DATA(
        PREF_NAME     IN VARCHAR2
    );

LANG

Specify the name of the language data that you want to drop for a given
language.

Example

    
    
    DBMS_VECTOR_CHAIN.DROP_LANG_DATA('indonesian');

**Parent topic:** [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html "The
DBMS_VECTOR_CHAIN package enables advanced operations with Oracle AI Vector
Search, such as chunking and embedding data along with text generation and
summarization capabilities. It is more suitable for text processing with
similarity search and hybrid search, using functionality that can be pipelined
together for an end-to-end search.")


[← Previous](drop_credential-dbms_vector_chain.md)

[Next →](drop_preference.md)
