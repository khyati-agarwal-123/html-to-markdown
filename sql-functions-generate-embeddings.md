[Previous](understand-stages-data-transformations.html) [Next](pl-sql-packages-generate-embeddings.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Generate Vector Embeddings](generate-vector-embeddings-node.html)
  3. [About Vector Generation](vector-generation.html)
  4. About SQL Functions to Generate Embeddings



## About SQL Functions to Generate Embeddings

Choose to implement Vector Utility SQL functions to perform parallel or on-the-fly chunking and embedding operations, within the database. The supplied SQL functions for vector generation are `VECTOR_CHUNKS` and `VECTOR_EMBEDDING`. 

Vector Utility SQL functions are intended for a direct and quick interaction with data, within pure SQL.

VECTOR_CHUNKS

Use the `VECTOR_CHUNKS` SQL function if you want to split plain text into chunks (pieces of words, sentences, or paragraphs) in preparation for the generation of embeddings, to be used with a vector index. 

For example, you can use this function to build a standalone Text Chunking system that lets you break down a large PDF document into smaller yet semantically meaningful chunk texts. You can experiment with your chunks by running parallel chunking operations, where you can inspect each chunk text, accordingly amend the chunking results, and then proceed further with other data transformation stages.

To generate chunks, this function uses the in-house implementation with Oracle Database. 

For detailed information on this function, see [VECTOR_CHUNKS](vector_chunks.html#GUID-5927E2FA-6419-4744-A7CB-3E62DBB027AD "Use VECTOR_CHUNKS to split plain text into smaller chunks to generate vector embeddings that can be used with vector indexes or hybrid vector indexes."). 

VECTOR_EMBEDDING

Use the `VECTOR_EMBEDDING` function if you want to generate a single vector embedding for different data types. 

For example, you can use this function in information-retrieval applications or chatbots, where you want to generate a query vector on the fly from a user's natural language text input string. You can then query a vector field with this query vector for a fast similarity search.

To generate an embedding, this function uses a vector embedding model (in ONNX format) that you load into the database.

Note:

If you want to generate embeddings by using third-party vector embedding models, then use Vector Utility PL/SQL packages. These packages let you work with both embedding models (in ONNX format) stored in the database and third-party embedding models (by calling third-party REST APIs). 

For detailed information on this function, see [VECTOR_EMBEDDING](vector_embedding.html#GUID-5ED78260-6D21-4B6B-86E0-A1E70EFA11CA "Use VECTOR_EMBEDDING to generate a single vector embedding for different data types using embedding or feature extraction machine learning models."). 

**Related Topics**

  * [Import Pretrained Models in ONNX Format for Vector Generation Within the Database](import-pretrained-models-onnx-format-vector-generation-database.html#GUID-D8140BF9-08E9-4B3F-9E28-E40A6FD181A4 "You can download pretrained embedding machine learning models, convert them into ONNX format if they are not already in ONNX format, import the ONNX format models into Oracle Database, and generate vector embeddings from your data within the database.")
  * [Generate Embeddings](generate-embeddings.html#GUID-813E0E54-9EEF-43FA-A506-1F276D47E7A6 "In these examples, you can see how to use the VECTOR_EMBEDDING SQL function or the UTL_TO_EMBEDDING PL/SQL function to generate a vector embedding from input text strings and images.")



**Parent topic:** [About Vector Generation](vector-generation.html "Learn about Vector Utility SQL functions and Vector Utility PL/SQL packages that help you transform unstructured data into vector embeddings.")

[← Previous](understand-stages-data-transformations.md)

[Next →](pl-sql-packages-generate-embeddings.md)
