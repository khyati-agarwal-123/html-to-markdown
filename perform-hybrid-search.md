[Previous](perform-multi-vector-similarity-search.html) [Next](understand-hybrid-search.html) JavaScript must be enabled to correctly display this
content

  1. [AI Vector Search User's Guide](index.html)2. [Query Data With Similarity and Hybrid Searches](query-data-similarity-and-hybrid-searches.html)
  3. Perform Hybrid Search

## Perform Hybrid Search

Hybrid search is an advanced information retrieval technique that lets you
search documents by keywords and vectors, to achieve more relevant search
results.

  * [Understand Hybrid Search](understand-hybrid-search.html)  
With hybrid search, you can search through your documents by performing a
combination of full-text queries and vector-based similarity queries, using
out-of-the-box or custom scoring techniques.

  * [Query Hybrid Vector Indexes End-to-End Example](query-hybrid-vector-indexes-end-end-example.html)  
In this example, you can see an end-to-end hybrid search workflow. First, you
run the `CREATE HYBRID VECTOR INDEX` SQL statement that prepares, chunks,
embeds, stores, and indexes your input data. You then perform vector search
alongside keyword search using the `DBMS_HYBRID_VECTOR.SEARCH` PL/SQL query
API.

**Parent topic:** [Query Data With Similarity and Hybrid Searches](query-data-
similarity-and-hybrid-searches.html "Use Oracle AI Vector Search native SQL
operations from your development environment to combine similarity with
relational searches.")


[← Previous](perform-multi-vector-similarity-search.md)

[Next →](understand-hybrid-search.md)
