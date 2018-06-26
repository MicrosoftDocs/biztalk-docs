---
title: "Oracle E-Business Suite adapter FAQs | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4f7fe4e0-ddd5-402f-bbbc-b320850eaf3b
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Oracle E-Business Suite adapter FAQs
The following are some frequently asked questions (FAQs) related to [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]. Also see [Frequently asked questions for the BizTalk Adapter Pack](../../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md).
  

## How can I use the Oracle E-Business adapter to communicate with Oracle E-Business Suite?  
 You can use the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to communicate with Oracle E-Business Suite either by developing BizTalk applications, using the WCF service model or using the WCF channel model. For more information, see [Overview of BizTalk Adapter for Oracle E-Business Suite](http://msdn.microsoft.com/library/4f18fa2e-4e97-4c28-b38d-fc39ac53789e).  
  
## What interfaces are supported by the Oracle E-Business adapter for retrieving metadata?  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports two interfaces for retrieving metadata:  
  
-   MetadataExchange provided by WCF. WCF provides a metadata-exchange endpoint for all WCF bindings, which enables clients to get metadata from Oracle E-Business Suite.  
  
-   IMetadataRetrievalContract provided by the WCF LOB Adapter SDK, which supports the metadata browsing and searching capabilities of the adapter.  
  
## How does the adapter connect to Oracle E-Business Suite?  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses the Oracle Data Access Components for Oracle Client. [Supported LOB systems](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx) lists the client versions. To connect to Oracle E-Business Suite, the adapter clients must provide a connection string, [connection Uniform Resource Identifier (URI)](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md). Internally, the adapter maps the connection URI to a connection string to connect to the underlying database in Oracle E-Business Suite. See [Create a connection to Oracle EBS](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-connection-to-oracle-e-business-suite.md).  
  
## Does the Oracle E-Business adapter provide a secure way of communicating with the Oracle E-Business Suite?  Are there any best practices to ensure data security?  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] supports Enterprise Single Sign-On (SSO) for authentication on the connections that it establishes with Oracle E-Business Suite. The SSO uses a database and a master secret to encrypt and store user credentials. It also provides services to map Microsoft Windows accounts to secondary credentials that are used to access a back-end system.  
  
 The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] also requires you to enter username and password credentials to connect to Oracle E-Business Suite. These credentials are used to authenticate the user, and thus provide a level of authorization for the connections. The Oracle E-Business adapter provides a number of methods through which you can supply these credentials. For information about how to securely provide Oracle credentials in BizTalk solutions, see [Security with the adapter and BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/security-with-the-oracle-e-business-suite-adapter-and-biztalk-server.md). For information about how to securely provide Oracle credentials in programming solutions, see [Secure programming with the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/secure-programming-with-the-oracle-ebs-adapter.md).  
  
 For more information:  
  
- Data security in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Secure your Oracle EBS applications](../../adapters-and-accelerators/adapter-oracle-ebs/secure-your-oracle-ebs-applications.md).  
  
- Best practices to ensure data security in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Security best practices](../../adapters-and-accelerators/adapter-oracle-ebs/best-practices-to-secure-the-oracle-e-business-suite-adapter.md).  
  
## Is there a GUI provided by the Oracle E-Business adapter to view and perform operations on the artifacts in Oracle E-Business Suite?  
 The Consume Adapter Service BizTalk Project Add-in and the Add Adapter Service Reference Visual Studio Plug-in provide a dialog box where you can view and perform operations on the artifacts in Oracle E-Business Suite. For more information about the GUI provided by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Browse, search, and get metadata for Oracle EBS operations](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
## What are binding properties in the Oracle E-Business adapter? Where can I find information about all the binding properties in the Oracle E-Business adapter?  
 Adapter clients can use binding properties in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to configure and control the adapter’s behavior. For information about all the binding properties surfaced in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Working with the binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
## What are inbound and outbound operations in the Oracle E-Business adapter?  
 In inbound operations, the LOB system (Oracle E-Business Suite) is the client and the adapter clients are the service, wherein the transactions originate from Oracle E-Business Suite. For example, the Polling and Notification operations.  
  
 In outbound operations, the adapter clients are the client and the LOB system (Oracle E-Business Suite) becomes the service, wherein the transactions originate from the adapter clients. For example, the Insert, Select, Update, and Delete Operation on Interface tables, operation on stored procedures and functions, and composite operations.  
  
## Where can I find information about the Oracle data types that are supported in the Oracle E-Business adapter?  
 For information about the Oracle data types supported in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Basic Oracle Data Types](../../adapters-and-accelerators/adapter-oracle-ebs/basic-oracle-data-types2.md).  
  
## What is applications context? How can I set applications context for various Oracle artifacts in the Oracle E-Business adapter?  
 For information about applications context and how to set it in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
## Which approach (BizTalk Server, WCF service model or WCF channel model) can I use to perform various operations using the Oracle E-Business adapter?  
 For information about the approach you can use to perform various operations using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Develop your Oracle EBS applications](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md).  
  
## See Also  
[Frequently asked questions for the BizTalk Adapter Pack](../../adapters-and-accelerators/frequently-asked-questions-for-the-biztalk-adapter-pack.md)