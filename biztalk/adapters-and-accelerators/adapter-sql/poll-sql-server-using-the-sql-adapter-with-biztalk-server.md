---
title: "Poll SQL Server using the SQL Adapter with BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eef9a4b4-552d-4552-b318-1deab506bad9
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Poll SQL Server using the SQL Adapter with BizTalk Server
You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive polling-based data-changed messages from SQL Server. You can specify a polling statement that the adapter executes to poll the database. The polling statement can be a SELECT statement or a stored procedure that returns a result set. Based on the type of polling message received, the adapter exposes three different ways of polling:  
  
- **Polling**. This operation returns a data set as part of the polling message. At design time, the schema of the database object being polled is not available. Instead, the schema is available as part of the polling message during run time.  
  
- **TypedPolling**. This operation returns a strongly-typed polling message. At design time, the schema of the database object is also available. You must use this operation for polling if you want to map certain elements from the polling message to another schema, which could be for another operation.  
  
- **XmlPolling**. This operation returns the polling message as an XML message. You must use this operation if you want to use SELECT statements or stored procedures that use the FOR XML clause to return data as XML messages. For more information about the FOR XML clause, see [FOR XML (SQL Server)](https://msdn.microsoft.com/library/ms178107.aspx). 
  
  For more information about these polling operations, see [Support for Polling](https://msdn.microsoft.com/library/dd788416.aspx).  
  
> [!NOTE]
>  The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to have a single BizTalk application with more than one Polling or TypedPolling operations for the same database or table. To support such a scenario, the adapter includes a unique ID— **InboundID**—in the connection URI. This ID, when added to the connection URI, makes it unique, thereby enabling multiple polling operations in a single BizTalk application.  
  
 The topics in this section provide instructions on how to use Polling, TypedPolling, and XmlPolling in a BizTalk application. This section also provides information about how to use the **InboundID** connection property.  
  
## In This Section  
  
-   [Receive Polling-based Data-changed Messages from SQL Server by using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md)  
  
-   [Receive Strongly-typed Polling-based Data-changed Messages from SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md)  
  
-   [Receive Polling Messages Using SELECT Statements with FOR XML Clause from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md)  
  
-   [Receive Polling Messages Across Multiple Receive Ports from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)  
  
## See Also  
[Develop BizTalk applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)