---
title: "Develop BizTalk applications using the SQL adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5471f28e-bce1-4295-b56d-954690e60749
caps.latest.revision: 31
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Develop BizTalk applications using the SQL adapter
Developing BizTalk applications involves creating a BizTalk project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] to generate XML schema. Once you have generated the schema, you can either use Content-Based Routing (CBR) or create BizTalk orchestrations to send and receive messages that conform to the generated schema.  
  
 CBR can be used in scenarios where the messages being sent to SQL Server do not require any intensive processing. For example, if you know that the receive port will receive messages only of a certain type, you can add a filter to the send port to route messages that match the filter expression to the send port.  
  
 In BizTalk orchestrations, you create send and receive ports to send and receive messages to and from the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which in turn sends the messages to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. This section provides information about using BizTalk orchestrations to perform operations on SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in turn uses the [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], which can interact with a WCF binding.  
  
> [!IMPORTANT]
>  To use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you must always set the **EnableBizTalkCompatibilityMode** binding property to **True**. For information about how to set binding properties, see [Configure the binding properties for the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
## In This Section  
  
-   [Prerequisites to create SQL applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md) 
  
-   [Building blocks to develop BizTalk applications with the SQL adapter](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md) 
  
-   [Insert, Update, Delete, and Select Operations on Tables and Views with the SQL adapter](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md)  
  
-   [Run Operations on Tables and Views with Large Data Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md)  
  
-   [Execute Stored Procedures in SQL Server by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)  
  
-   [Execute Stored Procedures With a Single XML Parameter](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-with-a-single-xml-parameter-in-sql-using-biztalk.md)  
  
-   [Execute Stored Procedures Having a FOR XML Clause in SQL Server using BizTalk server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)  
  
-   [Run Composite Operations on SQL Server by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)  
  
-   [Invoke Scalar Functions in SQL Server by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-using-biztalk-server.md)  
  
-   [Invoke Table-Valued Functions in SQL Server by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md) 
  
-   [Performing ExecuteReader, ExecuteScalar, or ExecuteNonQuery Operations by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)  
  
-   [Polling SQL Server by Using the SQL Adapter with BizTalk Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)  
  
-   [Receive SQL Query Notifications by Using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)  
  
## See Also  
[Develop your SQL applications](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)