---
description: "Learn more about: Data Provider for  Informix"
title: "Data Provider for  Informix"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Data Provider for  Informix
## Platform Compatibility  
  
### Code Page Conversions  
 The Data Provider supports a combination of single byte character sets (SBCS), mixed-byte character sets (MBCS) double-byte character sets (DBCS), and Unicode - UTF8 [1208], which is an 8-bit Unicode transformation format.  
  
#### Host CCSID  
 The Data Provider requires a value for Host CCSID (Coded Character Set Identifier) with which to perform code page conversions on string data. The default Host CCSID value is Unicode - UTF8 [1208]. Typically, IBM Informix database servers utilize Unicode.  
  
#### PC Code Page  
 The Data Provider requires a value for PC Code Page with which to perform code page conversions on string data. The default PC code page is Unicode - UTF8 [1208]. Typically, IBM Informix database servers utilize Unicode.  
  
#### Process Binary as Character  
 The Data Provider automatically converts to and from binary (CCSID 65535) and character string data types, based on the Informix data type and Windows consumer data type. The Informix encoding is determined by the Host CCSID. The Windows encoding is determined by the PC Code Page.  
  
### Data Type Mapping  
 This topic describes all data type mappings to OLE DB data types.  
  
#### Informix to OLE DB Data Type Mapping  
 The following table describes Informix data type mappings to OLE DB data types.  
  
|OLE DB data type|Informix data type|Description|  
|-|-|-|  
|DBTYPE_I8|bigint|A big integer is an 8-byte binary integer.|  
|DBTYPE_UI8|bigserial|An unsigned 8-byte binary integer.|  
|DBTYPE_Bytes|blob|A binary large object is a varying-length string used to store non-textual or binary data.|  
|DBTYPE_BOOL|boolean|A boolean is a single byte binary to store a true or false value.|  
|DBTYPE_Bytes|byte|A binary large object is a varying-length string used to store non-textual or binary data.|  
|DBTYPE_STR|char|A character is a fixed-length SBCS or MBCS string.|  
|DBTYPE_STR|clob|A varying-length character large object is a varying-length string.|  
|DBTYPE_DBDate|date|A date is a 10-byte string.|  
|DBTYPE_DBTimesStamp|datetime|A timestamp is a 32-byte string representing the date, time, and microseconds.|  
|DBTYPE_Decimal|decimal|A decimal number.|  
|DBTYPE_R8|float|A float is an 8-byte double-precision floating point number.|  
|DBTYPE_I8|int8|An integer 8 is an 8-byte binary integer.|  
|DBTYPE_I4|integer|An integer is a 4-byte binary integer.|  
|DBTYPE_DBTimesStamp|interval|A timestamp is a 32-byte string representing the date, time, and microseconds.|  
|DBTYPE_STR|lvarchar|A varying character is a varying-length character string.|  
|DBTYPE_WSTR|nchar|A fixed-length Unicode string.|  
|DBTYPE_WSTR|nvarchar|A varying-length Unicode string.|  
|DBTYPE_R4|real|A float is a 4-byte double-precision floating point number.|  
|DBTYPE_UI4|serial|An unsigned 4-byte binary integer.|  
|DBTYPE_UI8|serial8|An unsigned 8-byte binary integer.|  
|DBTYPE_R4|smallfloat|A real is a 4-byte single-precision floating point number.|  
|DBTYPE_I2|smallint|A two-byte binary integer.|  
|DBTYPE_STR|text|A varying-length character large object is a varying-length string.|  
|DBTYPE_STR|varchar|A varying character is a varying-length character string.|  
  
 Schema information in OLE DB is retrieved using predefined schema rowsets with IDBSchemaRowset::GetRowset. The Data Provider exposed the PROVIDER_TYPES Rowset to indicate the Informix to OLE DB data type support (types, mappings, limits), based on the IBM Informix version.  
  
#### Informix V11  
 The Data Provider supports accessing these data types when connected to Informix V11.  
  
