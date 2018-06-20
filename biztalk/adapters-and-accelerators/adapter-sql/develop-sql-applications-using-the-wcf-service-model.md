---
title: "Develop SQL applications using the WCF Service model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3ecfd6f-9144-4e41-a4b8-0c768a6ac254
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop SQL applications using the WCF Service model
[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] provides a programming model called the WCF service model, as an alternative to the WCF channel programming model.  
  
 The WCF service model uses familiar .NET paradigms to hide the complexities of exchanging SOAP messages over a channel. The service model accomplishes this simplification by reading the entire SOAP message into memory before copying the information into .NET data structures. Loading long messages into memory, however, may not be practical for some applications. In these cases, developers should use the WCF channel model. For more information about using the WCF channel model, see [Develop SQL applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md).  
  
 At the lowest level, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] presents the WCF channel model, in which clients invoke operations on a service by exchanging SOAP messages over a channel established between client and service endpoints. The WCF channel model exposes data types and methods that enable you to operate directly on the WCF channel architecture. The WCF channel model provides you with direct control over the contents of the SOAP messages you create and over the way both your application and the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] consume them. However, creating well-formed SOAP messages to send over a channel and validating the reply messages returned can be a detailed and exacting task.  
  
 The WCF service model uses proxy classes to invoke operations on a target service or to receive operations from a client. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes the SQL Server database as a WCF service on which you can invoke operations.  
  
- The proxy class that is used to invoke operations on a target service is called a WCF client class. This class models the operations exposed by a service as .NET methods with strongly-typed parameters. By using the WCF service model, you can invoke the operations exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] as .NET methods on the WCF client. For more information about WCF clients, see [WCF Client Overview](https://msdn.microsoft.com/library/ms735103.aspx).
  
  You can use either of the following tools to generate a WCF client class and associated helper code from the service metadata that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes:  
  
- **The ServiceModel Metadata Utility Tool (svcutil.exe)**, which ships with WCF.  
  
- **The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]**, which ships with [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and is integrated with the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] design experience. This tool presents a standard Microsoft Windows interface that provides powerful browsing and searching capabilities on operations that the adapter exposes. For more information about how to generate a WCF client application, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
   The topics in this section contain information, procedures, and examples to help you create and use the WCF service model to develop applications by using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## In This Section  
  
-   [Overview of the WCF service model with the SQL adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)  
  
-   [Metadata and the WCF Service Model with the SQL adapter](../../adapters-and-accelerators/adapter-sql/metadata-and-the-wcf-service-model-with-the-sql-adapter.md)  
  
-   [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)  
  
-   [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)  
  
-   [Insert, update, delete, or select operations on interface tables and views using the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)  
  
-   [Run Operations on Tables and Views with Large Data Types in SQL using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)  
  
-   [Invoke Stored Procedures in SQL using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/invoke-stored-procedures-in-sql-using-the-wcf-service-model.md)  
  
-   [Invoke Scalar Functions in SQL Server by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model.md)  
  
-   [Invoke Table-Valued Functions in SQL Server by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model.md)  
  
-   [ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in SQL using WCF Service Model](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-executenonquery-in-sql-using-wcf-service-model.md)  
  
-   [Poll SQL Server using the SQL Adapter with WCF Service Model](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)  
  
-   [Receive Query Notifications from SQL using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-from-sql-using-the-wcf-service-model.md)  
  
## See Also  
[Develop your SQL applications](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)