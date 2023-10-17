---
title: "Develop your Oracle Database applications in BizTalk Server | Microsoft Docs"
description: Create Oracle DB applications using WCF, or in BizTalk Server with the BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4a685b2-ac17-4949-bc77-001f56450847
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop your Oracle Database applications

## Overview
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding. Client applications can consume the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to invoke operations on Oracle database artifacts. The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] can be consumed:  
  
- Through a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
- By invoking methods on an instance of a [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] client proxy.  
  
- As a hosted [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service.  
  
- By sending SOAP messages over a channel instance in code that uses the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model.  

## BizTalk vs WCF service vs WCF channel  
 The following table:  
  
- Lists the different operations that can be performed on an Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
- Provides links to the topics containing information about performing the task using the chosen approach ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], WCF service model, or WCF channel model).  
  
|Task|BizTalk Server|WCF Service Model|WCF Channel Model|  
|----------|--------------------|-----------------------|-----------------------|  
|Basic Insert, Update, Delete, and Select operations on tables and views|[Insert, update, delete, or select operations using BizTalk Server with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-using-biztalk-server-with-oracle-db.md)|[Insert, update, delete, or select operations in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md)|[Run an Insert Operation in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)|  
|Operations on tables and views containing LOB data|[Run operations on tables with large object data types in Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-object-data-types-in-oracle-database.md)|[Complete operations on tables with large data types in Oracle Database using the WCF service model](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-data-types-in-oracle-db-using-a-wcf-service.md)||  
|Operations on functions and stored procedures|[Invoke Functions and Procedures in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md)|[Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)|[Invoke a Function in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)|  
|Invoking overloaded functions and procedures|[Invoke Overloaded Functions and Procedures in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md)|[Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)||  
|Operations on functions and procedures With REF CURSOR parameters|[Invoke Functions and Procedures with REF CURSORS in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-ref-cursors-in-oracle-db-using-biztalk-server.md)|[Run Operations Using REF CURSORS in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)||  
|Operations on functions and procedures with RECORD types|[Invoke Functions and Procedures with RECORD Types in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md)|[Run Operations Using RECORD Types in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)||  
|Operations on tables and views with BFILE data types|[Run operations on Tables with BFILE Data Types in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md)|||  
|SQLEXECUTE operation|[Run SQLEXECUTE operation in Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-biztalk-server.md)|[Run SQLEXECUTE operation in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)|[Run a SQLEXECUTE Operation in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)|  
|Receiving polling-based data-change messages|[Poll Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-biztalk-server.md)|[Receive Polling-based Data-changed Messages in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md)|[Receive Polling-based Data-changed Messages in Oracle Database using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)|  
|Performing Composite Operations on the Oracle Database|[Run Composite Operations on Oracle Database using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)|||  
|Receiving Database Change Notifications|[Receive Oracle Database Change Notifications Using BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)|[Receive Oracle Database Change Notifications Using the WCF Service Model1](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-the-wcf-service-model1.md)||  
  

  
## Next steps
 The topics in this section provide information, procedures, and examples to help you develop applications that consume the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] in both [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] programming solutions. 
  
-   [Create a connection to the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)
  
-   [Get metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) 
  
-   [Configure the binding properties for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)
  
-   [Streaming large object data types in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)
  
-   [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)
  
-   [Developing BizTalk Server Applications](../../core/developing-biztalk-server-applications.md)
  
-   [Develop Oracle Database applications using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)  
  
-   [Develop Oracle Database applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)  
  
-   [Get Metadata Programmatically from the Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)  
  
-   [Use the Oracle Database Adapter with SharePoint](../../adapters-and-accelerators/adapter-oracle-database/use-the-oracle-database-adapter-with-sharepoint.md)
  
-   [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)  
  
-   [Configure transaction isolation level and transaction timeout with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)

- [Use svcutil.exe](use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md)