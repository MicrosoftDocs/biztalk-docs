---
title: "Orchestration Engine Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dcaf7517-da4a-4ed0-a3bb-7e9b73931bff
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Orchestration Engine Performance Counters
The orchestration engine maintains several performance counters that you can examine with Performance Monitor to see how many orchestration instances and transactions are being processed by the engine over time.  
  
 To run Performance Monitor, go to the **Start** Menu, select **Run**, type in **perfmon**, and press **Enter**. Click the **Add** button, and select **XLANG/s Orchestrations** from the **Performance Object** drop-down list.  
  
 The following performance counters are accessible for each host instance under the **XLANG/s Orchestrations** performance object category:  
  
|Counter|Comments|  
|-------------|--------------|  
|% used physical memory|Percentage used of total physical memory on the machine.|  
|Active application domains|Number of loaded orchestration application domains in the process.|  
|Average batch factor|Number of persistence points reached since the host instance started, divided by the number of underlying transactions.|  
|Database transactions|Number of database transactions performed since the host instance started.|  
|Database transactions/sec|Average number performed per second.|  
|Dehydratable orchestrations|Number of orchestrations instances that can be dehydrated which are currently hosted by the host instance.|  
|Dehydrating orchestrations|Number of orchestrations that are in the process of dehydrating.|  
|Dehydration cycle in progress|Indicates whether there is a dehydration cycle currently in progress.|  
|Dehydration cycles|Number of dehydration cycles completed.|  
|Dehydration threshold|Number in milliseconds that determines how aggressively orchestrations are being dehydrated. If the orchestration engine predicts that an instance will be dehydratable for an amount of time longer than this threshold, it will dehydrate the instance.|  
|Idle orchestrations|Number of idle orchestration instances currently hosted by the host instance. This refers to orchestrations that are not making progress but are not dehydratable, as when the orchestration is blocked waiting for a receive, listen, or delay in an atomic transaction.|  
|Megabytes allocated private memory|Megabytes of allocated private memory for the host instance.|  
|Megabytes allocated virtual memory|Megabytes reserved for virtual memory for the host instance.|  
|MessageBox database connection failures|Number of attempted database connections that failed since the host instance started.|  
|Online MessageBox databases|Number of MessageBox databases currently available to the application.|  
|Orchestrations completed|Number of orchestration instances completed since the host instance started.|  
|Orchestrations completed/sec|Average number completed per second.|  
|Orchestrations created|Number of orchestration instances created since the host instance started.|  
|Orchestrations created/sec|Average number created per second.|  
|Orchestrations dehydrated|Number of orchestration instances dehydrated since the host instance started.|  
|Orchestrations dehydrated/sec|Average number dehydrated per second.|  
|Orchestrations discarded|Number of orchestration instances discarded from memory since the host instance started. An orchestration can be discarded if the engine fails to persist its state.|  
|Orchestrations discarded/sec|Average number discarded per second.|  
|Orchestrations rehydrated|Number of orchestration instances rehydrated since the host instance started.|  
|Orchestrations rehydrated/sec|Average number rehydrated per second.|  
|Orchestrations resident in memory|Number of orchestration instances currently hosted by the host instance.|  
|Orchestrations scheduled for dehydration|Number of dehydratable orchestrations for which there is a dehydration request pending.|  
|Orchestrations suspended|Number of orchestration instances suspended since the host instance started.|  
|Orchestrations suspended/sec|Average number suspended per second.|  
|Pending messages|Number of received messages for which receipt has not yet been acknowledged to the message box.|  
|Pending work items|Number of code execution blocks that are scheduled for execution.|  
|Persistence points|Number of times an orchestration instance has persisted its state to the database since the host instance started.|  
|Persistence points/sec|Average number of orchestration instances persisted per second.|  
|Runnable orchestrations|Number of orchestration instances ready to execute.|  
|Running orchestrations|Number of orchestration instances currently executing.|  
|Transactional scopes aborted|Number of long-running or atomic scopes that have been aborted since the host instance started.|  
|Transactional scopes aborted/sec|Average number aborted per second.|  
|Transactional scopes committed|Number of long-running or atomic scopes that have successfully completed since the host instance started.|  
|Transactional scopes committed/sec|Average number committed per second.|  
|Transactional scopes compensated|Number of long-running or atomic scopes that have successfully completed compensation scopes since the application started.|  
|Transactional scopes compensated/sec|Average number compensated per second.|  
  
## See Also  
 [Engine Performance Characteristics](../core/engine-performance-characteristics.md)   
 [Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md)