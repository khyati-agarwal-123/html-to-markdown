[Previous](supported-third-party-provider-operations-and-endpoints.html)[Next](vector-diagnostics-node.html) JavaScript must be enabled to correctly
display this content

  1. [AI Vector Search User's Guide](index.html)
  2. Supported Clients and Languages

## 10 Supported Clients and Languages

For more information about Oracle AI Vector Search support using some of
Oracle's available clients and languages, see the included reference material.

Clients and Languages | Reference Material  
---|---  
PL/SQL | Oracle Database PL/SQL Language Reference  
MLE JavaScript | Oracle Database JavaScript Developer's Guide  
JDBC | Oracle Database JDBC Developerâs Guide  
Node.js | node-oracledb documentation  
Python | python-oracledb documentation  
Oracle Call Interface | Oracle Call Interface Developer's Guide  
ODP.NET | Oracle Data Provider for .NET Developer's Guide  
SQL*Plus | SQL*Plus User's Guide and Reference  
  
Oracle Database 23ai supports binding with native VECTOR types for all Oracle
clients. Applications that use earlier Oracle Client 23ai libraries can
connect to Oracle Database 23ai in the following ways:

  * Using the `TO_VECTOR()` SQL function to insert vector data, as shown in the following example: 
    
        INSERT INTO vecTab VALUES(TO_VECTOR('[1.1, 2.9, 3.14]'));

  * Using the `FROM_VECTOR()` SQL function to fetch vector data, as shown in the following example:
    
        SELECT FROM_VECTOR(dataVec) FROM vecTab;


[← Previous](supported-third-party-provider-operations-and-endpoints.md)

[Next →](vector-diagnostics-node.md)
