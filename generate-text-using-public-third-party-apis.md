[Previous](generate-text.md) [Next](generate-text-locally-ollama.md)
JavaScript must be enabled to correctly display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Work with LLM-Powered APIs and Retrieval Augmentation Generation](work-llm-powered-apis-and-retrieval-augmentation-generation-node.md)
  3. [Use LLM-Powered APIs to Generate Summaries and Text](use-llm-powered-apis-generate-summary-and-text.md)
  4. [Generate Text](generate-text.md)
  5. Generate Text Using Public REST Providers

## Generate Text Using Public REST Providers

Perform a text-to-text transformation, using publicly hosted third-party text
generation models by Cohere, Google AI, Hugging Face, OpenAI, Vertex AI, or
Generative AI. The input is a textual prompt, and the generated output is a
textual answer or description based on the specified task in that prompt.

A prompt can be a text string (such as a question that you ask an LLM or a
command), and can include results from a search.

API used: Here, you can use the `UTL_TO_GENERATE_TEXT` function from either
the `DBMS_VECTOR` or the `DBMS_VECTOR_CHAIN` package, depending on your use
case.

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

To generate text for the prompt "`What is Oracle Text?`", using an external
LLM:

  1. Connect to Oracle Database as a local user.
    1. Log in to SQL*Plus as the `SYS` user, connecting as `SYSDBA`, to your PDB:
        
                conn sys/password@CDB_PDB as sysdba
        
                CREATE TABLESPACE tbs1
        DATAFILE 'tbs5.dbf' SIZE 20G AUTOEXTEND ON
        EXTENT MANAGEMENT LOCAL
        SEGMENT SPACE MANAGEMENT AUTO;

    2. Create a local user (`docuser`) and grant necessary privileges:
        
                DROP USER docuser cascade;
        
                CREATE USER docuser identified by docuser DEFAULT TABLESPACE tbs1 quota unlimited on tbs1;
        
                GRANT DB_DEVELOPER_ROLE, create credential to docuser;

    3. Connect to Oracle Database as `docuser` and alter the environment settings for your session:
        
                CONN docuser/password@CDB_PDB
        
                SET ECHO ON
        SET FEEDBACK 1
        SET NUMWIDTH 10
        SET LINESIZE 80
        SET TRIMSPOOL ON
        SET TAB OFF
        SET PAGESIZE 10000
        SET LONG 10000

  2. Set proxy if exists.

Set the HTTP proxy server, if configured:

    
        EXEC UTL_HTTP.SET_PROXY('<proxy-hostname>:<proxy-port>');

  3. Grant connect privilege to allow connection to the host.

Grant connect privilege to `docuser` for connecting to the host, using the
`DBMS_NETWORK_ACL_ADMIN` procedure. This example uses `*` to allow any host.
However, you can explicitly specify the host that you want to connect to.

    
        BEGIN
      DBMS_NETWORK_ACL_ADMIN.APPEND_HOST_ACE(
        host => '*',
        ace => xs$ace_type(privilege_list => xs$name_list('connect'),
                           principal_name => 'docuser',
                           principal_type => xs_acl.ptype_db));
    END;
    /

  4. Set up credentials and call UTL_TO_GENERATE_TEXT.

Set up your credentials for the REST provider that you want to access and then
call `UTL_TO_GENERATE_TEXT`:

     * Using Cohere, Google AI, Hugging Face, OpenAI, and Vertex AI: 

       1. Call `CREATE_CREDENTIAL` to create and store a credential. 

Cohere, Google AI, Hugging Face, OpenAI, and Vertex AI require the following
authentication parameter:

`{ "access_token": "<access token>" }`

You will later refer to this credential name when declaring JSON parameters
for the `UTL_TO_GENERATE_TEXT` call.

            
                        exec dbms_vector_chain.drop_credential('<credential name>');
            
                        declare
              jo json_object_t;
            begin
              jo := json_object_t();
              jo.put('access_token', '<access token>');
              dbms_vector_chain.create_credential(
                credential_name   => '<credential name>',
                params            => json(jo.to_string));
            end;
            /

