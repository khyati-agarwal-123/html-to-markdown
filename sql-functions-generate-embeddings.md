[Previous](understand-stages-data-transformations.md) [Next](pl-sql-
packages-generate-embeddings.md) JavaScript must be enabled to correctly
display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Generate Vector Embeddings](generate-vector-embeddings-node.md)
  3. [About Vector Generation](vector-generation.md)
  4. About SQL Functions to Generate Embeddings

## About SQL Functions to Generate Embeddings

Choose to implement Vector Utility SQL functions to perform parallel or on-
the-fly chunking and embedding operations, within the database. The supplied
SQL functions for vector generation are `VECTOR_CHUNKS` and
`VECTOR_EMBEDDING`.

Vector Utility SQL functions are intended for a direct and quick interaction
with data, within pure SQL.

VECTOR_CHUNKS

Use the `VECTOR_CHUNKS` SQL function if you want to split plain text into
chunks (pieces of words, sentences, or paragraphs) in preparation for the
generation of embeddings, to be used with a vector index.

For example, you can use this function to build a standalone Text Chunking
system that lets you break down a large PDF document into smaller yet
semantically meaningful chunk texts. You can experiment with your chunks by
running parallel chunking operations, where you can inspect each chunk text,
accordingly amend the chunking results, and then proceed further with other
data transformation stages.

To generate chunks, this function uses the in-house implementation with Oracle
Database.

For detailed information on this function, see [VECTOR_CHUNKS](vector_chunks-
vecse.md#GUID-73AF607D-4ADF-4324-96D1-891971E96100 "VECTOR_CHUNKS lets you
split plain text into chunks \(pieces of words, sentences, or paragraphs\) in
preparation for the generation of vector embeddings, to be used with a vector
index.").

VECTOR_EMBEDDING

Use the `VECTOR_EMBEDDING` function if you want to generate a single vector
embedding for different data types.

For example, you can use this function in information-retrieval applications
or chatbots, where you want to generate a query vector on the fly from a
user's natural language text input string. You can then query a vector field
with this query vector for a fast similarity search.

To generate an embedding, this function uses a vector embedding model (in ONNX
format) that you load into the database.

Note:

If you want to generate embeddings by using third-party vector embedding
models, then use Vector Utility PL/SQL packages. These packages let you work
with both embedding models (in ONNX format) stored in the database and third-
party embedding models (by calling third-party REST APIs).

For detailed information on this function, see
[VECTOR_EMBEDDING](vector_embedding-
vecse.md#GUID-11F89242-3789-4A19-B5E0-DB0838B071F8 "Use VECTOR_EMBEDDING if
you want to generate a single vector embedding for different data types.").

**Related Topics**

  * [Import Pretrained Models in ONNX Format for Vector Generation Within the Database](import-pretrained-models-onnx-format-vector-generation-database.md#GUID-D8140BF9-08E9-4B3F-9E28-E40A6FD181A4 "You can download pretrained embedding machine learning models, convert them into ONNX format if they are not already in ONNX format, import the ONNX format models into Oracle Database, and generate vector embeddings from your data within the database.")
  * [Generate Embeddings](generate-embeddings.md#GUID-813E0E54-9EEF-43FA-A506-1F276D47E7A6 "In these examples, you can see how to generate one or more vector embeddings from an input text string.")

**Parent topic:** [About Vector Generation](vector-generation.md "Learn
about Vector Utility SQL functions and Vector Utility PL/SQL packages that
help you transform unstructured data into vector embeddings.")


[← Previous](understand-stages-data-transformations.md)

[Next →](pl-sql-packages-generate-embeddings.md)
