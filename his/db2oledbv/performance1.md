---
title: "Performance1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da1c83cf-bd12-4ef0-b0ef-74514c6d7ab2
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Performance
This topic will help you maximize performance when using Data Provider.

## Configuring for Performance
 To improve performance, configure the providers in the following ways.

### Pool OLE DB resources to reduce connection startup time
 OLE DB Resource Pooling and Provider Connection Pooling may increase performance by reducing connection startup time. Resource Pooling is enabled through OLE DB Service Components that are part of the Windows operating system. You can enable OLE DB Resource Pooling by setting OLE DB initialization properties and registry settings. For more information, see [OLE DB Resource Pooling](https://go.microsoft.com/fwlink/?LinkID=180446) (https://go.microsoft.com/fwlink/?LinkID=180446).

### Pool provider resources to reduce connection startup time
 Connection Pooling is a client-side optimization that reduces connection startup time, while reducing memory utilization on the client computer. The Data Provider supports connection pooling. You can specify pooling using the OLE DB data source initialization string (**Connection Pooling=True**). Also, you can configure pooling using the **Advanced** dialog of the Data Source Wizard and **All** dialog of Data Links.

 The provider maintains a cache of connections, based on a Max Pool Size property. The default pool size is 100 connections (**Max Pool Size=100** ), which you can adjust using the **All** dialog of the Data Source Wizard or Data Links. There is no upper limit for the Max Pool Size property. If you configure a value that is less than 0 for the Max Pool Size property, the default value of 100 is used. Optionally, you can specify a number of seconds, to instruct the data provider to wait to establish connections using client-side pooling. When all connections in a pool are in use and the timeout period expires, then the data provider will return an error to the data consumer (“connection not available”). The default is 15 seconds (**Connect Timeout=15** ), which you can adjust using the **All** dialog of the Data Source Wizard or Data Links. There is no upper limit for the Connect Timeout property. Specify -1 to instruct the data provider to wait indefinitely for an open connection in the client-side connection pool.

### Optimize the rowset cache when getting data
 The RowsetCacheSize property instructs the data provider to pre-fetch rows from DB2 while concurrently processing and returning rows to the data consumer. This feature may improve performance in bulk read-only operations on multi-processor or multi-core computers. The default value for this property is 0 (**RowsetCacheSize=0** ), which indicates that the optional pre-fetch feature is "off". We recommend setting a value between 10 and 100, with an initial recommended value of 10, which you can adjust using the **All** dialog of the Data Source Wizard or Data Links. This property instructs the data provider to pre-fetch up to the specified number of row batches, which are stored in the data provider’s rowset cache. The size of the row batches is automatically determined based on the value for cRows on the OLE DB IRowset::GetNextRows interface specified by the consumer.

### Deferring preparing of commands with parameters until execution
 Defer Prepare instructs the data provider to optimize the processing of parameterized INSERT, UPDATE, DELETE, and SELECT commands. You can specify this option using the ADO.NET connection string or OLE DB data source initialization string (**Defer Prepare=True** ). Also, you can configure pooling using the **Advanced** dialog of the Data Source Wizard and **All** dialog of Data Links. For the INSERT, UPDATE, and DELETE commands, the Data Provider combines prepare, execute, and commit commands into one network flow to the remote database. For the SELECT command, the Data Provider combines prepare and execute commands into one network flow. This minimizes network traffic and frequently improves overall performance.

### Retrieving schema information from DB2 shadow catalog
 The Shadow Catalog property instructs the Data Provider to retrieve schema information from a DB2 shadow catalog. The DB2 administrator can define a shadow catalog to contain the schema information for tables, columns, primary keys, and indexes. All data consumers use this schema information at design time. Some data consumers use this information at runtime. The DB2 schema catalog can become inaccessible due to locks during writes (create and alter statement execution). Also, the default DB2 schema can be large, adding latency to design-time and run-time data consumer operations. A shadow catalog can reduce contention and improve performance, when performing schema fetch operations.

### Sending multiple rows in a single unit of work
 The Data Provider supports the OLE DB IRowsetFastLoad interface to enable consumers, such as Integration Services, to execute multiple INSERT statements in optimized batches. This better uses TCP/IP network packets and increases overall performance. You select RowsetFastLoad when configuring OLE DB Destinations in Data Flows within Integration Services packages using the Business Intelligence Developer Studio package designer. The IRowsetFastLoad interface is supported when inserting into DB2. For more information, see Access Mode for Integration Services OLE DB [Destination Custom Properties](https://go.microsoft.com/fwlink/?LinkId=241518) (https://go.microsoft.com/fwlink/?LinkId=241518).

### Command time-out to terminate long-running queries
 The Data Provider offers a command timeout property, to let you automatically terminate long-running queries that may adversely affect performance. The default value for the OLE DB Rowset DBPROP_COMMANDTIMEOUT is 0, which means no timeout.

 You can specify the value for command timeout from a number of consumers. The Data Provider offers an OLE DB Rowset DBPROP_COMMANDTIMEOUT property, to let developers automatically terminate long-running queries that may adversely affect performance. Integration Services and Analysis Services expose this property through the Data Source Query Timeout option in the Business Intelligence Development Studio. Reporting Services exposes this property through the Dataset Properties Timeout option in the Business Intelligence Development Studio. Replication and Query Processor expose this property through the sp_serveroption, @optname=query time-out.

## Measuring Performance
 To measure performance, the Data Provider offers performance counters. By default performance counters are turned off. They can be turned on by changing value of the following registry key to 1:

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Host Integration Server\Data Integration\UpdateCounters = 1
```

 The Data Provider performance counters capture information about open connections, open statements, packets and bytes sent/received, average host (DB2 server) processing time, command executions, data fetches, and transaction commits/rollbacks. For more information, see [Performance Counters](https://go.microsoft.com/fwlink/?LinkID=119211) (https://go.microsoft.com/fwlink/?LinkID=119211).