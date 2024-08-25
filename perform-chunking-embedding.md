[Previous](convert-text-string-embedding-locally-ollama.md) [Next](convert-
text-chunks-custom-chunking-specifications.md) JavaScript must be enabled to
correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Generate Vector Embeddings](generate-vector-embeddings-node.md)
  3. [Vector Generation Examples](vector-generation-examples.md)
  4. Perform Chunking With Embedding

## Perform Chunking With Embedding

In these examples, you can see how to split text data (such as text strings
and full documents) into meaningful chunks and then represent each chunk as a
vector embedding.

Chunking prepares your unstructured data to ensure that it is in a format that
can be processed by vector embedding models.

  * [Convert Text to Chunks With Custom Chunking Specifications](convert-text-chunks-custom-chunking-specifications.md)  
A chunked output, especially for long and complex documents, sometimes loses
contextual meaning or coherence with its parent content. In this example, you
can see how to refine your chunks by applying custom chunking specifications.

  * [Convert File to Text to Chunks to Embeddings Within Oracle Database](convert-file-text-chunks-embeddings-oracle-database.md)  
First convert a PDF file to text, split the text into chunks, and then create
vector embeddings on each chunk by accessing a vector embedding model stored
in the database.

  * [Convert File to Embeddings Within Oracle Database](convert-file-embeddings-oracle-database.md)  
Directly extract vector embeddings from a PDF document, using a single-step
statement, by accessing a vector embedding model stored in the database.

  * [Generate and Use Embeddings for an End-to-End Search](generate-and-use-embeddings-end-end-search.md)  
First generate vector embeddings from textual content by using a vector
embedding model stored in the database, and then populate and query a vector
index. At query time, you also vectorize the query criteria on the fly.

**Parent topic:** [Vector Generation Examples](vector-generation-examples.md
"Run these end-to-end examples to see how you can generate vector embeddings,
both within and outside the database.")


[← Previous](convert-text-string-embedding-locally-ollama.md)

[Next →](convert-text-chunks-custom-chunking-specifications.md)
