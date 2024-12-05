[Previous](create-and-use-custom-vocabulary.html) [Next](store-vector-embeddings.html) JavaScript must be enabled to correctly display this content

  1. [AI Vector Search User's Guide](index.html)2. [Generate Vector Embeddings](generate-vector-embeddings-node.html)
  3. [Vector Generation Examples](vector-generation-examples.html)4. [Configure Chunking Parameters](configure-chunking-parameters.html)
  5. Create and Use Custom Language Data

## Create and Use Custom Language Data

Create and use your own language-specific conditions (such as common
abbreviations) when chunking data.

Here, you use the chunker helper function `CREATE_LANG_DATA` from the
`DBMS_VECTOR_CHAIN` package to load the data file for Simplified Chinese. This
data file contains abbreviation tokens for your chosen language.

  1. Connect as a local user and prepare your data dump directory.
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
        
                drop user docuser cascade;
        
                create user docuser identified by docuser DEFAULT TABLESPACE tbs1 quota unlimited on tbs1;
        
                grant DB_DEVELOPER_ROLE to docuser;

    3. Create a local directory (`VEC_DUMP`) to store your language data file. Grant necessary privileges:
        
                create or replace directory VEC_DUMP as '/my_local_dir/';
        
                grant read, write on directory VEC_DUMP to docuser;
        
        commit;

    4. Transfer the data file for your required language to the `VEC_DUMP` directory. For example, `dreoszhs.txt` for Simplified Chinese.

To know the data file location for your language, see [Supported Languages and
Data File Locations](supported-languages-and-data-file-
locations.html#GUID-8C8AAE2F-E64A-470F-B109-BE1AC2D6E498 "These are the
supported languages for which language data files are distributed by default
in the specified directories.").

    5. Connect as the local user (`docuser`):
        
                conn docuser/password

  2. Create a relational table (`doc_langtab`) to store your abbreviation tokens in it:
    
        CREATE TABLE doc_langtab(token nvarchar2(64))
      ORGANIZATION EXTERNAL
      (default directory VEC_DUMP
       ACCESS PARAMETERS (RECORDS DELIMITED BY NEWLINE CHARACTERSET AL32UTF8)
       location ('dreoszhs.txt'));

  3. Create language data (`doc_lang_data`) by calling `DBMS_VECTOR_CHAIN.CREATE_LANG_DATA`:
    
        DECLARE
      lang_params clob := '{
                             "table_name"      : "doc_langtab",
                             "column_name"     : "token",
                             "language"        : "simplified chinese",
                             "preference_name" : "doc_lang_data"
                           }';
    BEGIN
      dbms_vector_chain.create_lang_data(json(lang_params));
    END;
    /

After loading the language data, you can now use language-specific chunking by
specifying the `LANGUAGE` chunking parameter with `VECTOR_CHUNKS` or
`UTL_TO_CHUNKS`.

**Related Topics**

  * [CREATE_LANG_DATA](create_lang_data.html#GUID-C9756FA9-B0B6-4750-8D9C-ADEF8B67C675 "Use the DBMS_VECTOR_CHAIN.CREATE_LANG_DATA chunker helper procedure to load your own language data file into the database.")
  * [VECTOR_CHUNKS](vector_chunks.html#GUID-5927E2FA-6419-4744-A7CB-3E62DBB027AD "Use VECTOR_CHUNKS to split plain text into smaller chunks to generate vector embeddings that can be used with vector indexes or hybrid vector indexes.")
  * [UTL_TO_CHUNKS](utl_to_chunks-dbms_vector_chain.html#GUID-4E145629-7098-4C7C-804F-FC85D1F24240 "Use the DBMS_VECTOR_CHAIN.UTL_TO_CHUNKS chainable utility function to split a large plain text document into smaller chunks of text.")

**Parent topic:** [Configure Chunking Parameters](configure-chunking-
parameters.html "Oracle AI Vector Search provides many parameters for chunking
text data, such as SPLIT \[BY\], OVERLAP, or NORMALIZE. In these examples, you
can see how to configure these parameters to define your own chunking
specifications and strategies, so that you can create meaningful chunks.")


[← Previous](create-and-use-custom-vocabulary.md)

[Next →](store-vector-embeddings.md)
