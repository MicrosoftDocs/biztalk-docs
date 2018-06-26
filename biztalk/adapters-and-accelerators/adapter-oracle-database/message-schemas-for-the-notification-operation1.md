---
title: "Message Schemas for the Notification Operation1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f98d76d0-6084-4de7-b6ff-124202ca92ab
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for the Notification Operation
The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces the Notification operation to receive database change notifications from the Oracle database.  
  
 You configure the Notification operation by setting binding properties in the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. For more information about the Notification-related binding properties, see [Read about the Oracle Database adapter binding properties](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). You set the **NotificationStatement** binding property to specify a SELECT statement for the query notification.  
  
## Message Structure for the Notification Operation  
 The following table shows the XML message structure for the Notification operation.  
  
|Operation|XML Message|Description|  
|---------------|-----------------|-----------------|  
|Notification|`<?xml version="1.0" encoding="utf-8" ?>  <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification">    <Info>Value</Info>    <Source>Value</Source>    <Type>Value</Type> </Notification>`|This is the inbound message that is sent by the Oracle database to the adapter clients. In the message:<br /><br /> - The `<Info>` tag indicates the reason for the notification. For example, an “insert” value in this tag indicates that data has been inserted in one or more of the tables referenced in the notification statement.<br /><br /> - The `<Source>` tag indicates the source for the notification. For example, a “data” value in this tag indicates a change in the data in a referenced object. Similarly, an “object” value in this tag indicates a change in a referenced object.<br /><br /> - The `<Type>` tag indicates the type of data change. For example, an “Update” value in the `<Type>` tag indicates that the results of the query have been updated.|  
  
## Message Action for the Notification Operation  
 The message action for the notification operation is “<http://Microsoft.LobServices.OracleDB/2007/03/Notification”>.  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)