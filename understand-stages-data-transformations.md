[Previous](vector-generation.md) [Next](sql-functions-generate-
embeddings.md) JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Generate Vector Embeddings](generate-vector-embeddings-node.md)
  3. [About Vector Generation](vector-generation.md)
  4. Understand the Stages of Data Transformations

## Understand the Stages of Data Transformations

Your input data may travel through different stages before turning into a
vector.

For example, you may first transform textual data (such as a PDF document)
into plain text, then break the resulting text into smaller pieces of text
(chunks) to finally create vector embeddings on each chunk.

As shown in the following diagram, input data passes through a pipeline of
optional stages from Text to Chunks to Tokens to Vectors, with Vector Index as
the endpoint:

![Description of dbms_vector_utilities_stages.eps
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/dbms_vector_utilities_stages.jpg)  
[Description of the illustration
dbms_vector_utilities_stages.eps](img_text/dbms_vector_utilities_stages.md)

Prepare: Text and Chunks

This stage prepares your unstructured data to ensure that it is in a format
that can be processed by vector embedding models.

To prepare large unstructured textual data (for example, a PDF or Word
document), you first transform the data into plain text and then pass the
resulting text through the Chunker. The chunker then splits the text into
smaller chunks using a process known as **chunking**. A single document may be
split into many chunks, each transformed into a vector.

**Chunks** are pieces of words (to capture specific words or word pieces),
sentences (to capture a specific meaning), or paragraphs (to capture broader
themes). Later, you will learn about several chunking parameters and
techniques to define so that each chunk contains relevant and meaningful
context.

Embed: Tokens and Vectors

You now pass the extracted chunks as input to the Model (declared vector
embedding model) for generating vector embeddings on each chunk. This stage
makes these chunks searchable.

The chunks are first passed through the Tokenizer of the model to split into
words or word pieces, known as **tokens**. The model then embeds each token
into a vector representation.

Tokenizers used by embedding models frequently have limits on the size of the
input text they can deal with, so chunking is needed to avoid loss of text
when generating embeddings. If input text is larger than the maximum input
limit imposed by the model, then the text gets truncated unless it is split up
into appropriate-sized segments or chunks. Chunking is not needed for smaller
documents, text strings, or summarized texts that meet this maximum input
limit.

The chunker must select a text size that approximates the maximum input limit
of your model. The actual number of tokens depends on the specified tokenizer
for the model, which typically uses a **vocabulary** list of words, numbers,
punctuations, and pieces of tokens.

A vocabulary contains a set of tokens that are collected during a statistical
training process. Each tokenizer uses a different vocabulary format to process
text into tokens, that is, the BERT multilingual model uses Word-Piece
encoding and the GPT model uses Byte-Pair encoding.

For example, the BERT model tokenizes the following four words:

`Embedding usecase for chunking`

as the following eight tokens and also includes `##` (number signs) to
indicate non-initial pieces of words:

`Em ##bedd ##ing use ##case for chunk ##ing`

Vocabulary files are included as part of a model's distribution. You can
supply a vocabulary file (recognized by your model's tokenizer) to the chunker
beforehand, so that it can correctly estimate the token count of your input
data when chunking.

Populate and Query: Vector Indexes

Finally, you store the semantic content of your input data as vectors in the
Vector Index. You can now implement combined similarity and relational queries
to retrieve relevant results using the extracted vectors.

**Parent topic:** [About Vector Generation](vector-generation.md "Learn
about Vector Utility SQL functions and Vector Utility PL/SQL packages that
help you transform unstructured data into vector embeddings.")


[← Previous](vector-generation.md)

[Next →](sql-functions-generate-embeddings.md)
