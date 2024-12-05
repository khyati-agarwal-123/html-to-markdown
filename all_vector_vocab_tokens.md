[Previous](all_vector_vocab.html) [Next](vector-memory-pool-views.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Diagnostics](vector-diagnostics-node.html)
  3. [Oracle AI Vector Search Views](oracle-ai-vector-search-views.html)4. [Text Processing Views](text-processing-views.html)
  5. ALL_VECTOR_VOCAB_TOKENS



## ALL_VECTOR_VOCAB_TOKENS

The `ALL_VECTOR_VOCAB_TOKENS` view displays tokens from all custom token vocabularies. 

Column Name | Data Type | Description  
---|---|---  
VOCAB_OWNER | VARCHAR2(128) | Owner of the vocabulary (for example, SYS)  
VOCAB_NAME | VARCHAR2(128) | User-specified name of the vocabulary (for example, DOC_VOCAB)  
VOCAB_TOKEN | VARCHAR2(255) | Tokens contained in the vocabulary  
  
**Parent topic:** [Text Processing Views](text-processing-views.html "These views display language-specific data \(abbreviation token details\) and vocabulary data related to the Oracle AI Vector Search SQL and PL/SQL utilities.")

[← Previous](all_vector_vocab.md)

[Next →](vector-memory-pool-views.md)
