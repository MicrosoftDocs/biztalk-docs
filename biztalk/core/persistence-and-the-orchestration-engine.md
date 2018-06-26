---
title: "Persistence and the Orchestration Engine | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestration engine, persistence"
  - "persistence"
  - "orchestration engine, serialization"
ms.assetid: 088230ef-13b3-440b-9875-6449f29dd5c6
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Persistence and the Orchestration Engine
State persistence, its management and restoration form the basis of a lot of fundamental functionalities of the orchestration engine. In particular, persistence is critical to the correct functioning of:  
  
- Dehydration and rehydration  
  
- Machine agnostic execution and rehydration  
  
- Compensation model  
  
- Controlled System Shutdown  
  
- Recovery  
  
  The orchestration engine saves to persistent storage the entire state of a running orchestration instance at various points, so that the instance can later be completely restored in memory. The state includes:  
  
- The internal state of the engine, including its current progress.  
  
- The state of any .NET components that maintain state information and are being used by the orchestration.  
  
- Message and variable values.  
  
## Persistence Points  
 The orchestration engine saves the state of a running orchestration instance at various points. If it needs to rehydrate the orchestration instance, start up from a controlled shutdown, or recover from an unexpected shutdown, it will run the orchestration instance from the last persistence point, as though nothing else had occurred. For example, if a message is received but there is an unexpected shutdown before state can be saved, the engine will not record that it has received the message, and will receive it again upon restarting. The engine will save the state of an orchestration in the following circumstances:  
  
-   The end of a transactional scope is reached.  
  
    -   The engine saves state at the end of a transactional scope so that the point at which the orchestration should resume is defined unambiguously, and so that compensation can be carried out correctly if necessary.  
  
    -   The orchestration will continue to run from the end of the scope if persistence was successful; otherwise, the appropriate exception handler will be invoked.  
  
    -   If the scope is transactional and atomic, the engine will save state at the end of the atomic scope when it commits.  
  
    -   If the scope is transactional and long-running, the engine will generate a new transaction and persist the complete state of the runtime when the scope completes.  
  
-   A debugging breakpoint is reached.  
  
-   A message is sent. The only exception to this is when a message is sent from within an atomic transaction scope.  
  
-   The orchestration starts another orchestration asynchronously, as with the **Start Orchestration** shape.  
  
-   The orchestration instance is suspended.  
  
-   When the orchestration engine is asked to shut down, it will try to save control information as well as the current state of all running orchestration instances, so that it can resume running them when it is started again. If the engine is unsuccessful in saving the current state, the engine will resume the orchestration instance from the last persistence point that occurred before the shutdown. This applies to the system shutdown in controlled condition as well as abnormal termination.  
  
-   The engine determines that the instance should be dehydrated.  
  
-   The orchestration instance is finished.  
  
## Serialization  
 All object instances that your orchestration refers to directly or indirectly (as through other objects) must be serializable for your orchestration state to be persisted. There are two exceptions:  
  
-   You can have a nonserializable object declared inside an atomic transaction. You can do this because atomic scopes do not contain persistence points.  
  
-   System.Xml.XmlDocument is not a serializable class; it is handled as a special case and can be used anywhere.  
  
> [!CAUTION]
>  In order for a .NET object to be persisted, it must be marked as serializable.  
  
> [!NOTE]
>  COM objects cannot be persisted using standard .NET serialization procedures. If you want to call a COM object outside of an atomic transaction, you must wrap the COM object in a .NET object that is .NET serializable and knows how to persist and restore the state of the COM object.  
  
## System Shutdown  
 When the orchestration engine is asked to shut down, it will try to save control information as well as the current state of all running orchestration instances, so that it can resume running them when it is started again. If the engine is unsuccessful in saving the current state, the engine will resume the orchestration instance from the last persistence point that occurred before the shutdown. This applies to the system shutdown in controlled condition as well as abnormal termination.  
  
## Recovery  
 The engine regularly saves to persistent storage the state information of an orchestration instance, and it also saves state in the event of a system shutdown.  
  
 When an orchestration instance fails abnormally for whatever reason, the instance can be recovered from the last persisted state, and it can continue to run as if there were no interruption. This is true even if the original server that the instance ran on goes out of service for some reason; the instance can simply resume running on a separate machine. Because of this multi-server recovery model, you no longer need clustering.  
  
## See Also  
 [Orchestration Dehydration and Rehydration](../core/orchestration-dehydration-and-rehydration.md)