Replace the `access_token` and `credential_name` values. For example:

            
                        declare
              jo json_object_t;
            begin
              jo := json_object_t();
              jo.put('access_token', 'AbabA1B123aBc123AbabAb123a1a2ab');
              dbms_vector_chain.create_credential(
                credential_name   => 'HF_CRED',
                params            => json(jo.to_string));
            end;
            /

       2. Call `UTL_TO_GENERATE_TEXT`: 
            
                        -- select example
            
            var params clob;
            exec :params := '
            {
              "provider": "<REST provider>",
              "credential_name": "<credential name>",
              "url": "<REST endpoint URL for text generation service>",
              "model": "<REST provider text generation model name>"
            }';
            
            select dbms_vector_chain.utl_to_generate_text(
             'What is Oracle Text?',json(:params)) from dual;
            
            -- PL/SQL example
            
            declare
              input clob;
              params clob;
              output clob;
            begin
              input := 'What is Oracle Text?';
            
              params := '
            {
              "provider": "<REST provider>",
              "credential_name": "<credential name>",
              "url": "<REST endpoint URL for text generation service>",
              "model": "<REST provider text generation model name>"
            }';
            
              output := dbms_vector_chain.utl_to_generate_text(input, json(params));
              dbms_output.put_line(output);
              if output is not null then
                dbms_lob.freetemporary(output);
              end if;
            exception
              when OTHERS THEN
                DBMS_OUTPUT.PUT_LINE (SQLERRM);
                DBMS_OUTPUT.PUT_LINE (SQLCODE);
            end;
            /

Replace the `provider`, `credential_name`, `url`, and `model` values.
Optionally, you can specify additional REST provider parameters.

Cohere example:

            
                        {
              "provider": "Cohere", 
              "credential_name": "COHERE_CRED",
              "url": "https://api.cohere.example.com/generateText",
              "model": "generate-text-model"
            }

Google AI example:

            
                        {
              "provider": "googleai",
              "credential_name": "GOOGLEAI_CRED",
              "url": "https://googleapis.example.com/models/",
              "model": "generate-text-model"
            }

Hugging Face example:

            
                        {
              "provider": "huggingface",
              "credential_name": "HF_CRED",
              "url": "https://api.huggingface.example.com/models/",
              "model": "generate-text-model"
            }

OpenAI example:

            
                        {
              "provider": "openai",
              "credential_name": "OPENAI_CRED",
              "url": "https://api.openai.example.com",
              "model": "generate-text-model",
              "max_tokens": 60,
              "temperature": 1.0
            }

Vertex AI example:

            
                        {
              "provider": "vertexai",
              "credential_name":"VERTEXAI_CRED",
              "url": "https://googleapis.example.com/models/",
              "model": "generate-text-model",
              "generation_config": {
                "temperature": 0.9,
                "topP": 1,
                "candidateCount": 1,
                "maxOutputTokens": 256
              }
            }

     * Using Generative AI: 

       1. Call `CREATE_CREDENTIAL` to create and store an OCI credential (`OCI_CRED`). 

Generative AI requires the following authentication parameters:

            
                        { 
            "user_ocid": "<user ocid>",
            "tenancy_ocid": "<tenancy ocid>",
            "compartment_ocid": "<compartment ocid>",
            "private_key": "<private key>",
            "fingerprint": "<fingerprint>" 
            }

You will later refer to this credential name when declaring JSON parameters
for the `UTL_TO_GENERATE_TEXT` call.

Note:

The generated private key may appear as:

            
                        -----BEGIN RSA PRIVATE KEY-----
            <private key string>
            -----END RSA PRIVATE KEY-----

You pass the `<private key string>` value (excluding the `BEGIN` and `END`
lines), either as a single line or as multiple lines.

            
                        exec dbms_vector_chain.drop_credential('OCI_CRED');
            
                        declare
              jo json_object_t;
            begin
              jo := json_object_t();
              jo.put('user_ocid','<user ocid>');
              jo.put('tenancy_ocid','<tenancy ocid>');
              jo.put('compartment_ocid','<compartment ocid>');
              jo.put('private_key','<private key>');
              jo.put('fingerprint','<fingerprint>');
              dbms_vector_chain.create_credential(
                credential_name   => 'OCI_CRED',
                params            => json(jo.to_string));
            end;
            /

