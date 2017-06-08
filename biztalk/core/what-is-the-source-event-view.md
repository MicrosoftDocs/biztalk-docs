---
title: "What Is the Source Event View? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking Profile Editor, Source Event view"
  - "Source Event view [Tracking Profile Editor]"
  - "message schemas, Tracking Profile Editor"
  - "orchestrations, Tracking Profile Editor"
  - "Tracking Profile Editor, message schemas"
  - "Tracking Profile Editor, orchestrations"
ms.assetid: 72e74780-8590-484b-899d-cdc3d2a908be
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is the Source Event View?
The Event Source View is where the Tracking Profile Editor (TPE) presents the orchestrations or message schemas selected from the assemblies or the context properties which you map to the activity definition.  
  
 The Source Event View is presented in the right pane of user interface. The contents of the pane vary based on the data source you selected.  
  
## Event source options  
 You have four options for event sources: orchestration schedules, messaging payloads, context properties, and messaging properties.  
  
 Orchestrations and messaging payloads require that you select an assembly from which to map your data items. You then select the specific orchestrations or message payload schemas of interest from the assembly. For orchestration schedules you are given a list of the orchestrations in the assembly. Messaging payloads allow you to select from a list of messaging payload schemas, and context properties present a list of schemas in the assembly and in system schemas that are publicly available.  
  
 When you select context properties, you are first given a list of context property names. When you select the context property, the related schema of the context property is shown in the right pane. You can then map the context property to your activity by dragging and dropping the property onto an activity node.  
  
 When you select messaging properties you are given a list of the known messaging properties that you can then map to the activity.  
  
## In This Section  
  
-   [Orchestration Schedule View](../core/orchestration-schedule-view.md)  
  
-   [Messaging Payload View](../core/messaging-payload-view.md)  
  
-   [Context Property View](../core/context-property-view.md)  
  
-   [Messaging Property View](../core/messaging-property-view.md)