|Informix Type_name|OLE DB data_type|Column_size|Minimum_scale|Maximum_scale|  
|-|-|-|-|-|  
|BIGINT|DBTYPE_I8|20|||  
|INT8|DBTYPE_I8|20|||  
|SERIAL8|DBTYPE_UI8|20|||  
|BIGSERIAL|DBTYPE_UI8|20|||  
|BOOLEAN|DBTYPE_BOOL|1|||  
|BYTE|DBTYPE_BYTES|2147483647|||  
|BLOB|DBTYPE_BYTES|2147483647|||  
|CHAR|DBTYPE_STR|32767|||  
|TEXT|DBTYPE_STR|2147483647|||  
|CLOB|DBTYPE_STR|2147483647|||  
|DATE|DBTYPE_DBDATE|10|||  
|DECIMAL|DBTYPE_DECIMAL|32|0|32|  
|FLOAT|DBTYPE_R8|53|||  
|NCHAR|DBTYPE_WSTR|32767|||  
|INTEGER|DBTYPE_I4|10|||  
|SERIAL|DBTYPE_UI4|10|||  
|SMALLFLOAT|DBTYPE_R4|24|||  
|REAL|DBTYPE_R4|24|||  
|SMALLINT|DBTYPE_I2|5|||  
|DATETIME|DBTYPE_DBTIMESTAMP|32|0|12|  
|INTERVAL|DBTYPE_DBTIMESTAMP|32|0|12|  
|VARCHAR|DBTYPE_STR|255|||  
|LVARCHAR|DBTYPE_STR|32739|||  
|NVARCHAR|DBTYPE_WSTR|255|||  
  
## Performance  
 This topic contains the following sections that will help you maximize performance when you are using the Data Provider for Informix.  
  
 [Configuring for Performance](../core/data-provider-for-informix1.md#configForPerformance)  
  
 [Measuring Performance](../core/data-provider-for-informix1.md#measuringPerformance)  
  
###  <a name="configForPerformance"></a> Configuring for Performance  
 To improve performance, configure the providers in the following ways.  
  
#### Pool provider resources to reduce connection startup time  
 Connection Pooling is a client-side optimization that reduces connection startup time, while reducing memory utilization on the client computer. The OLE DB provider supports connection pooling. You can specify pooling using the OLE DB data source initialization string (Connection Pooling=True). Also, you can configure pooling using the Advanced dialog of the Data Source Wizard and All dialog of Data Links.  
  
 The provider maintains a cache of connections, based on a Max Pool Size property. The default pool size is 100 connections (Max Pool Size=100), which you can adjust using the All dialog of the Data Source Wizard or Data Links. There is no upper limit for the Max Pool Size property. If you configure a value that is less than 0 for the Max Pool Size property, the default value of 100 is used.  
  
 Optionally, you can specify a number of seconds, to instruct the data provider to wait to establish connections using client-side pooling. When all connections in a pool are in use and the timeout period expires, then the data provider will return an error to the data consumer (“connection not available”). The default is 15 seconds (Connect Timeout=15), which you can adjust using the All dialog of the Data Source Wizard or Data Links. There is no upper limit for the Connect Timeout property. Specify -1 to instruct the data provider to wait indefinitely for an open connection in the client-side connection pool.  
  
#### Optimize the rowset cache when getting data  
 The RowsetCacheSize property instructs the data provider to pre-fetch rows from Informix while concurrently processing and returning rows to the data consumer. This feature may improve performance in bulk read-only operations on multi-processor or multi-core computers. The default value for this property is 0 ( RowsetCacheSize=0 ), which indicates that the optional pre-fetch feature is "off". We recommend setting a value between 10 and 100, with an initial recommended value of 10, which you can adjust using the All dialog of the Data Source Wizard or Data Links. This property instructs the data provider to pre-fetch up to the specified number of row batches, which are stored in the data provider’s rowset cache. The size of the row batches is automatically determined based on the value for cRows on the OLE DB IRowset::GetNextRows interface specified by the consumer.  
  
#### Deferring preparing of commands with parameters until execution  
 Defer Prepare instructs the data provider to optimize the processing of parameterized INSERT, UPDATE, DELETE, and SELECT commands. You can specify this option using the OLE DB data source initialization string ( Defer Prepare=True ). Also, you can configure pooling using the Advanced dialog of the Data Source Wizard and All dialog of Data Links. For the INSERT, UPDATE, and DELETE commands, the Data Provider combines prepare, execute, and commit commands into one network flow to the remote database. For the SELECT command, the Data Provider combines prepare and execute commands into one network flow. This minimizes network traffic and frequently improves overall performance.  
  
#### Command time-out to terminate long-running queries  
 The OLE DB Provider for Informix offers a command timeout property, to let developers automatically terminate long-running queries that may adversely affect performance.  
  
 The default value for the OLE DB Rowset DBPROP_COMMANDTIMEOUT is 0, which means no timeout. You can specify the value for command timeout from a number of consumers, such as those in SQL Server 2008 R2.  
  
###  <a name="measuringPerformance"></a> Measuring Performance  
 To measure performance, the data provider offers performance counters. By default performance counters are turned off. They can be turned on by changing value of the following registry key to 1:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Host Integration Server\Data Integration\UpdateCounters = 1  
  
 The data provider performance counters capture information about open connections, open statements, packets and bytes sent/received, average host (Informix server) processing time, command executions, data fetches, and transaction commits/rollbacks.
