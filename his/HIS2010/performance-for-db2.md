---
title: "Performance for DB2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19f42124-fac2-430d-86b5-1057cb1567d3
caps.latest.revision: 4
---
# Performance for DB2
This topic contains the following sections that will help you maximize performance when you are using the Data Providers for DB2.  
  
-   [Configuring for Performance](../HIS2010/performance-for-db2.md#conf)  
  
-   [Measuring Performance](../HIS2010/performance-for-db2.md#meas)  
  
##  <a name="conf"></a> Configuring for Performance  
 To improve performance, configure the providers in the following ways.  
  
 **Pool provider resources to reduce connection startup time**  
  
 Connection Pooling is a client-side optimization that reduces connection startup time, while reducing memory utilization on the client computer. The ADO.NET provider, OLE DB provider, Entity provider, and BizTalk Adapter support connection pooling. You can specify pooling using the ADO.NET connection string or OLE DB data source initialization string (**Connection Pooling=True**). Also, you can configure pooling using the **Advanced** dialog of the Data Source Wizard and **All** dialog of Data Links.  
  
 The provider maintains a cache of connections, based on a Max Pool Size property. The default pool size is 100 connections (**Max Pool Size=100**), which you can adjust using the **All** dialog of the Data Source Wizard or Data Links. There is no upper limit for the Max Pool Size property. If you configure a value that is less than 0 for the Max Pool Size property, the default value of 100 is used.  
  
 Optionally, you can specify a number of seconds, to instruct the data provider to wait to establish connections using client-side pooling. When all connections in a pool are in use and the timeout period expires, then the data provider will return an error to the data consumer (“connection not available”). The default is 15 seconds (**Connect Timeout=15**), which you can adjust using the **All** dialog of the Data Source Wizard or Data Links. There is no upper limit for the Connect Timeout property. Specify -1 to instruct the data provider to wait indefinitely for an open connection in the client-side connection pool.  
  
 **Optimize the rowset cache when getting data**  
  
 The RowsetCacheSize property instructs the data provider to pre-fetch rows from DB2 while concurrently processing and returning rows to the data consumer. This feature may improve performance in bulk read-only operations on multi-processor or multi-core computers. The default value for this property is 0 (**RowsetCacheSize=0**), which indicates that the optional pre-fetch feature is "off". We recommend setting a value between 10 and 100, with an initial recommended value of 10, which you can adjust using the **All** dialog of the Data Source Wizard or Data Links. This property instructs the data provider to pre-fetch up to the specified number of row batches, which are stored in the data provider’s rowset cache. The size of the row batches is automatically determined based on the value for cRows on the OLE DB IRowset::GetNextRows interface specified by the consumer.  
  
 **Deferring preparing of commands with parameters until execution**  
  
 Defer Prepare instructs the data provider to optimize the processing of parameterized INSERT, UPDATE, DELETE, and SELECT commands. You can specify this option using the ADO.NET connection string or OLE DB data source initialization string (**Defer Prepare=True**). Also, you can configure pooling using the **Advanced** dialog of the Data Source Wizard and **All** dialog of Data Links. For the INSERT, UPDATE, and DELETE commands, the Data Provider combines prepare, execute, and commit commands into one network flow to the remote database. For the SELECT command, the Data Provider combines prepare and execute commands into one network flow. This minimizes network traffic and frequently improves overall performance.  
  
 **Sending multiple rows in a single unit of work**  
  
 The OLE DB Provider for DB2 supports the OLE DB IRowsetFastLoad interface to enable SQL Server 2008 R2 Integration Services to execute multiple INSERT, UPDATE, DELETE or CALL statements in optimized batches. This better uses TCP/IP network packets and increases overall performance. Developers can select IRowsetFastLoad when configuring OLE DB Destinations in Data Flows within Integration Services packages using the Business Intelligence Developer Studio package designer. The IRowsetFastLoad interface is supported when inserting, updating or deleting rows into DB2 for z/OS V8 and V9, DB2 for i5/OS V5R4 and V6R1, and DB2 for LUW V9. For more information, see Access Mode for Integration Services OLE DB Destination Custom Properties (http://go.microsoft.com/fwlink/?LinkID=180768).  
  
 **Command time-out to terminate long-running queries**  
  
 The ADO.NET Data Provider for DB2 and OLE DB Provider for DB2 offer a command timeout property, to let developers automatically terminate long-running queries that may adversely affect performance.  
  
 The default value for the ADO.NET Command.CommandTimeout property is 30 seconds, instructing the provider to wait 30 seconds for the command to execute. The default value for the OLE DB Rowset DBPROP_COMMANDTIMEOUT is 0, which means no timeout. You can specify the value for command timeout from a number of consumers, such as those in SQL Server 2008 R2. For more information, see the Data Consumer topics in Data Integration (Configuration).  
  
##  <a name="meas"></a> Measuring Performance  
 To measure performance, the data provider offers performance counters. By default performance counters are turned off. They can be turned on by changing value of the following registry key to 1:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Host Integration Server\Data Integration\UpdateCounters = 1  
  
 The data provider performance counters capture information about open connections, open statements, packets and bytes sent/received, average host (DB2 server) processing time, command executions, data fetches, and transaction commits/rollbacks. For more information, see Performance Counters (http://go.microsoft.com/fwlink/?LinkID=119211).  
  
## See Also  
 [Performance Problems](../HIS2010/performance-problems1.md)   
 [Data Integration (Operations)](../HIS2010/data-integration-operations-1.md)