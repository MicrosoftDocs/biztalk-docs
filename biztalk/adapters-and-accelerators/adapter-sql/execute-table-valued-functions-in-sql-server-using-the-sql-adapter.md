---
title: "Execute Table-Valued Functions in SQL Server using the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3fb8c81c-9384-4eba-b0a0-baed1782245b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Execute Table-Valued Functions in SQL Server using the SQL adapter
The Transact-SQL and CLR table valued functions in SQL Server are surfaced as operations in [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]. The operation name in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is the same as the name of the table valued function in SQL Server.  
  
 All the parameters in the table valued function are exposed in the corresponding operation. If you do not specify an input parameter for a table valued function, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] internally invokes the function using the DEFAULT keyword. This implies that the table valued function is executed using the default value specified while defining the function.  
  
 For more information about:  
  
- Using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with BizTalk Server to invoke table valued functions in SQL Server, see [Invoking Table-Valued Functions in SQL Server by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md).  
  
- Message structure and SOAP actions for table valued functions, see [Message Schemas for Procedures and Functions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md).  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)