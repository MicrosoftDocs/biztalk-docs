---
title: "Receive query notifications After a Receive Location Breakdown in SQL using BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e70fa4c2-d81b-4eb0-a23d-871b64c881e6
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Receive query notifications After a Receive Location Breakdown in SQL using BizTalk Server
Consider a scenario where you have a BizTalk application that receives database change notification messages when changes are made to the EMPLOYEE table. If the receive location configured as part of the BizTalk application breaks down, and simultaneously records are added into the EMPLOYEE table, you will not receive notifications for the recently added records. You will also not know when the receive location is available again. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes a binding property, **NotifyOnListenerStart**, that you can configure to get a notification that the receive location has recovered. You can specify the following values for the **NotifyOnListenerStart** binding property:  
  
- Set this property to **True**, to receive a notification informing that the receive location is available, as soon as the receive location recovers.  
  
- Set this property to **False**, to not receive a notification informing that the receive location has recovered, after the receive location recovers.  
  
  Default is **True**.  
  
## Configuring the SQL Adapter Behavior  
 For either of the approaches, you do not need to perform any specific tasks while generating metadata or while configuring the BizTalk application. You only need to set the **NotifyOnListenerStart** binding property accordingly on the WCF-Custom or WCF-SQL receive location. To create the BizTalk application, you must perform the same set of tasks as described in [Receive Query Notifications Incrementally from SQL using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md). However, when configuring the BizTalk application using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you can try changing the value of the **NotifyOnListenerStart** binding property and see the difference in the two configurations.  
  
 The following figure demonstrates how the notifications are received based on the value of the **NotifyOnListenerStart** binding property.  
  
 ![Configure SQL Adapter for notifications](../../adapters-and-accelerators/adapter-oracle-database/media/4018300a-1a58-47da-ac9d-c77c13d7081d.gif "4018300a-1a58-47da-ac9d-c77c13d7081d")  
  
 Note that in the first scenario, when the **NotifyOnListenerStart** is set to **true** and records are inserted into the database table while the receive location was down, the adapter only sends you a notification message when the receive location comes back up. The adapter does not perform any operation to process the records that were inserted while the receive location was down. The adapter client must implement the relevant logic in their application to process the records that were inserted while the receive location was down.  
  
## See Also  
 [Receive SQL Query Notifications using BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)