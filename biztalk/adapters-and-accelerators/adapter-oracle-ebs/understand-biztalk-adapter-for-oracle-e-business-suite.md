---
title: "Understand BizTalk Adapter for Oracle E-Business Suite | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77a3f0a8-fc64-42cd-bb7c-0a6f527622e4
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Understand BizTalk Adapter for Oracle E-Business Suite
## BizTalk Adapter Pack features
The [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] enables service-oriented programmatic access in order to interact with an external system. The adapters provide the following advantages to clients:  
  
- **Consistent design-time experience**. The adapters provide a common and user-friendly design-time experience for browsing, searching, and retrieving metadata of LOB artifacts.  
  
- **Varied programming options**. The adapters provide a choice of programming model including the Windows Communication Foundation (WCF) channel model, WCF service model, ADO.NET, Web services, or BizTalk Server supported models.  
  
- **Uniform experience across LOBs**. The adapters standardize on using WCF and [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)], and hence provide a uniform experience of gaining access to any LOB system.  
  
  As mentioned, the adapters are built on top of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. This SDK  provides a common basis for building integration adapters that a variety of client applications such as BizTalk Server and Microsoft Office can consume. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] aligns the adapter strategy with the Microsoft services strategy by exposing integration adapters as WCF channels. For more information about the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], see the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation. The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] documentation is installed along with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], typically under \<*installation drive*\>:\Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents.  

## Overview of the Oracle EBS adapter
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] exposes Oracle E-Business Suite as a WCF service. Adapter clients can perform operations on the Oracle E-Business Suite by exchanging SOAP messages with the adapter. The adapter consumes the SOAP message and makes appropriate ODP.NET calls to perform the operation. The adapter returns the response from Oracle E-Business Suite back to the client in the form of SOAP messages.  
  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]displays metadata of the Oracle E-Business Suite artifacts (PL/SQL APIs, interface tables/views, concurrent programs, and request sets) and the underlying Oracle database artifacts (such as tables, functions, and procedures) that describe the structure of a SOAP message in the form of Web Services Description Language (WSDL). The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to enable adapter clients to retrieve metadata for operations. The adapter also generates programming artifacts that can be used in your programming solution. For more information about [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], and [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], see [Connect to the Oracle E-Business Suite in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md).  
  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the Oracle Data Provider for .NET (ODP.NET) 11.1.0.7 to communicate with Oracle E-Business Suite. ODP.NET 11.1.0.7 is one of the components of Oracle Data Access Components (ODAC). You can use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to communicate with Oracle E-Business Suite in the following ways:  
  
- By developing BizTalk applications. For more information, see [Developing BizTalk Server  Applications](../../core/developing-biztalk-server-applications.md).  
  
- By using the [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] service model. For more information, see [Develop Oracle Database Applications By Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md).  
  
- By using the WCF channel model. For more information, see [Develop SQL Applications by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).  

## Access to Oracle E-Business Suite
 To perform operations in Oracle E-Business Suite, adapter clients must have access to relevant artifacts in Oracle E-Business Suite. External applications can add or remove data in Oracle E-Business Suite interface tables and the database tables by using SQL statements. Applications can also access data in the interface tables and the database tables by using views, functions, and procedures. With [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], adapter clients can browse the artifacts in Oracle E-Business Suite as well as in the underlying database. In Oracle E-Business Suite, the adapter clients can browse interface tables, interface views, concurrent programs, and request sets while in the underlying Oracle database, the adapter clients can browse tables, views, stored procedures, functions, PL/SQL APIs, and packages. Adapter clients can select the artifacts they require for their solution and retrieve metadata for those artifacts. This enables users to access and execute the operations on the artifacts in Oracle E-Business Suite and the underlying Oracle database.  
  
 This section lists the features of the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].  
  
## More good stuff  
  
-    [Connect to Oracle E-Business Suite using the adapter](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-the-adapter.md)

- [Browse, Search, and get Oracle E-Business Suite metadata](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-oracle-e-business-suite-metadata.md)

- [What operations are supported by the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/what-operations-are-supported-by-the-oracle-e-business-suite-adapter.md)

- [Handle transactions with the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/handle-transactions-with-the-oracle-database-adapter.md) 

- [Features for Oracle EBS adapter clients](../../adapters-and-accelerators/adapter-oracle-ebs/features-for-oracle-ebs-adapter-clients.md) 

-   [Key Features in BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/key-features-in-biztalk-adapter-for-oracle-e-business-suite.md)  
  
-   [Limitations of BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/limitations-of-biztalk-adapter-for-oracle-e-business-suite.md)  
  
## See Also  
[Get started](../../adapters-and-accelerators/adapter-oracle-ebs/get-started-with-the-biztalk-adapter-for-oracle-e-business-suite.md)