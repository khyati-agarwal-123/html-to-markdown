[Previous](vector-utilities-related-views.md) [Next](all_vector_lang.md)
JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Vector Diagnostics](vector-diagnostics-node.md)
  3. [Oracle AI Vector Search Views](oracle-ai-vector-search-views.md)
  4. [Vector Utilities-Related Views](vector-utilities-related-views.md)
  5. ALL_VECTOR_ABBREV_TOKENS

## ALL_VECTOR_ABBREV_TOKENS

The `ALL_VECTOR_ABBREV_TOKENS` view displays a list of abbreviation tokens
from all supported languages.

Column Name | Data Type | Description  
---|---|---  
`ABBREV_OWNER` |  `VARCHAR2(128)` |  Owner of the abbreviation token (for example, `PUBLIC`)   
`ABBREV_LANGUAGE` |  `NUMBER` |  Language ID for the language (for example, `1` for American)   
`ABBREV_TOKEN` |  `NVARCHAR2(255)` |  List of all abbreviation tokens corresponding to each language  
  
**Parent topic:** [Vector Utilities-Related Views](vector-utilities-related-
views.md "These views display language-specific data \(abbreviation token
details\) and vocabulary data related to the Oracle AI Vector Search SQL and
PL/SQL utilities.")


[← Previous](vector-utilities-related-views.md)

[Next →](all_vector_lang.md)
