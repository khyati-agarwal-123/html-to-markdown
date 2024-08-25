[Previous](load-binary-vector-data-using-sqlloader-example.md)
[Next](create-vector-indexes.md) JavaScript must be enabled to correctly
display this content

  1. [Oracle AI Vector Search User's Guide](index.md)
  2. [Store Vector Embeddings](store-vector-embeddings-01.md)
  3. Unload and Load Vectors Using Oracle Data Pump

## Unload and Load Vectors Using Oracle Data Pump

Starting with Oracle Database 23ai, Oracle Data Pump enables you to use
multiple components to load and unload vectors to databases.

Oracle Data Pump technology enables very high-speed movement of data and
metadata from one database to another. Oracle Data Pump is made up of three
distinct components: Command-line clients, expdp and impdp; the DBMS_DATAPUMP
PL/SQL package (also known as the Data Pump API); and the DBMS_METADATA PL/SQL
package (also known as the Metadata API).

Unloading and Loading a table with vector datatype columns is supported in all
modes (`FULL`, `SCHEMA`, `TABLES`) using all the available access methods
(`DIRECT_PATH`,` EXTERNAL_TABLE`, `AUTOMATIC`, `INSERT_AS_SELECT`).

Examples Vector Export and Import Syntax

    
    
    expdp <username>/<password>@<Database-instance-TNS-alias>  dumpfile=<dumpfile-name>.dmp directory=<directory-name> full=y metrics=y access_method=direct_path
    
    expdp <username>/<password>@<Database-instance-TNS-alias>  dumpfile=<dumpfile-name>.dmp directory=<directory-name> schemas=<schema-name> metrics=y access_method=external_table
    
    expdp <username>/<password>@<Database-instance-TNS-alias>  dumpfile=<dumpfile-name>.dmp directory=<directory-name> tables=<schema-name>.<table-name> metrics=y access_method=direct_path
    
    impdp <username>/<password>@<Database-instance-TNS-alias>  dumpfile=<dumpfile-name>.dmp directory=<directory-name> metrics=y access_method=direct_path

Note:

  * `TABLE_EXISTS_ACTION=APPEND | TRUNCATE` can only be used with the `EXTERNAL_TABLE` access method. 
  * `TABLE_EXISTS_ACTION=APPEND | TRUNCATE` can load `VECTOR` column data into a `VARCHAR2` column if the conversion can fit into that `VARCHAR2`. 
  * `TABLE_EXISTS_ACTION=APPEND | TRUNCATE` can only load a `VECTOR` column with the source `VECTOR` data dimasion that matches that loaded `VECTOR` column's dimension. If the dimension does not match, then an error is raised. 
  * `TABLE_EXISTS_ACTION=REPLACE` supports any access method. 
  * It is not possible to use a the transportable tablespace mode with vector indexes. However, this mode supports tables with the `VECTOR` datatype. 

**Related Topics**

  * [Overview of Oracle Data Pump](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=SUTIL-GUID-17FAE261-0972-4220-A2E4-44D479F519D4)
  * [DBMS_DATAPUMP](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-AEA7ED80-DB4A-4A70-B199-592287206348)
  * [DBMS_METADATA](/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23/vecse&id=ARPLS-GUID-F72B5833-C14E-4713-A588-6BDF4D4CBA2A)

**Parent topic:** [Store Vector Embeddings](store-vector-embeddings-01.md
"You store the resulting vector embeddings and associated unstructured data
with your relational business data in Oracle Database.")


[← Previous](load-binary-vector-data-using-sqlloader-example.md)

[Next →](create-vector-indexes.md)
