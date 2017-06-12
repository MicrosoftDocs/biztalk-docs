---
title: "Message Schemas for Query Notification | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5183655-64d4-4767-a923-0a575e3708cd
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for Query Notification
The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces the Notification operation to receive query notifications from the SQL Server database.  
  
 You configure the Notification operation by setting binding properties in the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. For more information about the Notification-related binding properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). You set the **NotificationStatement** binding property to specify a SQL statement (SELECT or EXEC \<stored procedure>) for the query notification. The result set of this query is returned as strongly-typed data to your code in the Notification operation.  
  
## Message Structure for the Notification Operation  
 The following table shows the XML message structure for the Notification operation.  
  
|Operation|XML Message|Description|  
|---------------|-----------------|-----------------|  
|Notification|`<?xml version="1.0" encoding="utf-8" ?>  <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification">    <Info>Value</Info>    <Source>Value</Source>    <Type>Value</Type> </Notification>`|This is the inbound message that is sent by the SQL Server to the adapter clients. In the message:<br /><br /> - The `<Info>` tag indicates the reason for the notification. For example, an “insert” value in this tag indicates that data has been inserted in one or more of the tables referenced in the notification statement.<br /><br /> - The `<Source>` tag indicates the source for the notification. For example, a “data” value in this tag indicates a change in the data in a referenced object. Similarly, an “object” value in this tag indicates a change in a referenced object.<br /><br /> - The `<Type>` tag indicates the type of data change. Query notification messages are of two types: change and subscribe. A “change” value in the `<Type>` tag indicates that the results of the query have changed, whereas a “subscribe” value in the `<Type>` tag indicates that a subscription request failed.<br /><br /> For more information about the query notification message tags, see the “Properties” section at [http://go.microsoft.com/fwlink/?LinkId=122393](http://go.microsoft.com/fwlink/?LinkId=122393).|  
  
## Message Action for the Notification Operation  
 The message action for the notification operation is “Notification.”  
  
## See Also  
[Technical reference](../../adapters-and-accelerators/adapter-sql/technical-reference-for-the-sql-adapter.md)