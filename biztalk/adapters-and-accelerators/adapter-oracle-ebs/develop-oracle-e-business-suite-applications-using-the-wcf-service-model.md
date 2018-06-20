---
title: "Develop Oracle E-Business Suite applications using the WCF Service Model | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1cf3430d-12e9-437c-b398-d978faa4da2b
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop Oracle E-Business Suite applications using the WCF Service Model
[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] provides a programming model called the WCF service model to connect to the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]. The service model was added to WCF to address, in part, some of the limitations of the WCF channel programming model.  
  
 The WCF service model uses familiar .NET paradigms to hide the complexities of exchanging SOAP message over a channel. The service model accomplishes this simplification by reading the entire SOAP message into memory before copying the information into .NET data structures. Loading long messages into memory may not be practical for some applications. In these cases, developers should use the WCF channel model. For more information about using the WCF channel model, see [Develop Oracle E-Business Suite Applications by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md).  
  
 At the lowest level, the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] presents the WCF channel model in which clients invoke operations on a service by exchanging SOAP messages over a channel established between client and service endpoints. The WCF channel model exposes data types and methods that enable you to operate directly on the WCF channel architecture. The WCF channel model provides you with direct control over the contents of the SOAP messages you create and over the way both your application and the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] consume them. However, creating well-formed SOAP messages to send over a channel and validating the reply messages returned can be a detailed and exacting task.  
  
 The WCF service model uses proxy classes to invoke operations on a target service or to receive operations from a client. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes the Oracle E-Business Suite as a WCF service on which you can invoke operations.  
  
- The proxy class used to invoke operations on a target service is called a WCF client class. This class models the operations exposed by a service as .NET methods with strongly-typed parameters. By using the WCF service model, you can invoke the operations exposed by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] as .NET methods on the WCF client. For more information about WCF clients, see [WCF Client Overview](https://msdn.microsoft.com/library/ms735103.aspx).
  
  You can use either of the following tools to generate a WCF client class and associated helper code from the service metadata that the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes:  
  
- **The ServiceModel Metadata Utility Tool (svcutil.exe)**, which ships with WCF.  
  
- **The [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]**, which ships with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] and is integrated with the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] design experience. This tool presents a standard Microsoft Windows interface that provides powerful browsing and searching capabilities on operations that the adapter exposes. For more information about how to generate a WCF client, see [Generate a WCF Client or a WCF Service Contract for Oracle E-Business Suite Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
## In This Section  
 The following topics give information about how to develop applications that use the WCF service model:  
  
-   [Overview of the WCF Service Model with the Oracle E-Business Suite Adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md)  
  
-   [Metadata and the WCF Service Model with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/metadata-and-the-wcf-service-model-with-oracle-e-business-suite.md)  
  
-   [Generate a WCF Client or a WCF Service Contract for Oracle E-Business Suite Solution Artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md)  
  
-   [Configure a Client Binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md)  
  
-   [Performing Insert, Update, Delete, or Select Operations on Interface Tables and Views Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)  
  
-   [Complete Operations on Tables with Large Data Types in Oracle E-Business Suite Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md)  
  
-   [Invoke Concurrent Programs in Oracle E-Business Suite Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [Invoke Request Sets in Oracle E-Business Suite Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-request-sets-in-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [Performing ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations in Oracle E-Business Suite Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-ebs/executereader-executescalar-executenonquery-in-oracle-ebs-with-a-wcf-service.md)  
  
-   [Poll Oracle E-Business Suite Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)  
  
-   [Receive Oracle E-Business Suite Database Change Notifications Using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-the-wcf-service-model.md)  
  
## See Also  
[Develop your Oracle E-Business Suite applications](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)