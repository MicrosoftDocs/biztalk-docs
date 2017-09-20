---
title: "Orchestration Dehydration Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ab92e0e-6a33-4aaa-ab14-0c82322b04d5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Orchestration Dehydration Performance Counters
The following table lists the names of Orchestration Engine performance counters that are specific to monitoring the behavior of dehydration. Use Performance Monitor to watch these counters while tuning your dehydration parameters.  
  
|Dehydration Performance Counter|Description|  
|-------------------------------------|-----------------|  
|Dehydratable orchestrations|Number of orchestrations instances that can be dehydrated which are currently hosted by the host instance.|  
|Dehydrating orchestrations|Number of orchestrations that are in the process of dehydrating.|  
|Dehydration cycle in progress|Indicates whether there is a dehydration cycle currently in progress.|  
|Dehydration cycles|Number of dehydration cycles completed.|  
|Dehydration threshold|Number in milliseconds that determines how aggressively orchestrations are being dehydrated. If the orchestration engine predicts that an instance will be dehydratable for an amount of time longer than this threshold, it will dehydrate the instance.|  
|Orchestrations dehydrated|Number of orchestration instances dehydrated since the host instance started.|  
|Orchestrations dehydrated/sec|Average number dehydrated per second.|  
|Orchestrations rehydrated|Number of orchestration instances rehydrated since the host instance started.|  
|Orchestrations rehydrated/sec|Average number rehydrated per second|  
|Orchestrations scheduled for dehydration|Number of dehydratable orchestrations for which there is a dehydration request pending.|