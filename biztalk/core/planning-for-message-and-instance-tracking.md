---
title: "Planning for Message and Instance Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HAT, planning"
  - "planning, HAT"
ms.assetid: 69b0d30e-77df-4847-9a59-6dd806152b71
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for Message and Instance Tracking
You should decide during the planning stages which information you need to track, so that after you deploy the project you can set the tracking options and limit the amount of tracked data to give you only the information you need.  
  
 We recommend that you do not track all messages, because each time a message is touched, BizTalk Server message and server instance tracking makes another copy. For example, you can narrow the scope by tracking only a specific port. This helps to maximize the performance of your system and keep the databases uncluttered.  
  
## See Also  
 [Management and Tracking Architecture](../core/management-and-tracking-architecture.md)