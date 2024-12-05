[Previous](oracle-ai-vector-search-parameters.html) [Next](dbms_vector-vecse.html) JavaScript must be enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)
  2. Vector Search PL/SQL Packages

## 12 Vector Search PL/SQL Packages

The `DBMS_VECTOR`, `DBMS_VECTOR_CHAIN`, and `DBMS_HYBRID_VECTOR` PL/SQL APIs
are available to support Oracle AI Vector Search capabilities.

  * [DBMS_VECTOR](dbms_vector-vecse.html)  
The `DBMS_VECTOR` package simplifies common operations with Oracle AI Vector
Search, such as extracting chunks or embeddings from user data, generating
text for a given prompt or an image, creating a vector index, or reporting on
index accuracy.

  * [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html)  
The `DBMS_VECTOR_CHAIN` package enables advanced operations with Oracle AI
Vector Search, such as chunking and embedding data along with text generation
and summarization capabilities. It is more suitable for text processing with
similarity search and hybrid search, using functionality that can be pipelined
together for an end-to-end search.

  * [DBMS_HYBRID_VECTOR](dbms_hybrid_vector-vecse.html)  
The `DBMS_HYBRID_VECTOR` package contains a JSON-based query API `SEARCH`,
which lets you query against hybrid vector indexes.


[← Previous](oracle-ai-vector-search-parameters.md)

[Next →](dbms_vector-vecse.md)
