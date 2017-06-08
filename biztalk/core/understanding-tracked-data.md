---
title: "Understanding Tracked Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instances, viewing"
  - "service instances, viewing"
  - "viewing, suspended instances"
  - "messages, viewing"
  - "viewing, service details"
  - "viewing, orchestration details"
  - "viewing, message details"
  - "orchestrations, viewing"
  - "suspended instances"
  - "instances, suspended"
ms.assetid: dcc3fbd5-cd2c-4780-a577-0ccd521cf5eb
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Understanding Tracked Data
When you run a tracking query, the tracked information appears in the results list at the bottom of the Query Results window.  
  
## Viewing message details  
 You can track message properties. You can also save tracked message bodies to a file and view them using non-Microsoft tools.  
  
-   You can right-click any message referenced by a service instance and select Message details.  
  
-   If the message is already processed but it was tracked—because you had tracking turned on—you can save it to your hard disk and examine it.  
  
-   You can attach to the orchestration instance and use the Orchestration Debugger.  
  
## Viewing service events  
 When a suspended service appears in the event log, you can investigate a service by using the **Message Flow**, **Orchestration Debugger**, **Show Tracked Message Events**, **Show Live Service Instances**, options from the **Context** menu.  
  
## Viewing orchestration events  
 Use the Orchestration Debugger to view the path a message instance has taken through an orchestration. As you step through, a rendered image of the orchestration shows the progress of the message, and allows you to place breakpoints in the orchestration for debugging purposes.  
  
## In This Section  
  
-   [What is Message Tracking?](../core/what-is-message-tracking.md)  
  
-   [What is Event Tracking?](../core/what-is-event-tracking.md)