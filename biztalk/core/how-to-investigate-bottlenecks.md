---
title: "How to Investigate Bottlenecks | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ca22d07-d5fe-4dfb-8b52-3be3a95b0d6f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Investigate Bottlenecks
This topic describes a recommended process for how to investigate bottlenecks.  
  
## What is the Source of the Problem?  
 The source of the problem could be hardware or software related. When resources are underutilized it is usually an indication of a bottleneck somewhere in the system. Bottlenecks can be caused either due to hardware limitations or due to inefficient software configurations or both.  
  
 Identifying bottlenecks is an incremental process whereby alleviating one bottleneck can lead to the discovery of the next one. The science of identifying and alleviating these bottlenecks is the objective of this topic. It is possible for a system to perform at peaks for short periods of time. However, for sustainable throughput a system can only process as fast as its slowest performing component.  
  
## Using a Serial Approach  
 Bottlenecks can occur at the endpoints (entry/exit) of the system or somewhere in the middle (orchestration/database). After the location of the bottleneck has been isolated a structured approach can be undertaken to identify the source. After the bottlenecks have been alleviated it is essential to measure performance again to ensure that a new bottleneck has not been introduced elsewhere in the system further down the line.  
  
 The process of identifying and fixing bottlenecks should be done in a serial manner whereby only one parameter at a time should be varied and then performance measured to verify the impact of that single change. Varying more than one parameter at a time could conceal the effect of the change.  
  
 For example, changing parameter 1 could improve performance however, changing parameter 2 in conjunction with changing parameter 1 could have a detrimental effect negating the benefits of changing parameter 1 thus leading to a net zero effect. However, this results in a false negative on the effect of varying parameter 1 and a false positive on the effect of varying parameter 2.  
  
## Testing Consistency  
 Measuring performance characteristics after changing settings is imperative to validate the effect of the change.  
  
-   Hardware: It is important to use consistent hardware as varying the hardware can display inconsistent behavior producing misleading results e.g. do not use a laptop.  
  
-   Test Run Duration: It is also important to measure performance for a fixed minimum period to ensure that the results are indeed sustainable and not simply peaks. Another reason to run tests for longer periods is to ensure that the system has gone through the initial warm/ramp up period where all caches are populated, database tables have reached expected counts and throttling is given sufficient time to kick in and regulate throughput once predefined thresholds are hit. This approach will help discover optimal sustainable throughput.  
  
-   Test Parameters: It is also imperative to not vary test parameters from test run to test run. For example, varying map complexity and/or document sizes can produce different throughput and latency results.  
  
-   Clean State: Once a test is complete it is important to cleanup all state before running the next test run. For example, historical data can buildup in the database impacting runtime throughput. Recycling the service instances help to release cached resources like memory, database connections and threads.  
  
## Expectations: Throughput versus Latency  
 It is reasonable to expect a certain amount of throughput and/or latency from the deployed system. Attempting to have both high throughput & low latency is like pulling in two different directions. However it is realistic to expect optimal throughput with reasonable latency. As throughput improves increased stress (higher CPU consumption, higher disk-IO contention, memory pressure, greater lock contention) is placed on the system which can have a negative impact on latency. To discover optimal capacity of a system it is imperative to identify and alleviate any and all bottlenecks.  
  
 Bottlenecks can be caused by legacy data (completed instances) residing in the database not cleaned out. When this occurs performance can degrade. Giving the system sufficient time to drain can help alleviate the problem. However, discovering the cause of the backlog buildup and helping alleviate the issue is important.  
  
 To discover the cause of the backlog, it is important to analyze historical data, monitor Performance Monitor counters (to discover usage patterns, and diagnose the source of the backlog). This is a common situation where large volumes of data are processed in a batched manner on a nightly basis. Discovering the capacity of the system and its ability to recover from a backlog can be useful in estimating hardware requirements for handling overdrive scenarios and the amount of buffer room to accommodate within a system to handle unforeseen spikes in throughput.  
  
 Tuning the system for optimal sustainable throughput requires an in depth understanding of the application being deployed, the strengths and weaknesses of the system and usage patterns of the specific scenario. The only way to discover bottlenecks and predict optimal sustainable throughput with certainty is through thorough testing on a topology that closely matches what will be used in production.  
  
 Other topics in this section guides you through the process of defining that topology, and provides guidance on how to alleviate bottlenecks and hopefully help to avoid bottlenecks in the first place.  
  
## Scaling  
 Bottlenecks can occur at various stages of the deployed topology. Some bottlenecks can be addressed by upgrading hardware. Hardware can be upgraded either by scaling-up (more CPU’s, memory or cache) or by scaling-out (additional servers). The decision to scale up/out depends on the type of bottleneck encountered and the application being configured. The following will help with guidance on how to change hardware deployment topologies based on bottlenecks encountered. An application needs to be built from the ground up to be capable of taking advantage of scaling up/out. For example:  
  
-   Scaling up a server with additional CPU’s and/or memory may not help alleviate the problem if the application is serialized and dependent on a single thread of execution.  
  
-   Scaling out a system with additional servers may not help if the additional servers simply add contention on a common resource that cannot be scaled. However, scaling-out provides additional benefits. Deploying two dual-proc servers instead of one quad-proc server helps provide a redundant server that serves the dual purpose of scaling to handle additional throughput and provides a highly available topology.