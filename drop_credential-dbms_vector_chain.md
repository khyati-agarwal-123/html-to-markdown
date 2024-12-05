[Previous](create_vocabulary.html) [Next](drop_lang_data.html) JavaScript must
be enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html)
  4. DROP_CREDENTIAL

## DROP_CREDENTIAL

Use the `DBMS_VECTOR_CHAIN.DROP_CREDENTIAL` credential helper procedure to
drop an existing credential name from the data dictionary.

Syntax

    
    
    DBMS_VECTOR_CHAIN.DROP_CREDENTIAL (
        CREDENTIAL_NAME      IN VARCHAR2
    );

CREDENTIAL_NAME

Specify the credential name that you want to drop.

Examples

  * For Generative AI:
    
        exec dbms_vector_chain.drop_credential('OCI_CRED');

  * For Cohere:
    
        exec dbms_vector_chain.drop_credential('COHERE_CRED');

**Parent topic:** [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html "The
DBMS_VECTOR_CHAIN package enables advanced operations with Oracle AI Vector
Search, such as chunking and embedding data along with text generation and
summarization capabilities. It is more suitable for text processing with
similarity search and hybrid search, using functionality that can be pipelined
together for an end-to-end search.")


[← Previous](create_vocabulary.md)

[Next →](drop_lang_data.md)
