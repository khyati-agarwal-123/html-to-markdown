[Previous](why-use-vector-search-instead-other-vector-databases.html)[Next](get-started-node.html) JavaScript must be enabled to correctly display
this content

  1. [AI Vector Search User's Guide](index.html)2. [Overview](overview-node.html)
  3. Oracle AI Vector Search Workflow

## Oracle AI Vector Search Workflow

A typical Oracle AI Vector Search workflow follows the included primary steps.

This is illustrated in the following diagram:

Figure 2-2 Oracle AI Vector Search Use Case Flowchart

  

![Description of Figure 2-2
follows](https://docs.oracle.com/en/database/oracle/oracle-database/23/vecse/img/23_6_ai_vector_workflow.png)[Description of "Figure 2-2 Oracle AI Vector Search Use Case
Flowchart"](https://docs.oracle.com/en/database/oracle/oracle-
database/23/vecse/img_text/23_6_ai_vector_workflow.html)

  

Note:

Find all of our Interactive Architecture Diagrams on the [Oracle Help
Center](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-
database/23/vecse&id=aliad_home).

Oracle AI Vector Search is designed for Artificial Intelligence (AI)
workloads. It allows you to query data based on semantics rather than
keywords. The preceding diagram shows the possible steps you must take to
manage vector embeddings with Oracle AI Vector Search.

Primary workflow steps:

  1. Generate Vector Embeddings from Your Unstructured Data

You can perform this step either outside or within Oracle Database. To perform
this step inside Oracle Database, you must first import a vector embedding
model using the ONNX standard. Your unstructured data can reside within or
outside Oracle Database.

For more information, see [Generate Vector Embeddings](generate-vector-
embeddings-node.html#GUID-A788574C-F88D-4E5E-B220-A40FA8CBB174 "Oracle AI
Vector Search offers Vector Utilities \(SQL and PL/SQL tools\) to
automatically generate vector embeddings from your unstructured data, either
within or outside Oracle Database.").

  2. Store Vector Embeddings, Unstructured Data, and Relational Business Data in Oracle Database

After you have generated the vector embeddings, you can store them along with
the corresponding unstructured and relational business data. If vector
embeddings are stored outside Oracle Database, you can use SQL*Loader or Data
Pump to load the vector embedding inside a relational table within Oracle
Database.

For more information, see [Store Vector Embeddings](store-vector-
embeddings.html#GUID-DF5E5492-2E9E-4C38-838D-56567BEC17C1 "Store vector
embeddings and associated unstructured data with your relational business data
in Oracle Database.").

  3. Create Vector Indexes and Hybrid Vector Indexes

Similar to how you create indexes on regular table columns, you can create
vector indexes on vector embeddings, and you can create hybrid vector indexes
(a combination of Oracle Text index and vector index) on your unstructured
data. This is beneficial for running similarity searches over huge vector
spaces.

For more information, see [Create Vector Indexes and Hybrid Vector
Indexes](create-vector-indexes-and-hybrid-vector-
indexes.html#GUID-8AF956F3-D951-4968-9B79-A6E180E87456 "Depending on whether
to use similarity search or hybrid search, you can create either a vector
index or a hybrid vector index.").

  4. Query Data with Similarity and Hybrid Searches

You can then use Oracle AI Vector Search native SQL operations to combine
similarity with traditional relational key searches. In addition, you can run
hybrid searches, an advanced information retrieval technique that combines
both the similarity and keyword searches to achieve highly relevant search
results. SQL and PL/SQL provide powerful utilities to transform unstructured
data, such as documents, into chunks before generating vector embeddings on
each chunk.

For more information, see [Query Data With Similarity and Hybrid
Searches](query-data-similarity-and-hybrid-
searches.html#GUID-1085EF0C-D1CA-423F-A6F2-54A9E76BAAA5 "Use Oracle AI Vector
Search native SQL operations from your development environment to combine
similarity with relational searches.") and [Supported Clients and
Languages](supported-clients-and-languages.html#GUID-
BAD95D81-BD27-4122-A5B6-7B4807EDD63B "For more information about Oracle AI
Vector Search support using some of Oracle's available clients and languages,
see the included reference material.").

  5. Generate a Prompt and Send it to an LLM for a Full RAG Inference

You can use vector utility PL/SQL APIs for prompting large language models
(LLMs) with textual prompts and images using LLM-powered interfaces. LLMs
inherently lack the ability to access or incorporate new information after
their training cutoff. By providing your LLM with up-to-date facts from your
company, you can minimize the probability that an LLM will make up answers
(hallucinate). Retrieval Augmented Generation (RAG) is an approach developed
to address the limitations of LLMs. RAG combines the strengths of pretrained
language models, including reranking ones, with the ability to retrieve
information from a dataset or database in real time during the generation of
responses. Oracle AI Vector Search enables RAG and LLM integration using
popular frameworks like LangChain, Ollama, and LlamaIndex.

For more information, see [Work with LLM-Powered APIs and Retrieval Augmented
Generation](work-llm-powered-apis-and-retrieval-augmented-generation-
node.html#GUID-AF82CA2B-5B40-4B05-AD1E-E990A4C1BF86 "You can use Vector
Utility PL/SQL APIs for prompting Large Language Models \(LLMs\) with textual
prompts and images, using LLM-powered interfaces. You can also communicate
with LLMs through the implementation of Retrieval Augmented Generation
\(RAG\), which helps to generate more accurate and informative responses.").

**Parent topic:** [Overview](overview-node.html "Oracle AI Vector Search
stores and indexes vector embeddings for fast retrieval and similarity
search.")


[← Previous](why-use-vector-search-instead-other-vector-databases.md)

[Next →](get-started-node.md)
