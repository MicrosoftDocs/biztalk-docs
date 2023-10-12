---
description: "Learn more about: Planning for Message and Instance Tracking"
title: "Planning for Message and Instance Tracking"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Planning for Message and Instance Tracking
You should decide during the planning stages which information you need to track, so that after you deploy the project you can set the tracking options and limit the amount of tracked data to give you only the information you need.  
  
 We recommend that you do not track all messages, because each time a message is touched, BizTalk Server message and server instance tracking makes another copy. For example, you can narrow the scope by tracking only a specific port. This helps to maximize the performance of your system and keep the databases uncluttered.  
  
## See Also  
 [Management and Tracking Architecture](../core/management-and-tracking-architecture.md)
