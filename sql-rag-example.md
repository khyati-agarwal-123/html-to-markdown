[Previous](retrieval-augmented-generation1.md) [Next](supported-clients-and-
languages.md) JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Work with LLM-Powered APIs and Retrieval Augmentation Generation](work-llm-powered-apis-and-retrieval-augmentation-generation-node.md)
  3. [Use Retrieval Augmented Generation to Complement LLMs](use-retrieval-augmented-generation-complement-llms.md)
  4. SQL RAG Example

## SQL RAG Example

This scenario allows you to run a similarity search for specific documentation
content based on a user query. Once documentation chunks are retrieved, they
are concatenated and a prompt is generated to ask an LLM to answer the user
question using retrieved chunks.

  1. Start SQL*Plus and connect to Oracle Database as a local test user.
    1. Log in to SQL*Plus as the `sys` user, connecting as `sysdba`:
        
                conn sys/password AS sysdba
        
                SET SERVEROUTPUT ON;
        SET ECHO ON;
        SET LONG 100000;

    2. Create a local test user (`vector`) and grant necessary privileges:
        
                DROP USER vector cascade;
        
                CREATE USER vector identified by <my vector password>
        
                GRANT DB_DEVELOPER_ROLE, CREATE CREDENTIAL TO vector;

    3. Set the proxy if one exists:
        
                EXEC UTL_HTTP.SET_PROXY('<my proxy full name>:<my proxy port>');

    4. Grant connect privilege for a host using the `DBMS_NETWORK_ACL_ADMIN` procedure. This example uses `*` to allow any host. However, you can explicitly specify each host that you want to connect to.
        
                BEGIN
          DBMS_NETWORK_ACL_ADMIN.APPEND_HOST_ACE(
            host => '*',
            ace => xs$ace_type(privilege_list => xs$name_list('connect'),
                               principal_name => 'VECTOR',
                               principal_type => xs_acl.ptype_db));
        END;
        /

    5. Connect to Oracle Database as the test user.
        
                conn docuser/password;

  2. Create a credential for Oracle Cloud Infrastructure Generative AI:

    1. Run `DBMS_VECTOR_CHAIN.CREATE_CREDENTIAL` to create and store an OCI credential (`OCI_CRED`). 

OCIGenAI requires the following parameters:

        
                { 
        "user_ocid": "<user ocid>",
        "tenancy_ocid": "<tenancy ocid>",
        "compartment_ocid": "<compartment ocid>",
        "private_key": "<private key>",
        "fingerprint": "<fingerprint>" 
        }

Note:

The generated private key may appear as:

        
                -----BEGIN RSA PRIVATE KEY-----
        <private key string>
        -----END RSA PRIVATE KEY-----

You pass the `<private key string>` value (excluding the `BEGIN` and `END`
lines), either as a single line or as multiple lines.

        
                BEGIN
          DBMS_VECTOR_CHAIN.DROP_CREDENTIAL(credential_name => 'OCI_CRED');
        EXCEPTION
          WHEN OTHERS THEN NULL;
        END;
        /
        
                DECLARE
          jo json_object_t;
        BEGIN
          jo := json_object_t();
          jo.put('user_ocid', '<user ocid>');
          jo.put('tenancy_ocid', '<tenancy ocid>');
          jo.put('compartment_ocid', '<compartment ocid>');
          jo.put('private_key', '<private key>');
          jo.put('fingerprint', '<fingerprint>');
          DBMS_VECTOR_CHAIN.CREATE_CREDENTIAL(
            credential_name => 'OCID_CRED',
            params          => json(jo.to_string));
        END;
        /

    2. Check credential creation:
        
                col owner format a15
        col credential_name format a20
        col username format a20
        
                SELECT owner, credential_name, username
        FROM all_credentials
        ORDER BY owner, credential_name, username;

  3. Generate a prompt using similarity search results:

Note:

For information about loading the ONNX format model into the database as
`doc_model`, see [Import ONNX Models into Oracle Database End-to-End
Example](import-onnx-models-oracle-database-end-end-
example.md#GUID-6AEA7A0E-78E0-4083-A126-4516EB98175A "Learn to import a
pretrained embedding model that is in ONNX format and generate vector
embeddings.").

    
        SET SERVEROUTPUT ON;
    
    VAR prompt CLOB;
    VAR user_question CLOB;
    VAR context CLOB;
    
    BEGIN
      -- initialize the concatenated string
      :context := '';
    
      -- read this question from the user
      :user_question := 'what are vector indexes?';
    
      -- cursor to fetch chunks relevant to the user's query
      FOR rec IN (SELECT EMBED_DATA
                  FROM doc_chunks
                  WHERE DOC_ID = 'Vector User Guide'
                  ORDER BY vector_distance(embed_vector, vector_embedding(
                      doc_model using :user_question as input), COSINE)
                  FETCH EXACT FIRST 10 ROWS ONLY)
      LOOP
        -- concatenate each value to the string
        :context := :context || rec.embed_data;
      END LOOP;
    
      -- concatenate strings and format it as an enhanced prompt to the LLM
      :prompt := 'Answer the following question using the supplied context 
                    assuming you are a subject matter expert. Question: '
                    || :user_question || ' Context: ' || :context;
    
      DBMS_OUTPUT.PUT_LINE('Generated prompt: ' || :prompt);
    END;
    /

  4. Issue the GenAI call:
    
        DECLARE
      input CLOB;
      params CLOB;
      output CLOB;
    BEGIN
      input := :prompt;
      params := '{
        "provider" : "ocigenai",
        "credential_name" : "OCI_CRED",
        "url" : "https://inference.generativeai.us-chicago-1.oci.
                oraclecloud.com/20231130/actions/generateText",
        "model" : "cohere.command"
      }';
    
      output := DBMS_VECTOR_CHAIN.UTL_TO_GENERATE_TEXT(input, json(params));
      DBMS_OUTPUT.PUT_LINE(output);
      IF output IS NOT NULL THEN
        DBMS_LOB.FREETEMPORARY(output);
      END IF;
    EXCEPTION
      WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE(SQLERRM);
        DBMS_OUTPUT.PUT_LINE(SQLCODE);
    END;
    /

**Parent topic:** [Use Retrieval Augmented Generation to Complement LLMs](use-
retrieval-augmented-generation-complement-llms.md "RAG lets you mitigate the
inaccuracies and hallucinations faced when using LLMs. Oracle AI Vector Search
enables RAG within Oracle Database using the DBMS_VECTOR_CHAIN PL/SQL package
or through popular frameworks \(such as LangChain\).")


[← Previous](retrieval-augmented-generation1.md)

[Next →](supported-clients-and-languages.md)
