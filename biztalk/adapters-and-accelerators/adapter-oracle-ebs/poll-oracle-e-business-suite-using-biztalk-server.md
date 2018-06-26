---
title: "Poll Oracle E-Business Suite using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a22b99a5-1715-4351-b0e0-6b8dcfacd9eb
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Poll Oracle E-Business Suite using BizTalk Server
You can configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to receive polling-based messages from Oracle database. The adapter provides two ways of polling the Oracle database:  
  
- **Using SELECT statements**. You can specify a simple SELECT statement to poll the Oracle database. The adapter executes the SELECT statement at specified intervals and returns the result to the adapter clients.  
  
- **Using stored procedures**. You can specify a stored procedure to poll the Oracle database. The adapter executes the stored procedure at specified intervals and returns the result to the adapter clients.  
  
  The key difference in the two approaches is the way adapter clients specify a polling statement that the adapter uses to poll the Oracle database. While the polling statement for the first approach is a simple SELECT statement, the polling statement for the stored procedure approach is a request message that executes the stored procedure. Adapter clients specify the polling statement, for either approach, for the **PollingInput** binding property. For more information about the binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
  The topics in this section provide instructions on how to poll using a SELECT statement and a stored procedure.  
  
## In This Section  
  
-   [Poll Oracle E-Business Suite Using SELECT Statement](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement.md)  
  
-   [Poll Oracle E-Business Suite Using Stored Procedures](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-stored-procedures.md)  
  
## See Also  
[Develop BizTalk applications using the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)