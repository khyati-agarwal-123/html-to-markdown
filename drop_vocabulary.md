[Previous](drop_preference.html) [Next](rerank-dbms_vector_chain.html)
JavaScript must be enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html)
  4. DROP_VOCABULARY

## DROP_VOCABULARY

Use the `DBMS_VECTOR_CHAIN.DROP_VOCABULARY` chunker helper procedure to remove
vocabulary data from the data dictionary.

Syntax

    
    
    DBMS_VECTOR_CHAIN.DROP_VOCABULARY(
        VOCABULARY_NAME    IN VARCHAR2   
    );

VOCAB_NAME

Specify the name of the vocabulary that you want to drop, in the form:

`vocabulary_name`

or

`owner.vocabulary_name`

Example

    
    
    DBMS_VECTOR_CHAIN.DROP_VOCABULARY('MY_VOCAB_1');

**Parent topic:** [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html "The
DBMS_VECTOR_CHAIN package enables advanced operations with Oracle AI Vector
Search, such as chunking and embedding data along with text generation and
summarization capabilities. It is more suitable for text processing with
similarity search and hybrid search, using functionality that can be pipelined
together for an end-to-end search.")


[← Previous](drop_preference.md)

[Next →](rerank-dbms_vector_chain.md)
