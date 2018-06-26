---
title: "Invoke Stored Procedures in SQL using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4edd2fac-0b54-4406-932e-e3044a66b2e6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Invoke Stored Procedures in SQL using the WCF Service Model
The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers the stored procedures as operations that the adapter clients can invoke on the WCF client to invoke the stored procedure. Based on how the stored procedure returns the result set, the adapter categorizes all the stored procedures as:  
  
- **Procedures**. Invoking stored procedures from the **Procedures** node returns an array of DataSet.  
  
- **Strongly-Typed Procedures**. Invoking stored procedures from the **Strongly-Typed Procedures** node returns a strongly-typed result set.  
  
  Note that the same set of stored procedures in the database you connected to will be listed both under the **Procedures** and **Strongly-Typed Procedures** node. Based on the kind of result set you want, you must invoke the stored procedure from the relevant node. For more information about how the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] supports stored procedures, see [Execute Stored Procedures in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md).  
  
  This section provides instructions on how to invoke stored procedures from both the **Procedures** and **Strongly-Typed Procedures** node by using a WCF client.  
  
## In This Section  
  
-   [Involk Weakly-typed Stored Procedures in SQL Using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/invoke-weakly-typed-stored-procedures-in-sql-using-the-wcf-service-model.md)  
  
-   [Invoke Strongly-typed Stored Procedure in SQL Using WCF Service Model](../../adapters-and-accelerators/adapter-sql/invoke-strongly-typed-stored-procedures-in-sql-using-wcf-service-model.md)  
  
## See Also  
[Develop applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)