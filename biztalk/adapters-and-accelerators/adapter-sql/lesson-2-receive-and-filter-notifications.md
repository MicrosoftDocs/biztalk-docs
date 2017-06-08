---
title: "Lesson 2: Receive and Filter Notifications | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b5ec679c-1c67-4bf4-aa88-0787373343f5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 2: Receive and Filter Notifications
In this lesson, you start creating an orchestration that receives notifications for changes to the **Employee** table. After the orchestration receives the notification, it extracts the type of notification and if the notification type is for an Insert operation on the **Employee** table, an “if” condition is used to perform subsequent tasks. In this lesson, you will perform the following tasks:  
  
1.  Add a one-way receive port and a **Receive** shape to the orchestration to receive the notification message.  
  
2.  Add an **Expression** shape that contains an xpath query to extract the type of notification.  
  
3.  After the notification type is known, add a filter to the orchestration by including a **Decide** shape. This shape decides whether the notification is for an Insert notification and then performs subsequent operations. If the notification is not for an Insert operation, the orchestration does not do anything.  
  
## In This Section  
  
-   [Step 1: Add Orchestration Shapes to Receive Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)  
  
-   [Step 2: Extract Notification Type from Notification Message](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)  
  
-   [Step 3: Add a Filter for Insert Notifications](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md)