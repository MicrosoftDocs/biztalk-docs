---
title: "Develop your Oracle E-Business Suite applications in BizTalk | Microsoft Docs"
description: Create Oracle EBS applications using WCF, or in BizTalk Server with the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7b1ebff-b3f8-4e07-a089-d1d5bfb78d56
caps.latest.revision: 32
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop your Oracle E-Business Suite applications

## Overview
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] binding. Client applications can consume the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to invoke operations on Oracle E-Business Suite artifacts. The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] can be consumed:  
  
- Through a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
- By invoking methods on an instance of a client proxy.  
  
- By sending SOAP messages over a channel instance in code that uses the WCF channel model.  

## BizTalk vs WCF service vs WCF channel 
  
 The following table:  
  
- Lists the different operations that can be performed on Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
- Provides links to the topics containing information about performing the task using the chosen approach ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], WCF service model or WCF channel model).  
  
|Operation|BizTalk Server|WCF Service Model|WCF Channel Model|  
|---|---|---|---|  
|Performing operations on interface tables and views | [Insert, update, delete, or select on interface tables and interface views with Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-or-select-on-interface-tables-and-views-with-oracle-ebs.md) |[Insert, update, delete, or select operations on interface tables and views using the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)|[Run an insert operation on an interface table in Oracle E-Business Suite using the WCF channel model](../../adapters-and-accelerators/adapter-oracle-ebs/insert-on-an-interface-table-in-oracle-ebs-using-the-wcf-channel-model.md)|  
|Performing operations on tables and views with large data types | [Complete operations on tables with large data types in Oracle E-Business Suite using the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md) |[Complete operations on tables with large data types in Oracle E-Business Suite using the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/run-table-operations-with-large-data-types-in-oracle-ebs-using-a-wcf-service.md)||  
|Performing composite operations on Oracle database | [Complete composite operations on Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/complete-composite-operations-on-oracle-e-business-suite.md)|||  
|Invoking concurrent programs in Oracle E-Business Suite | [Invoke concurrent programs in Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-concurrent-programs-in-oracle-e-business-suite.md) | [Invoke concurrent programs in Oracle E-Business Suite using the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/run-concurrent-programs-in-oracle-e-business-suite-using-the-wcf-service-model.md)||  
|Invoking request sets in Oracle E-Business Suite | [Invoke request sets in Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-request-sets-in-oracle-e-business-suite.md) | [Invoke request sets in Oracle E-Business Suite using the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/invoke-request-sets-in-oracle-e-business-suite-using-the-wcf-service-model.md)||  
|Performing ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations| [ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/executereader-executescalar-or-executenonquery-in-oracle-e-business-suite.md) |[ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in Oracle E-Business Suite using the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/executereader-executescalar-executenonquery-in-oracle-ebs-with-a-wcf-service.md)||  
|Polling Oracle database Using BizTalk Server|[Poll Oracle E-Business Suite using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)|[Poll Oracle E-Business Suite using the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)||  
|Receiving database change notifications from Oracle E-Business Suite|[Receive Oracle Database Change Notifications Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)|[Receive Oracle E-Business Suite database change notifications using the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-the-wcf-service-model.md)|[Poll Oracle E-Business Suite using SELECT statement with the WCF channel model](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement-with-the-wcf-channel-model.md)|  

## Next steps  
 The topics in this section provide information, procedures, and examples to help you develop applications that consume the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] in both [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and .NET programming solutions. 
  
-   [Create a connection to Oracle EBS](create-a-connection-to-oracle-e-business-suite.md)
-   [Get metadata for Oracle EBS operations in Visual Studio](get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)
-   [Working with the binding properties](read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)
-   [Receive polling-based data-changed messages](receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md)
-   [Enable transactions using MSDTC](enable-ms-dtc-to-allow-transactions-for-oracle-e-business-suite-adapter.md)
-   [Develop BizTalk applications using the Oracle EBS adapter](develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)
-   [Develop applications using the WCF Service Model](develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)
-   [Develop applications using the WCF Channel Model](develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)
-   [Use the Oracle EBS adapter with SharePoint](use-the-oracle-e-business-suite-adapter-with-sharepoint.md)
-   [Samples](samples-for-the-oracle-ebs-adapter.md)
-   [Configure transaction properties and application context](configure-transaction-properties-and-application-context-in-oracle-ebs-adapter.md)
  
