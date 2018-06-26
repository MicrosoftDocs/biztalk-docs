---
title: "Poll Oracle Database using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c3aef30-956d-4585-b2de-7eebb919fab5
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Poll Oracle Database using BizTalk Server
You can configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to receive polling-based messages from Oracle database. The adapter provides two ways of polling the Oracle database:  
  
- **Using SELECT statements**. You can specify a simple SELECT statement to poll the tables and views in the Oracle database. The adapter executes the SELECT statement at specified intervals and returns the result to the adapter clients.  
  
- **Using stored procedures, functions, or procedures or functions within a package**. You can specify a stored procedure, function, or procedure or function within a package to poll the Oracle database. The adapter executes the request message at specified intervals and returns the result to the adapter clients.  
  
  The key difference in the two approaches is the way adapter clients specify a polling statement that the adapter uses to poll the Oracle database. While the polling statement for the first approach is a simple SELECT statement, the polling statement for the other approach is a request message that executes the stored procedure, function, or procedure or function within a package. Adapter clients specify the polling statement, for either approach, in the **PollingStatement** binding property. For more information about the binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
  The topics in this section provide instructions on how to poll using a SELECT statement and a stored procedure, function, or procedure or function within a package.  
  
## In This Section  
  
-   [Poll Oracle Database using the SELECT statement](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-the-select-statement.md)  
  
-   [Poll Oracle Database Using Stored Procedures, Functions, or Packaged Procedures and Functions](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-db-using-stored-procedures-functions-or-packaged-procedures.md)  
  
## See Also  
[Develop BizTalk applications using the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)