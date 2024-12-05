[Previous](generate-text-using-public-third-party-apis.html) [Next](describe-image-content.html) JavaScript must be enabled to correctly display this
content

  1. [AI Vector Search User's Guide](index.html)2. [Work with LLM-Powered APIs and Retrieval Augmented Generation](work-llm-powered-apis-and-retrieval-augmented-generation-node.html)
  3. [Use LLM-Powered APIs to Generate Summary and Text](use-llm-powered-apis-generate-summary-and-text.html)4. [Generate Text Response](generate-text-response.html)
  5. Generate Text Using the Local REST Provider Ollama

## Generate Text Using the Local REST Provider Ollama

Perform a text-to-text transformation by accessing open LLMs, using the local
host REST endpoint provider Ollama. The input is a textual prompt, and the
generated output is a textual answer or description based on the specified
task in that prompt.

A prompt can be a text string (such as a question that you ask an LLM or a
command), and can include results from a search.

Ollama is a free and open-source command-line interface tool that allows you
to run open LLMs (such as Llama 3, Phi 3, Mistral, or Gemma 2) locally and
privately on your Linux, Windows, or macOS systems. You can access Ollama as a
service using SQL and PL/SQL commands.

Here, you can use the `UTL_TO_GENERATE_TEXT` function from either the
`DBMS_VECTOR` or the `DBMS_VECTOR_CHAIN` package, depending on your use case.

WARNING:

Certain features of the database may allow you to access services offered
separately by third-parties, for example, through the use of JSON
specifications that facilitate your access to REST APIs.

Your use of these features is solely at your own risk, and you are solely
responsible for complying with any terms and conditions related to use of any
such third-party services. Notwithstanding any other terms and conditions
related to the third-party services, your use of such database features
constitutes your acceptance of that risk and express exclusion of Oracle's
responsibility or liability for any damages resulting from such access.

To generate a descriptive answer for the prompt "`What is Oracle Text?`", by
calling a local LLM using Ollama:

  1. Connect to Oracle Database as a local user.
    1. Log in to SQL*Plus as the `SYS` user, connecting as `SYSDBA`:
        
                conn sys/password as sysdba
        
                CREATE TABLESPACE tbs1
        DATAFILE 'tbs5.dbf' SIZE 20G AUTOEXTEND ON
        EXTENT MANAGEMENT LOCAL
        SEGMENT SPACE MANAGEMENT AUTO;
        
                SET ECHO ON
        SET FEEDBACK 1
        SET NUMWIDTH 10
        SET LINESIZE 80
        SET TRIMSPOOL ON
        SET TAB OFF
        SET PAGESIZE 10000
        SET LONG 10000

    2. Create a local user (`docuser`) and grant necessary privileges:
        
                DROP USER docuser cascade;
        
                CREATE USER docuser identified by docuser DEFAULT TABLESPACE tbs1 quota unlimited on tbs1;
        
                GRANT DB_DEVELOPER_ROLE, create credential to docuser;

    3. Connect as the local user (`docuser`):
        
                CONN docuser/password

  2. Install Ollama and run a model locally.
    1. Download and run the Ollama application from <https://ollama.com/download>.

You can either install Ollama as a service that runs in the background or as a
standalone binary with a manual install. For detailed installation-specific
steps, see Quick Start in the [Ollama
Documentation](https://github.com/ollama/ollama/tree/main/docs).

Note the following:

       * The Ollama server needs to be able to connect to the internet so that it can download the models. If you require a proxy server to access the internet, remember to set the appropriate environment variables before running the Ollama server. For example, to set for Linux: 
            
                        -- set a proxy if you require one
            
            export https_proxy=<proxy-hostname>:<proxy-port>
            export http_proxy=<proxy-hostname>:<proxy-port>
            export no_proxy=localhost,127.0.0.1,.example.com
            export ftp_proxy=<proxy-hostname>:<proxy-port>

       * If you are running Ollama and the database on different machines, then on the database machine, you must change the `URL` to refer to the host name or IP address that is running Ollama instead of the local host. 

       * You may need to change your firewall settings on the machine that is running Ollama to allow the port through.

    2. If running Ollama as a standalone binary from a manual install, then start the server:
        
                ollama serve

    3. Run a model using the `ollama run <model_name>` command.

For example, to call the Llama 3 model:

        
                ollama run llama3

For detailed information on this step, see [Ollama
Readme](https://github.com/ollama/ollama/blob/main/README.md#quickstart).

    4. Verify that Ollama is running locally by using a cURL command.

For example:

        
                -- generate text
        
        curl -X POST http://localhost:11434/api/generate -d '{
          "model" : "llama3",
          "prompt": "Why is the sky blue?",
          "stream": false }'

  3. Set the HTTP proxy server, if configured.
    
        EXEC UTL_HTTP.SET_PROXY('<proxy-hostname>:<proxy-port>');

  4. Grant connect privilege to `docuser` for allowing connection to the host, using the `DBMS_NETWORK_ACL_ADMIN` procedure.

This example uses `*` to allow any host. However, you can explicitly specify
the host that you want to connect to.

    
        BEGIN
      DBMS_NETWORK_ACL_ADMIN.APPEND_HOST_ACE(
        host => '*',
        ace => xs$ace_type(privilege_list => xs$name_list('connect'),
                           principal_name => 'docuser',
                           principal_type => xs_acl.ptype_db));
    END;
    /

  5. Call `UTL_TO_GENERATE_TEXT`.

The Ollama service has a REST API endpoint for generating text. Specify the
URL and other configuration parameters in a JSON object.

    
        var gent_ollama_params clob;
    exec :gent_ollama_params := '{
       "provider": "ollama",
       "host"    : "local",
       "url"     : "http://localhost:11434/api/generate", 
       "model"   : "llama3"
    }';
    
    select dbms_vector.utl_to_generate_text('What is Oracle Text?', json(:gent_ollama_params)) from dual;

You can replace the `url` and `model` with your own values, as required.

Note:

For a complete list of all supported REST endpoint URLs, see [Supported Third-
Party Provider Operations and Endpoints](supported-third-party-provider-
operations-and-endpoints.html#GUID-BE3EE403-CD10-4708-A15F-EFB1FA69DF09
"Review a list of third-party REST providers and REST endpoints that are
supported for various vector generation, summarization, text generation, and
reranking operations.").

The response to your prompt may appear as:

    
        Oracle Text (formerly known as Oracle InterMedia) is a suite of text search and retrieval tools within Oracle Database. It allows you to index and query 
    unstructured text data, such as documents, emails, and other text-based content.
    
    With Oracle Text, you can:
    
    1. Index text: Create indexes on text columns or external files, making it possible to efficiently search and retrieve relevant text data.
    2. Query text: Use SQL syntax to query the indexed text data, allowing you to find specific words, phrases, or patterns within large volumes of 
    text.
    3. Full-text search: Perform full-text searches on unstructured text data, returning relevant results based on keyword matches, proximity, and 
    relevance.
    
    Oracle Text supports various indexing schemes, including:
    
    1. Basic Indexing: A simple, fast index for searching exact keywords.
    2. Phrase Indexing: An index that allows you to search for phrases (e.g., "John Smith").
    3. Thesaurus Indexing: An index that enables searches based on synonyms and related words.
    
    Oracle Text also includes various text analysis and processing features, such as:
    
    1. Tokenization: Breaking down text into individual words or tokens.
    2. Stemming: Reducing words to their base form (e.g., "running" becomes "run").
    3. Stopword removal: Eliminating common words like "the," "and," and "a" that don't add much value to the search.
    
    Oracle Text is particularly useful in scenarios where you need to search, analyze, or retrieve unstructured text data, such as:
    
    1. Content management: Searching and retrieving documents, articles, or other content.
    2. Email archiving: Indexing and searching email messages.
    3. Search engines: Building custom search solutions for specific domains or industries.
    
    In summary, Oracle Text is a powerful tool within the Oracle Database that enables you to index, query, and retrieve unstructured text data with ease.

**Related Topics**

  * [UTL_TO_GENERATE_TEXT](utl_to_generate_text-dbms_vector.html#GUID-EA78DFB6-D951-43D1-8ECB-DD6D21C6F6A6 "Use the DBMS_VECTOR.UTL_TO_GENERATE_TEXT chainable utility function to generate a text response for a given prompt or an image, by accessing third-party text generation models.")
  * [DBMS_VECTOR](dbms_vector-vecse.html#GUID-829230F9-BD1E-41F9-BAAB-5D3C3E52FC12 "The DBMS_VECTOR package simplifies common operations with Oracle AI Vector Search, such as extracting chunks or embeddings from user data, generating text for a given prompt or an image, creating a vector index, or reporting on index accuracy.")
  * [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html#GUID-A09FF69E-FCCB-4EDA-B7E4-B02A11359504 "The DBMS_VECTOR_CHAIN package enables advanced operations with Oracle AI Vector Search, such as chunking and embedding data along with text generation and summarization capabilities. It is more suitable for text processing with similarity search and hybrid search, using functionality that can be pipelined together for an end-to-end search.")

**Parent topic:** [Generate Text Response](generate-text-response.html "In
these examples, you can see how to generate a textual answer, description, or
summary based on the specified task in a given prompt.")


[← Previous](generate-text-using-public-third-party-apis.md)

[Next →](describe-image-content.md)
