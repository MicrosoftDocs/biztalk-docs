---
title: "Develop your SQL applications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fac4b5b0-2980-4784-a081-e795654292ed
caps.latest.revision: 39
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop your SQL applications
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] binding. Client applications can consume the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to invoke operations on SQL Server artifacts. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be consumed:  
  
-   Through a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   By invoking methods on an instance of a client proxy.  
  
-   As a hosted WCF service.  
  
-   By sending SOAP messages over a channel instance in code that uses the WCF channel model.  
  
 The following table:  
  
-   Lists the different operations that can be performed on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
-   Provides links to the topics containing information about performing the task using the chosen approach ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], WCF service model, WCF channel model).  
  
|Task|BizTalk Server|WCF Service Model|WCF Channel Model|  
|----------|--------------------|-----------------------|-----------------------|  
|Performing basic Insert, Update, Delete, and Select operations on tables and views|[Insert, update, delete, or select operations using BizTalk Server with the SQL adapter](../../adapters-and-accelerators/adapter-sql/insert-update-delete-or-select-using-the-sql-adapter-in-biztalk-server.md)|[Insert, update, delete, or select operations on interface tables and views using the WCF service model](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)|[Run an Insert Operation on a Table in SQL using the WCF Channel Model](../../adapters-and-accelerators/adapter-sql/run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model.md)|  
|Performing operations on tables and views with large data type columns<br /><br /> (Also includes information about FILESTREAM operations using the adapter)|[Operations on tables and views that contain large data types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md)|[Run Operations on Tables and Views with Large Data Types in SQL using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)|-|  
|Executing stored procedures|[Execute stored procedures in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)|[Invoke Stored Procedures in SQL using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/invoke-stored-procedures-in-sql-using-the-wcf-service-model.md)|-|  
|Executing stored procedures with single parameters without using a BizTalk orchestration|[Execute stored procedures with a single XML parameter in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-with-a-single-xml-parameter-in-sql-using-biztalk.md)|-|-|  
|Executing stored procedures that contain a FOR XML clause in the definition|[Execute stored procedures having a FOR XML clause in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)|-|-|  
|Performing composite operations on SQL Server|[Run composite operations on SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)|-|-|  
|Invoking scalar functions in SQL Server|[Invoke Scalar Functions in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-using-biztalk-server.md)|[Invoke Scalar Functions in SQL Server by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model.md)|-|  
|Invoking table-valued functions in SQL Server|[Invoke Table-Valued Functions in SQL Server using BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md)|[Invoke Table-Valued Functions in SQL Server by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model.md)|-|  
|Performing **ExecuteReader**, **ExecuteScalar**, or **ExecuteNonQuery** operations|[ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations in SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)|[ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in SQL using WCF Service Model](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-executenonquery-in-sql-using-wcf-service-model.md)|-|  
|Receiving polling-based data-change messages|[Poll SQL Server using the SQL Adapter with BizTalk Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)|[Poll SQL Server using the SQL Adapter with WCF Service Model](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)|[Receive Polling-based Data-changed Messages from SQL Server by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)|  
|Receiving SQL Server notifications|[Receive SQL Query Notifications using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)|[Receive Query Notifications from SQL using the WCF Service Model](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-from-sql-using-the-wcf-service-model.md)|-|  
  
 The topics in this section provide information, procedures, and examples to help you develop applications that consume the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in both [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and .NET programming solutions. The topics also provide information on other key aspects of using the adapters such as:  
  
-   Connecting to SQL Server.  
  
-   Retrieving metadata from SQL Server.  
  
-   Using binding properties to configure the adapter.  
  
