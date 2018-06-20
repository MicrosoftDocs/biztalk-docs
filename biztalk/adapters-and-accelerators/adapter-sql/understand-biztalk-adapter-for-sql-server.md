---
title: "Understand BizTalk Adapter for SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 302a7f20-ffa2-49f1-a4c4-dd713adc23e1
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Understand BizTalk Adapter for SQL Server
The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access making it possible to interact with an external system. The adapters provide the following advantages to clients:  
  
- **Consistent design-time experience**. The adapters provide a common and user-friendly design-time experience for browsing, searching, and retrieving metadata of LOB artifacts.  
  
- **Varied programming options**. The adapters provide a choice of programming model including the Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, Web services, or BizTalk supported models.  
  
- **Uniform experience across LOBs**. The adapters standardize on using WCF and the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], and hence provide a uniform experience of gaining access to any LOB system.  
  
  As mentioned, the adapters are built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels. For more information about the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], see the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation is installed along with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], typically under \<installation drive\>:\Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.  
  
  To perform operations on a SQL Server database, adapter clients must have access to relevant tables, procedures, views, scalar functions, and table valued functions. Database tables are the basic unit of storage in the SQL Server database. External applications can select, insert, delete, and update data from a table by using SQL statements. Applications can also access data in the tables by using procedures, views, scalar functions, and table valued functions. With [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)], adapter clients can browse artifacts such as tables, procedures, views, and other such items in a SQL Server database. Adapter clients can select the artifacts they require for their solution, and retrieve metadata for those artifacts. This enables users to access and execute the operations on the artifacts in the SQL Server database.  
  
  This section lists the features of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## In This Section  
  
-   [Overview of BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)  
  
-   [Key features in BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/key-features-in-biztalk-adapter-for-sql-server.md) 
  
-   [Limitations of BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/limitations-of-biztalk-adapter-for-sql-server.md)  
  
## See Also  
[Get started with the BizTalk adapter for SQL](../../adapters-and-accelerators/adapter-sql/get-started-with-the-biztalk-adapter-for-sql.md)