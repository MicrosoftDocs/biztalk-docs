---
title: "What Is Host Throttling? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "host throttling, outbound"
  - "host throttling, inbound"
  - "host throttling, about host throttling"
ms.assetid: 36d1818b-c8a2-4f23-bfb3-c034ee242f69
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is Host Throttling?
Most of the processing that takes place on a BizTalk server occurs within a logical entity known as a BizTalk Server host instance, which is a process running as a Windows service or an isolated host process on the BizTalk server. To manage the use of resources by a host instance process, BizTalk Server utilizes an adjustable throttling mechanism that governs the flow and processing of messages through a host instance.  
  
 The throttling mechanism moderates the workload of the host instance to ensure that the workload does not exceed the capacity of the host instance or any downstream host instances. The throttling mechanism also prevents a condition known as resource contention that can lower the overall performance of the host instance process or other system processes. Resource contention occurs when one or more processes consume a limited resource to the detriment of themselves and/or another process. For example, the consumption of excessive memory or threads can lead to memory allocation failure or high thread context-switches, which can impact the performance of the process. Resource contention like this can be detrimental to the overall performance of BizTalk Server.  
  
 The host throttling mechanism also detects when available resources are being underutilized. If available resources are underutilized then the throttling mechanism allows additional messages to be processed by a host instance. The host throttling mechanism continually monitors if available resources are being over or underutilized and adjusts message flow through the host instance accordingly.  
  
 The BizTalk Server host throttling mechanism helps to ensure that the system operates at an optimal and sustainable level.  
  
 Host throttling configuration parameters are set on a per host basis in the BizTalk Server Administration console. Note that the throttling configuration parameters that are set for the host apply to any or all receive handlers, send handlers, or orchestrations that are housed in the corresponding host instances. If you want to set throttling parameters that will apply only to a specific receive handler, send handler, or orchestration then you should do the following:  
  
-   Create a new host and set the throttling parameters appropriately.  
  
-   Configure the receive handler, send handler, or orchestration to run in this host.  
  
-   Create one or more instances of this host to run on your BizTalk server(s).  
  
## Inbound host throttling  
 Inbound host throttling, also known as *message publishing throttling* in BizTalk Server, is applied to host instances that contain receive adapters or orchestrations that publish messages to the MessageBox database. An inbound host throttling condition can be triggered under the following conditions:  
  
- The amount of memory, the number of threads, or the number of database connections used by the host instance exceeds the throttling thresholds defined in **Settings Dashboard** available in the BizTalk Group and selecting **Settings**. These values are measurable with performance monitor counters available under the **BizTalk:Message Agent** performance object category.  
  
- Downstream hosts are unable to process the messages that are published. This increases the value of the **Message count in DB** parameter. The threshold at which the **Message count in DB** value triggers a throttling condition is configurable on the **Hosts** option in **Settings Dashboard**. The message count in database can be measured with the **Database Size** counter under the **BizTalk:Message Agent** performance object category.  
  
- The **Message publishing incoming rate** for the host instance exceeds the **Message publishing outgoing rate\\*** the specified **Rate overdrive factor** value. The **Rate overdrive factor** value is defined in **Settings Dashboard**, **Hosts** and then **Rate-Based Throttling**. The message publishing incoming and outgoing rates can be measured with the corresponding performance monitor counters under the **BizTalk:Message Agent** performance object category.  
  
- The default throttling behavior has been modified. [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) describes the different values that impact throttling behavior.  
  
  Depending on the severity of the throttling condition, the following actions are taken:  
  
- A progressive delay in the processing logic of the host instance is implemented. The delay may be implemented when an End Point Manager (EPM) thread receives a batch of messages from the transport adapter, and/or when the EPM submits a batch of messages to be published into the MessageBox database. Both the duration of the processing delay and the rate at which the duration is incremented scale with the severity of the throttling condition.  
  
