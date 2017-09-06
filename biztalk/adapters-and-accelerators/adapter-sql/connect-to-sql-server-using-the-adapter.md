---
title: "Connect to SQL Server using the adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 727d73e6-fb84-48ce-ae72-5de70dcae8b8
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Connect to SQL Server using the adapter
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] requires adapter clients to provide a connection string, called the connection Uniform Resource Identifier (URI), to connect to the SQL Server database. Internally, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] maps the URI to a database connection string to connect to the SQL Server database. With a connection URI, adapter clients can specify connection parameters to connect to an external system. For more information about the connection URI, see [Create the SQL Server Connection URI](../../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).  
  
 In the connection URI, you can also specify the name of a failover SQL Server database on a standby computer to connect to if the primary SQL Server database is not available. The failover SQL Server database must be a mirror of the primary SQL Server database. The failover SQL Server database is specified using an optional parameter, FailoverPartner, in the connection URI. Providing a failover SQL Server database ensures high availability and data redundancy. For more information about high availability with respect to SQL Server, see [Database Mirroring in SQL Server](https://msdn.microsoft.com/library/5h52hef8.aspx).
  
 Make sure you comply with the security guidelines when establishing a connection with the SQL Server database. For more information about security guidelines, see [Secure your SQL applications](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md).  
  
## See Also  
 [Overview of BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)   
 [Create a Connection to SQL Server](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)