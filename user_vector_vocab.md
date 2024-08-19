[Previous](user_vector_lang.md) [Next](user_vector_vocab_tokens.md)
JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Vector Diagnostics](vector-diagnostics-node.md)
  3. [Oracle AI Vector Search Views](oracle-ai-vector-search-views.md)
  4. [Vector Utilities-Related Views](vector-utilities-related-views.md)
  5. USER_VECTOR_VOCAB

## USER_VECTOR_VOCAB

The `USER_VECTOR_VOCAB` view displays all custom token vocabularies created by
the current user.

Column Name | Data Type | Description  
---|---|---  
`VOCAB_NAME` |  `VARCHAR2(128)` |  User-specified name of the vocabulary (for example, `DOC_VOCAB`)   
`FORMAT` |  `VARCHAR2(4)` |  Format of the vocabulary, such as `XLM`, `BERT`, or `GPT2`  
`CASED` |  `VARCHAR2(7)` |  Character-casing of the vocabulary, that is, vocabulary to be treated as cased or uncased  
  
**Parent topic:** [Vector Utilities-Related Views](vector-utilities-related-
views.md "These views display language-specific data \(abbreviation token
details\) and vocabulary data related to the Oracle AI Vector Search SQL and
PL/SQL utilities.")


[← Previous](user_vector_lang.md)

[Next →](user_vector_vocab_tokens.md)
