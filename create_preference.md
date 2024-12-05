[Previous](create_lang_data.html) [Next](create_vocabulary.html) JavaScript must be enabled to correctly display this content 

  1. [AI Vector Search User's Guide](index.html)2. [Vector Search PL/SQL Packages](vector-search-pl-sql-packages-node.html)
  3. [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html)
  4. CREATE_PREFERENCE



## CREATE_PREFERENCE

Use the `DBMS_VECTOR_CHAIN.CREATE_PREFERENCE` preference helper procedure to create a vectorizer preference, to be used when creating or updating hybrid vector indexes. 

Purpose

To create a vectorizer preference. 

This allows you to customize vector search parameters of a hybrid vector indexing pipeline. The goal of a vectorizer preference is to provide you with a straightforward way to configure how to chunk or embed your documents, without requiring a deep understanding of various chunking or embedding strategies.

Usage Notes

A **vectorizer** preference is a JSON object that collectively holds user-specified values related to the following chunking, embedding, or vector index creation parameters: 

  * Chunking (`UTL_TO_CHUNKS` and `VECTOR_CHUNKS`) 

  * Embedding (`UTL_TO_EMBEDDING`, `UTL_TO_EMBEDDINGS`, and `VECTOR_EMBEDDING`) 

  * Vector index creation (`distance`, `accuracy`, and `vector_idxtype`) 




All vector index preferences follow the same JSON syntax as defined for their corresponding `DBMS_VECTOR` and `DBMS_VECTOR_CHAIN` APIs. 

After creating a vectorizer preference, you can use the `VECTORIZER` parameter to pass this preference name in the `paramstring` of the `PARAMETERS` clause for `CREATE_HYBRID_VECTOR_INDEX` and `ALTER_INDEX` SQL statements. 

Creating a preference is optional. If you do not specify any optional preference, then the index is created with system defaults.

Syntax
    
    
    DBMS_VECTOR_CHAIN.CREATE_PREFERENCE (
        PREF_NAME     IN VARCHAR2,
        PREF_TYPE     IN VARCHAR2,
        PARAMS        IN JSON default NULL
    );

PREF_NAME

Specify the name of the vectorizer preference to create.

PREF_TYPE

Type of preference. The only supported preference type is: 

`DBMS_VECTOR_CHAIN.VECTORIZER`

PARAMS

Specify vector search-specific parameters in JSON format:

  * [Embedding Parameter](create_preference.html#GUID-B83978CD-EAF8-4794-9652-F335C54C3385__P_JBQ_3NF_GDC)* [Chunking Parameters](create_preference.html#GUID-B83978CD-EAF8-4794-9652-F335C54C3385__P_VF1_JNF_GDC)

  * [Vector Index Parameters](create_preference.html#GUID-B83978CD-EAF8-4794-9652-F335C54C3385__P_WVP_JNF_GDC)




Embedding Parameter: 
    
    
    { "model" : <embedding_model_for_vector_generation> }

For example:
    
    
    { "model" : MY_INDB_MODEL }

`model` specifies the name under which your ONNX embedding model is stored in the database. 

If you do not have an in-database embedding model in ONNX format, then perform the steps listed in [Oracle Database AI Vector Search User's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=VECSE-GUID-E7C08BA2-B2B9-4081-9050-B9EB3EA46FA6). 

Chunking Parameters: 
    
    
    {
        "by"           :  mode,
        "max"          :  max,
        "overlap"      :  overlap,
        "split"        :  split_condition,
        "vocabulary"   :  vocabulary_name,
        "language"     :  nls_language,
        "normalize"    :  normalize_mode,
        "extended"     :  boolean
    }

For example:
    
    
    JSON(
     '{ "by"           :    "vocabulary",
        "max"          :    "100",
        "overlap"      :    "0",
        "split"        :    "none",
        "vocabulary"   :    "myvocab",
        "language"     :    "american",
        "normalize"    :    "all" 
      }')

If you specify `split` as `custom` and `normalize` as `options`, then you must additionally specify the `custom_list` and `norm_options` parameters, respectively: 
    
    
    JSON(
     '{ "by"           :    "vocabulary",
        "max"          :    "100",
        "overlap"      :    "0",
        "split"        :    "custom",
        "custom_list"  :    [ "<p>" , "<s>" ],
        "vocabulary"   :    "myvocab",
        "language"     :    "american",
        "normalize"    :    "options",
        "norm_options" :    [ "whitespace" ] 
      }')

The following table describes all the chunking parameters:

Parameter | Description and Acceptable Values  
---|---  
by | Specify a mode for splitting your data, that is, to split by counting the number of characters, words, or vocabulary tokens. Valid values: characters (or chars): Splits by counting the number of characters. words: Splits by counting the number of words. Words are defined as sequences of alphabetic characters, sequences of digits, individual punctuation marks, or symbols. For segmented languages without whitespace word boundaries (such as Chinese, Japanese, or Thai), each native character is considered a word (that is, unigram). vocabulary: Splits by counting the number of vocabulary tokens. Vocabulary tokens are words or word pieces, recognized by the vocabulary of the tokenizer that your embedding model uses. You can load your vocabulary file using the chunker helper API DBMS_VECTOR_CHAIN.CREATE_VOCABULARY. Note: For accurate results, ensure that the chosen model matches the vocabulary file used for chunking. If you are not using a vocabulary file, then ensure that the input length is defined within the token limits of your model. Default value: words  
max | Specify a limit on the maximum size of each chunk. This setting splits the input text at a fixed point where the maximum limit occurs in the larger text. The units of max correspond to the by mode, that is, to split data when it reaches the maximum size limit of a certain number of characters, words, numbers, punctuation marks, or vocabulary tokens. Valid values: by characters: 50 to 4000 characters by words: 10 to 1000 words by vocabulary: 10 to 1000 tokens Default value: 100  
split [by] | Specify where to split the input text when it reaches the maximum size limit. This helps to keep related data together by defining appropriate boundaries for chunks. Valid values: none: Splits at the max limit of characters, words, or vocabulary tokens. newline, blankline, and space: These are single-split character conditions that split at the last split character before the max value. Use newline to split at the end of a line of text. Use blankline to split at the end of a blank line (sequence of characters, such as two newlines). Use space to split at the end of a blank space. recursively: This is a multiple-split character condition that breaks the input text using an ordered list of characters (or sequences). recursively is predefined as BLANKLINE, newline, space, none in this order: 1. If the input text is more than the max value, then split by the first split character. 2. If that fails, then split by the second split character. 3. And so on. 4. If no split characters exist, then split by max wherever it appears in the text. sentence: This is an end-of-sentence split condition that breaks the input text at a sentence boundary. This condition automatically determines sentence boundaries by using knowledge of the input language's sentence punctuation and contextual rules. This language-specific condition relies mostly on end-of-sentence (EOS) punctuations and common abbreviations. Contextual rules are based on word information, so this condition is only valid when splitting the text by words or vocabulary (not by characters). Note: This condition obeys the by word and max settings, and thus may not determine accurate sentence boundaries in some cases. For example, when a sentence is larger than the max value, it splits the sentence at max. Similarly, it includes multiple sentences in the text only when they fit within the max limit. custom: Splits based on a custom split characters list. You can provide custom sequences up to a limit of 16 split character strings, with a maximum length of 10 each. Specify an array of valid text literals using the custom_list parameter. { "split" : "custom", "custom_list" : [ "split_chars1", ... ] }For example:{ "split" : "custom", "custom_list" : [ "<p>" , "<s>" ] }Note: You can omit sequences only for tab (\t), newline (\n), and linefeed (\r). Default value: recursively  
overlap | Specify the amount (as a positive integer literal or zero) of the preceding text that the chunk should contain, if any. This helps in logically splitting up related text (such as a sentence) by including some amount of the preceding chunk text. The amount of overlap depends on how the maximum size of the chunk is measured (in characters, words, or vocabulary tokens). The overlap begins at the specified split condition (for example, at newline). Valid value: 5% to 20% of max Default value: 0  
language | Specify the language of your input data. This clause is important, especially when your text contains certain characters (for example, punctuations or abbreviations) that may be interpreted differently in another language. Valid values: NLS-supported language name or its abbreviation, as listed in Oracle Database Globalization Support Guide. Custom language name or its abbreviation, as listed in Supported Languages and Data File Locations. You use the DBMS_VECTOR_CHAIN.CREATE_LANG_DATA chunker helper API to load language-specific data (abbreviation tokens) into the database, for your specified language. Default value: NLS_LANGUAGE from session  
normalize | Automatically pre-processes or post-processes issues (such as multiple consecutive spaces and smart quotes) that may arise when documents are converted into text. Oracle recommends you to use a normalization mode to extract high-quality chunks. Valid values: none: Applies no normalization. all: Normalizes common multi-byte (unicode) punctuation to standard single-byte. options: Specify an array of normalization options using the norm_options parameter. { "normalize" : "options", "norm_options" : [ "normalize_option1", ... ] } punctuation: Converts quotes, dashes, and other punctuation characters supported in the character set of the text to their common ASCII form. For example: U+2013 (En Dash) maps to U+002D (Hyphen-Minus) U+2018 (Left Single Quotation Mark) maps to U+0027 (Apostrophe) U+2019 (Right Single Quotation Mark) maps to U+0027 (Apostrophe) U+201B (Single High-Reversed-9 Quotation Mark) maps to U+0027 (Apostrophe) whitespace: Minimizes whitespace by eliminating unnecessary characters. For example, retain blanklines, but remove any extra newlines and interspersed spaces or tabs: " \n \n " => "\n\n" widechar: Normalizes wide, multi-byte digits and (a-z) letters to single-byte. These are multi-byte equivalents for 0-9 and a-z A-Z, which can show up in Chinese, Japanese, or Korean text. For example:{ "normalize" : "options", "norm_options" : [ "whitespace" ] } Default value: none  
extended | Increases the output limit of a VARCHAR2 string to 32767 bytes, without requiring you to set the max_string_size parameter to extended. Default value: 4000 or 32767 (when max_string_size=extended)  
  
Vector Index Parameters: 
    
    
    { 
      "distance"        :  <vector_distance>,
      "accuracy"        :  <vector_accuracy>, 
      "vector_idxtype"  :  <vector_idxtype>
    }

For example:
    
    
    { 
      "distance"        :  COSINE,
      "accuracy"        :  95, 
      "vector_idxtype"  :  HNSW
    }

Parameter | Description  
---|---  
distance | Distance metric or mathematical function used to compute the distance between vectors: COSINE MANHATTAN DOT EUCLIDEAN L2_SQUARED EUCLIDEAN_SQUARED Note: Currently, the HAMMING and JACCARD vector distance metrics are not supported with hybrid vector indexes. For detailed information on each of these metrics, see Vector Distance Functions and Operators. Default value: COSINE  
accuracy | Target accuracy at which the approximate search should be performed when running an approximate search query using vector indexes. As explained in Understand Approximate Similarity Search Using Vector Indexes, you can specify non-default target accuracy values either by specifying a percentage value or by specifying internal parameters values, depending on the index type you are using. For a Hierarchical Navigable Small World (HNSW) approximate search: In the case of an HNSW approximate search, you can specify a target accuracy percentage value to influence the number of candidates considered to probe the search. This is automatically calculated by the algorithm. A value of 100 will tend to impose a similar result as an exact search, although the system may still use the index and will not perform an exact search. The optimizer may choose to still use an index as it may be faster to do so given the predicates in the query. Instead of specifying a target accuracy percentage value, you can specify the EFSEARCH parameter to impose a certain maximum number of candidates to be considered while probing the index. The higher that number, the higher the accuracy. For detailed information, see Understand Hierarchical Navigable Small World Indexes. For an Inverted File Flat (IVF) approximate search: In the case of an IVF approximate search, you can specify a target accuracy percentage value to influence the number of partitions used to probe the search. This is automatically calculated by the algorithm. A value of 100 will tend to impose an exact search, although the system may still use the index and will not perform an exact search. The optimizer may choose to still use an index as it may be faster to do so given the predicates in the query. Instead of specifying a target accuracy percentage value, you can specify the NEIGHBOR PARTITION PROBES parameter to impose a certain maximum number of partitions to be probed by the search. The higher that number, the higher the accuracy. For detailed information, see Understand Inverted File Flat Vector Indexes. Valid range for both HNSW and IVF vector indexes is: > 0 and <= 100 Default value: None  
vector_idxtype | Type of vector index to create: HNSW for an HNSW vector index IVF for an IVF vector index For detailed information on each of these index types, see Manage the Different Categories of Vector Indexes. Default value: IVF  
  
Example
    
    
    begin
      DBMS_VECTOR_CHAIN.CREATE_PREFERENCE(
        'my_vec_spec',
         DBMS_VECTOR_CHAIN.VECTORIZER,
         json('{ "vector_idxtype" :  "hnsw",
                 "model"          :  "my_doc_model",
                 "by"             :  "words",
                 "max"            :  100,
                 "overlap"        :  10,
                 "split"          :  "recursively,
                 "language"       :  "american" }'));
    end;
    /
    
    CREATE HYBRID VECTOR INDEX my_hybrid_idx on 
        doc_table(text_column) 
        parameters('VECTORIZER my_vec_spec');

**Related Topics**

  * [CREATE HYBRID VECTOR INDEX](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=CCREF-GUID-22B07106-419E-4C55-B4E1-3FD691E033BC)**Parent topic:** [DBMS_VECTOR_CHAIN](dbms_vector_chain-vecse.html "The DBMS_VECTOR_CHAIN package enables advanced operations with Oracle AI Vector Search, such as chunking and embedding data along with text generation and summarization capabilities. It is more suitable for text processing with similarity search and hybrid search, using functionality that can be pipelined together for an end-to-end search.")

[← Previous](create_lang_data.md)

[Next →](create_vocabulary.md)
