---
title: "Overview of BizTalk Adapter for SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e46690e-d5c4-4d6b-b7a0-9a5adf4431cd
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Overview of BizTalk Adapter for SQL Server
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] exposes the SQL Server database as a WCF service. Adapter clients can perform operations on the SQL Server database by exchanging SOAP messages with the adapter. The adapter consumes the SOAP message and makes appropriate ADO.NET calls to perform the operation. The adapter returns the response from the SQL Server database back to the client in the form of SOAP messages.  
  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] surfaces metadata of artifacts in the SQL Server database (such as tables, views, and procedures).  This metadata describes the structure of a SOAP message in the form of Web Services Description Language (WSDL). The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to enable adapter clients to retrieve metadata for operations. The adapter also generates programming artifacts that can be used in your programming solution. For more information about [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], see [Connect to SQL Server in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-in-visual-studio-using-the-sql-adapter.md).  
  
 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses ADO.NET to communicate with the SQL Server database. You can use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to communicate with the SQL Server database in the following ways:  
  
- By developing BizTalk applications. For more information, see [Develop BizTalk applications](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md).  
  
- By using the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model. For more information, see [Develop applications using the WCF Service model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md).  
  
- By using the WCF channel model. For more information, see [Develop applications using the WCF Channel model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).  
  
## In This Section  
  
-   [How Does the Adapter Connect to SQL Server?](https://msdn.microsoft.com/library/dd788114.aspx) 
  
-   [How Does the Adapter Surface SQL Server Metadata?](https://msdn.microsoft.com/library/dd787941.aspx)  
  
-  [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)  
  
-   [What operations are supported by the SQL adapter](../../adapters-and-accelerators/adapter-sql/what-operations-are-supported-by-the-sql-adapter.md)  
  
## See Also  
 [Understand BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)