Replace all the authentication parameter values. For example:

            
                        declare
              jo json_object_t;
            begin
            
              -- create an OCI credential
              jo := json_object_t();
              jo.put('user_ocid','ocid1.user.oc1..aabbalbbaa1112233aabbaabb1111222aa1111bb');
              jo.put('tenancy_ocid','ocid1.tenancy.oc1..aaaaalbbbb1112233aaaabbaa1111222aaa111a');
              jo.put('compartment_ocid','ocid1.compartment.oc1..ababalabab1112233abababab1111222aba11ab');
              jo.put('private_key','AAAaaaBBB11112222333...AAA111AAABBB222aaa1a/+');
              jo.put('fingerprint','01:1a:a1:aa:12:a1:12:1a:ab:12:01:ab:a1:12:ab:1a');
              dbms_vector_chain.create_credential(
                credential_name   => 'OCI_CRED',
                params            => json(jo.to_string));
            end;
            /

       2. Call `UTL_TO_GENERATE_TEXT`: 
            
                        -- select example
            
            var params clob;
            exec :params := '
            {
              "provider": "ocigenai",
              "credential_name": "OCI_CRED",
              "url": "<REST endpoint URL for text generation service>",
              "model": "<REST provider text generation model name>"
            }';
            
            select dbms_vector_chain.utl_to_generate_text(
             'What is Oracle Text?',json(:params)) from dual;
            
            -- PL/SQL example
            
            declare
              input clob;
              params clob;
              output clob;
            begin
              input := 'What is Oracle Text?';
            
              params := '
            {
              "provider": "ocigenai",
              "credential_name": "OCI_CRED",
              "url": "<REST endpoint URL for text generation service>",
              "model": "<REST provider text generation model name>"
            }';
            
              output := dbms_vector_chain.utl_to_generate_text(input, json(params));
              dbms_output.put_line(output);
              if output is not null then
                dbms_lob.freetemporary(output);
              end if;
            exception
              when OTHERS THEN
                DBMS_OUTPUT.PUT_LINE (SQLERRM);
                DBMS_OUTPUT.PUT_LINE (SQLCODE);
            end;
            /

Replace the `url` and `model` values. Optionally, you can specify additional
REST provider-specific parameters.

For example:

            
                        {
              "provider": "OCIGenAI", 
              "credential_name": "GENAI_CRED",
              "url": "https://generativeai.oci.example.com/generateText",
              "model": "generate-text-model",
              "inferenceRequest": {
                "maxTokens": 300,
                "temperature": 1
              }
            }

Example output:

The response to your prompt appears as:

    
        BMS_VECTOR_CHAIN.UTL_TO_GENERATE_TEXT(:INPUT,JSON(:PARAMS))
    --------------------------------------------------------------------------------
    Oracle Text is a powerful tool that enhances Oracle Database with integrated 
    text mining and text analytics capabilities.
    
    It enables users to extract valuable insights and make informed decisions by 
    analyzing unstructured text data stored within the database.
    
    Here are some enhanced capabilities offered by Oracle Text:
    
    1. Full-Text Search: Enables powerful and rapid full-text searches across large
    collections of documents. This helps users find relevant information quickly
    and effectively, even within massive datasets.
    
    2. Natural Language Processing: Implements advanced language processing techn
    iques to analyze text and extract meaningful information. This includes capabilities
    like tokenization, stemming, lemmatization, and part-of-speech tagging, 
    which collectively facilitate efficient text processing and understanding.
    
    3. Sentiment Analysis: Provides a deeper understanding of sentiment expressed
     in text. It enables businesses to automatically analyze customer opinions, feed
    back, and reviews, helping them gain valuable insights into customer sentiment,
    satisfaction levels, and potential trends.
    
    4. Entity Recognition: Automatically identifies and categorizes entities with
    in text, such as names of people, organizations, locations, or any other specific
    terms of interest. This is useful in applications like customer relationship 
    management, where linking relevant information to individuals or organizations is
    crucial.
    
    5. Contextual Analysis: Delivers insights into the context and relationships
    between entities and concepts in textual data. It helps organizations better und
    erstand the broader implications and associations between entities, facilitating
     a deeper understanding of their data.
    
    These features collectively empower various applications, enhancing the function
    ality of the Oracle Database platform to allow businesses and organizations to 
    derive maximum value from their unstructured text data.
    
    Let me know if you'd like to dive deeper into any of these specific capabilities
    , or if there are other aspects of Oracle Text you'd like to explore further.

This example uses the default settings for each provider. For detailed
information on additional parameters, refer to your third-party provider's
documentation.

**Related Topics**

  * [About Chainable Utility Functions and Common Use Cases](chainable-utility-functions-and-common-use-cases.md#GUID-63773EF5-071E-4C02-9EC9-D4E0BA2CE2A2 "These are intended to be a set of chainable and flexible "stages" through which you pass your input data to transform into a different representation, including vectors.")
  * [DBMS_VECTOR Package](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-111D54BC-B2E5-4134-BBE0-ACE0F121B991)
  * [DBMS_VECTOR_CHAIN Package](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-A5B4C9B9-4F94-44E5-817E-FF1A08180C4B)

**Parent topic:** [Generate Text](generate-text.md "In these examples, you
can see how to generate a textual answer, description, or summary based on the
specified task in the prompt.")


[← Previous](generate-text.md)

[Next →](generate-text-locally-ollama.md)
