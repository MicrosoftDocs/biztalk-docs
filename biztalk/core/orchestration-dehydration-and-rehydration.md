---
title: "Orchestration Dehydration and Rehydration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57d7c0bf-a707-4ebd-afab-e75dd80c3c34
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Orchestration Dehydration and Rehydration
When many long-running business processes are running at the same time, memory and performance are potential issues. The orchestration engine addresses these issues by "dehydrating" and "rehydrating" orchestration instances.  
  
 Dehydration is the process of serializing the state of an orchestration into a SQL Server database. Rehydration is the reverse of this process: deserializing the last running state of an orchestration from the database. Dehydration is used to minimize the use of system resources by reducing the number of orchestrations that have to be instantiated in memory at one time.  
  
## Dehydration  
 The orchestration engine might determine that an orchestration instance has been idle for a relatively long period of time. It calculates thresholds to determine how long it will wait for various actions to take place, and if those thresholds are exceeded, it dehydrates the instance. This can occur under the following circumstances:  
  
- When the orchestration is waiting to receive a message, and the wait is longer than a threshold determined by the engine.  
  
- When the orchestration is "listening" for a message, as it does when you use a **Listen** shape, and no branch is triggered before a threshold determined by the engine. The only exception to this is when the **Listen** shape contains an activation receive.  
  
- When a delay in the orchestration is longer than a threshold determined by the engine.  
  
  The engine dehydrates the instance by saving the state, and frees up the memory required by the instance. By dehydrating dormant orchestration instances, the engine makes it possible for a large number of long-running business processes to run concurrently on the same computer.  
  
  You can set 12 properties to configure how dehydration works in BizTalk Server. The topics in this section list and describe these properties and their default values, and discuss how various values affect dehydration behavior.  
  
## Rehydration  
 The orchestration engine can be triggered to rehydrate an orchestration instance by the receipt of a message or by the expiration of a time-out specified in a Delay shape. It then loads the saved orchestration instance into memory, restores its state, and runs it from the point where it left off. For more information about using shapes in orchestrations, see [Orchestration Shapes](../core/orchestration-shapes.md).  
  
 An orchestration can be configured to run on more than one server. After an orchestration instance has been dehydrated, it can be rehydrated on any of these servers. If one server goes down, the engine continues to run the orchestration on a different server, continuing from its previous state. The engine also takes advantage of this feature to implement load balancing across servers.  
  
## Next steps
  
-   [Dehydration Default Properties](../core/dehydration-default-properties.md)  
  
-   [How to Calculate Dehydration](../core/how-to-calculate-dehydration.md)  
  
-   [Sample Dehydration Calculation](../core/sample-dehydration-calculation.md)  
  
-   [Orchestration Dehydration Performance Counters](../core/orchestration-dehydration-performance-counters.md)  
  
-   [BTSNTSvc.exe.config File](../core/btsntsvc-exe-config-file.md)  
  
-   [Other Activities That Can Affect Dehydration Behavior](../core/other-activities-that-can-affect-dehydration-behavior.md)