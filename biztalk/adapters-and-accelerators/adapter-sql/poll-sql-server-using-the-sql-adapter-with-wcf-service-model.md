---
title: "Poll SQL Server using the SQL Adapter with WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eef2e868-bd51-4393-b091-f67299b4759d
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Poll SQL Server using the SQL Adapter with WCF Service Model
You can configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive polling-based data-changed messages from SQL Server. You can specify a polling statement that the adapter executes to poll the database. The polling statement can be a SELECT statement or a stored procedure that returns a result set. Based on the type of polling message received, the adapter exposes different polling operations:  
  
- **Polling**. This operation returns a data set as part of the polling message.  
  
- **TypedPolling**. This operation returns a strongly-typed polling message.  
  
- **XmlPolling**. This operation returns the polling message as an XML message. You must use this operation if you want to use SELECT statements or stored procedures that use the FOR XML clause to return data as XML messages. [FOR XML clause](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server) provides more info. 
  
  For more information about these polling operations, see [Polling in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md).  
  
> [!NOTE]
>  The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to have a single application with more than one Polling or TypedPolling operations for the same database or table. To support such a scenario, the adapter includes a unique ID— **InboundID**—in the connection URI. This ID, when added to the connection URI, makes it unique, thereby enabling multiple polling operations in a single application.  
  
 The topics in this section provide instructions on how to use both Polling and TypedPolling operations in a .NET application.  
  
## In This Section  
  
-   [Receive Polling-based Data-changed Messages from SQL Server Using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-service.md)  
  
-   [Receive Strongly-typed Polling-based Data-changed Messages from SQL Server Using WCF Service Model](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md)  
  
## See Also  
[Develop SQL applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)