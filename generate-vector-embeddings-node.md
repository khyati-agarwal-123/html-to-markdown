[Previous](sql-quick-start-using-binary-vector-generator.md) [Next](vector-
generation.md) JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. Generate Vector Embeddings

## 4 Generate Vector Embeddings

Oracle AI Vector Search offers Vector Utilities (SQL and PL/SQL tools) to
automatically generate vector embeddings from your unstructured data, either
within or outside Oracle Database.

Embeddings are vector representations that capture the semantic meaning of
your data (as explained in [Overview of Oracle AI Vector Search](overview-ai-
vector-search.md#GUID-746EAA47-9ADA-4A77-82BB-64E8EF5309BE "Oracle AI Vector
Search is designed for Artificial Intelligence \(AI\) workloads and allows you
to query data based on semantics, rather than keywords.")). A vector embedding
model creates embeddings by assigning numerical values to each element of your
data, such as a word, sentence, or paragraph.

To generate embeddings within the database, you can import and use vector
embedding models in ONNX format. To generate embeddings outside the database,
you can access third-party vector embedding models (remotely or locally) by
calling third-party REST APIs.

  * [About Vector Generation](vector-generation.md)  
Learn about Vector Utility SQL functions and Vector Utility PL/SQL packages
that help you transform unstructured data into vector embeddings.

  * [Import Pretrained Models in ONNX Format for Vector Generation Within the Database](import-pretrained-models-onnx-format-vector-generation-database.md)  
You can download pretrained embedding machine learning models, convert them
into ONNX format if they are not already in ONNX format, import the ONNX
format models into Oracle Database, and generate vector embeddings from your
data within the database.

  * [Access Third-Party Models for Vector Generation Leveraging Third-Party REST APIs](access-third-party-models-vector-generation-leveraging-third-party-rest-apis.md)  
You can access third-party vector embedding models to generate vector
embeddings from your data, outside the database by calling third-party REST
APIs.

  * [Vector Generation Examples](vector-generation-examples.md)  
Run these end-to-end examples to see how you can generate vector embeddings,
both within and outside the database.


[← Previous](sql-quick-start-using-binary-vector-generator.md)

[Next →](vector-generation.md)
