---
title: "Messages and Message Schemas for BizTalk Adapter for SQL Server | Microsoft Docs"
description: XML structure of messages and data types used by the SQL Server adapter for BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e95c6342-5420-4fb8-9b41-7c87d27b5b68
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Messages and Message Schemas for BizTalk Adapter for SQL Server

## Overview
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding. It exposes operations that applications can invoke on it and that it can, in turn, invoke on applications. These operations are invoked by sending SOAP messages over a channel. If a response is required, it is returned in a SOAP message over the same channel.  
  
 As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms. The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses.  
  
## In This Section  
  
-   [Basic SQL Server Data Types](../../adapters-and-accelerators/adapter-sql/basic-sql-server-data-types.md)  
  
-   [Message Schemas for Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)  
  
-   [Message Schemas for Procedures and Functions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)  
  
-   [Message Schemas for the Polling and TypedPolling Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)  
  
-   [Message Schemas for Query Notification](../../adapters-and-accelerators/adapter-sql/message-schemas-for-query-notification.md)  
  
-   [Message Schemas for Composite Operations](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)  
  
-   [Message Schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-sql/executenonquery-executereader-and-executescalar-message-schemas-in-sql.md)  
  
