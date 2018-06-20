---
title: "Understand the BizTalk Adapter for Oracle Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF LOB Adapter SDK"
  - "features of Oracle database adapter"
  - "table"
  - "adapter client"
  - "service model"
  - "WCF"
  - "artifacts"
  - "database tables"
  - "adapters, features"
  - "Windows Communication Foundation"
  - "adapter features"
  - "channel model"
ms.assetid: a8691957-0430-4cba-83f8-b60c21a86849
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Understand the BizTalk Adapter for Oracle Database
The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access in order to interact with an external system. The adapters provide the following advantages to clients:  
  
- **Consistent design-time experience**. The adapters provide a common and user-friendly design-time experience for browsing, searching, and retrieving metadata of LOB artifacts.  
  
- **Varied programming options**. The adapters provide a choice of programming model including the Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, Web services, or BizTalk supported models.  
  
- **Uniform experience across LOBs**. The adapters standardize on using WCF and [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], and hence provide a uniform experience of gaining access to any LOB system.  
  
  As mentioned, the adapters are built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligns the adapter strategy with the Microsoft Services strategy by exposing integration adapters as Windows Communication Foundation (WCF) channels. For more information about the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], see the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation is installed along with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], typically under \<installation drive\>:\Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.  
  
  To perform operations on an Oracle database, adapter clients must have access to relevant tables, functions, and procedures. Database tables are the basic unit of storage in the Oracle database. External applications can add or remove data from a table by using SQL statements. Applications can also access data in the tables by using views, functions, and procedures. With [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)], adapter clients can browse the artifacts such as tables, procedures, packages, views, and other such items in an Oracle database. Adapter clients can select the artifacts they require for their solution and retrieve metadata for those artifacts. This enables users to access and execute the operations on the artifacts in the Oracle database.  
  
  This section lists the features of the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
## In This Section  
  
-   [Overview of BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)  
  
-   [Key Features in BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md)  
  
-   [Limitations of BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/limitations-of-biztalk-adapter-for-oracle-database.md)  
  
## See Also  
[Getting started with BizTalk Server](../../core/getting-started-with-biztalk-server.md)