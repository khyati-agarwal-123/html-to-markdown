[Previous](supplied-vector-utility-pl-sql-packages.md) [Next](terms-using-
vector-utility-pl-sql-packages.md) JavaScript must be enabled to correctly
display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Generate Vector Embeddings](generate-vector-embeddings-node.md)
  3. [About Vector Generation](vector-generation.md)
  4. [About PL/SQL Packages to Generate Embeddings](pl-sql-packages-generate-embeddings.md)
  5. Supported Third-Party Provider Operations

## Supported Third-Party Provider Operations

Review a list of both the public and local, third-party REST providers that
are supported for vector generation, summarization, and text generation
operations.

Public or Remote REST Endpoint Providers

The supported publicly-hosted third-party REST endpoint providers are:

  * Cohere

  * Google AI

  * Hugging Face

  * Oracle Cloud Infrastructure (OCI) Generative AI

  * OpenAI

  * Vertex AI

Local REST Endpoint Provider

You can use Ollama as a third-party REST endpoint provider, locally and
privately on your Linux, Windows, and macOS systems.

Ollama is a free and open-source command-line interface tool that allows you
to run open LLMs, such as Llama 3, Phi 3, Mistral, and Gemma 2. You can access
Ollama using SQL and PL/SQL commands.

You can download and install Ollama on your local host as a service that runs
in the background, from <https://ollama.com/download>. For detailed
installation-specific steps, see [Ollama
Documentation](https://github.com/ollama/ollama/tree/main/docs).

REST Operations

The corresponding operations allowed for both public and local third-party
REST providers are:

Operation | Detailed Information  
---|---  
`UTL_TO_EMBEDDING` and `UTL_TO_EMBEDDINGS` to generate one or more embeddings  | 

  * [DBMS_VECTOR.UTL_TO_EMBEDDING and DBMS_VECTOR.UTL_TO_EMBEDDINGS](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-8E615832-F6C0-4435-8F43-3FAF80692D5B)
  * [DBMS_VECTOR_CHAIN.UTL_TO_EMBEDDING and DBMS_VECTOR_CHAIN.UTL_TO_EMBEDDINGS](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-C6439E94-4E86-4ECD-954E-4B73D53579DE)

  
`UTL_TO_SUMMARY` to generate summaries  | 

  * [DBMS_VECTOR_CHAIN.UTL_TO_SUMMARY](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-EC9DDB58-6A15-4B36-BA66-ECBA20D2CE57)

  
`UTL_TO_GENERATE_TEXT` to generate text for prompts  | 

  * [DBMS_VECTOR.UTL_TO_GENERATE_TEXT](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-EA78DFB6-D951-43D1-8ECB-DD6D21C6F6A6)
  * [DBMS_VECTOR_CHAIN.UTL_TO_GENERATE_TEXT](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-017C9002-194C-48E5-B59B-EF5C60BC8405)

  
  
**Parent topic:** [About PL/SQL Packages to Generate Embeddings](pl-sql-
packages-generate-embeddings.md "Choose to implement Vector Utility PL/SQL
packages to perform chunking, embedding, and text generation operations along
with text processing and similarity search, both within and outside the
database. The supplied PL/SQL packages for vector generation are DBMS_VECTOR
and DBMS_VECTOR_CHAIN.")


[← Previous](supplied-vector-utility-pl-sql-packages.md)

[Next →](terms-using-vector-utility-pl-sql-packages.md)