- The number of threads that are available to the End Point Manager (EPM) is restricted. The EPM receives batches of messages from adapters and publishes the messages to the MessageBox database. By default, the EPM is configured to use 20 threads per CPU. If the host throttling mechanism detects a stress condition for inbound processing then it can temporarily reduce the number of threads available to the EPM until the stress condition is eliminated. The EPM cannot process messages from transport adapters or deliver message batches to the MessageBox database unless an EPM thread is available to service the inbound message batch.  
  
- The use of memory and other resources is reduced as applicable. BizTalk Server can send instructions to other service classes to limit memory use by dehydrating running schedules, shrinking memory cache size, and by limiting the usage of memory-intensive threads.  
  
  **Inbound message flow from Adapter to MessageBox**  
  
  ![Inbound Message flow from Adapter to MessageBox](../core/media/inboundmsgflow.gif "InboundMsgFlow")  
  
## Outbound host throttling  
 Outbound host throttling, also known as *message processing throttling* in BizTalk Server, is applied to host instances that contain orchestrations or send adapters that receive and deliver or process messages that have been published to the MessageBox. An outbound host throttling condition can be triggered under the following conditions:  
  
- The amount of memory, the number of threads, or the number of database connections used by the host instance exceeds the throttling thresholds defined in **Resource-Based Throttling** in **Settings Dashboard**. These values are measurable with performance monitor counters available under the **BizTalk:Message Agent** performance object category.  
  
- The **Message delivery incoming rate** for the host instance exceeds the **Message delivery outgoing rate** \* the specified **Rate overdrive factor** value. The **Rate overdrive factor** value is defined on the **Rate-Based Throttling** tab in **Settings Dashboard**. The message delivery incoming and outgoing rates can be measured with the corresponding performance monitor counters under the **BizTalk:Message Agent** performance object category.  
  
- The number of messages being processed concurrently by the host instance exceeds the **In-process messages per CPU** \* the number of CPUs available on the box. The **In-process messages** threshold is defined on the **Resource-Based Throttling** tab in **Settings Dashboard**. The number of messages being processed concurrently by the host instance can be measured with the **In-process message count** performance counter under the **BizTalk:Message Agent** performance object category.  
  
- The default throttling behavior has been modified. [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) describes the different values that impact throttling behavior.  
  
  Depending upon the severity of the throttling condition, the following actions are taken:  
  
- A progressive delay in the processing logic of the host instance is implemented before delivering the messages to the outbound transport adapter or the orchestration engine for processing the messages. Both the duration of the processing logic delay and the rate at which the duration is incremented scale with the severity of the throttling condition.  
  
- The number of messages that can be held by the in-memory queue is limited. The in-memory queue serves as a temporary placeholder for delivering messages from the MessageBox to the Message Agent which in turn delivers messages to XLANG and send adapters. By default, the in-memory queue is set to hold 100 messages per CPU. When the queue is full, no more messages are de-queued from the MessageBox until the in-memory queue is freed up.  
  
- The size of the Message Agent thread pool is limited. By limiting the Message Agent thread pool size, the host throttling mechanism effectively reduces the amount of messages that are delivered to XLANG and adapters.  
  
   The default Message Agent thread pool size can be modified by changing the **Maximum engine threads** value on the **General** tab in **Settings Dashboard**. For more information about modifying this value, see [How to Modify General Settings](../core/how-to-modify-general-settings.md).  
  
- The use of memory and other resources is reduced as applicable. BizTalk Server can send instructions to other service classes to limit memory use by dehydrating running schedules, shrinking memory cache size, and by limiting the usage of memory intensive threads.  
  
  **Outbound message flow from MessageBox to Adapters and XLANG**  
  
  ![Outbound message flow to Adapters and XLANG](../core/media/outboundmsgflow.gif "OutboundMsgFlow")  
  
## See Also  
 [How BizTalk Server Implements Host Throttling](../core/how-biztalk-server-implements-host-throttling.md)   
 [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)