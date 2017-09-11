---
title: "Message Schemas for the Notification Operation2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dddab2ef-94db-46c8-95c1-57517681e8dd
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for the Notification Operation
The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]surfaces the Notification operation to receive database change notifications from the underlying database in Oracle E-Business Suite.  
  
 You configure the Notification operation by setting binding properties in the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. For more information about the Notification-related binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite binding properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). You set the **NotificationStatement** binding property to specify a SELECT statement for the query notification.  
  
## Message Structure for the Notification Operation  
 The following table shows the XML message structure for the Notification operation.  
  
|Operation|XML Message|Description|  
|---------------|-----------------|-----------------|  
|Notification|`<?xml version="1.0" encoding="utf-8" ?>  <Notification xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Notification">    <Info>Value</Info>    <Source>Value</Source>    <Type>Value</Type> </Notification>`|This is the inbound message that is sent by Oracle E-Business Suite to the adapter clients. In the message:<br /><br /> - The `<Info>` tag indicates the reason for the notification. For example, an “insert” value in this tag indicates that data has been inserted in one or more of the tables referenced in the notification statement.<br /><br /> - The `<Source>` tag indicates the source for the notification. For example, a “data” value in this tag indicates a change in the data in a referenced object. Similarly, an “object” value in this tag indicates a change in a referenced object.<br /><br /> - The `<Type>` tag indicates the type of data change. For example, an “Update” value in the `<Type>` tag indicates that the results of the query have been updated.|  
  
## Message Action for the Notification Operation  
 The message action for the notification operation is “Notification.”  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)