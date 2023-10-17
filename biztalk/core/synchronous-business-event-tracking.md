---
description: "Learn more about: Synchronous Business Event Tracking"
title: "Synchronous Business Event Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performance, BAM"
  - "events, tracking [BAM]"
  - "BAM, event tracking"
  - "BAM, performance"
ms.assetid: 302c7918-bc62-46f1-a949-fbf94a7073e3
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Synchronous Business Event Tracking
The simplest way to send event data to BAM is to use an instance of the class DirectEventStream. This class saves the event data directly into the BAM Primary Import Database in the context of the current transaction of the application (if present).  
  
 If any error happens during this operation, the method call will throw an exception back in the calling application. This will happen for example if the name of an item passed in UpdateActivity mismatches the BAM Activity Definition, or you did not deploy the BAM Definition yet. This allows the calling application to catch and recover from any errors when saving the BAM data, which results in much easier management later.  
  
 Saving the data synchronously might have a performance impact, because the calling application has to wait until BAM executes all stored procedures and triggers.  
  
## See Also  
 [Asynchronous Business Event Tracking](../core/asynchronous-business-event-tracking.md)
