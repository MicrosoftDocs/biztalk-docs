---
title: "Monitoring Throttling Using Performance Threshold Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc2c3024-a54b-4485-8110-c2ec9ec52721
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitoring Throttling Using Performance Threshold Rules
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will initialize throttling to protect the system from reaching an unrecoverable state. Throttling can indicate a problem and assist you in identifying its source. After you have identified the cause of the bottleneck based on the throttling state, analyze the other performance counters to narrow down the source of the problem.  
  
 For example, high contention on the MessageBox database could be due to high CPU usage, which could be caused by excessively paging to disk, which in turn could be caused by low memory conditions. High contention on the MessageBox could also be caused by high lock contention, which could be due to saturated disk drives.  
  
 Monitoring the Message Delivery Throttling State and the Message Publishing Throttling State for each host instance is usually a good place to start when troubleshooting throttling. If the value of these counters is not zero, it is indicative that throttling is happening within the BizTalk Server system and it is possible to further analyze the cause of the bottleneck. For descriptions on the other performance counters, see [Identifying Bottlenecks in the Database Tier](http://go.microsoft.com/fwlink/?LinkID=154678) (<http://go.microsoft.com/fwlink/?LinkID=154678>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
## BizTalk Server System Performance Counters  
  
|Object|Instance|Counter|Monitoring Purpose|  
|------------|--------------|-------------|------------------------|  
|Processor|_Total|% Processor Time|Resource Contention|  
|Process|BTSNTSvc|Virtual Bytes|Memory Leak/Bloat|  
|Process|BTSNTSvc|Private Bytes|Memory Leak/Bloat|  
|Process|BTSNTSvc|Handle Count|Resource Contention|  
|Process|BTSNTSvc|Thread Count|Resource Contention|  
|Physical Disk|_Total|% Idle Time|Resource Contention|  
|Physical Disk|_Total|Current Disk Queue Length|Resource Contention|  
  
## BizTalk Application Counters  
  
|Object|Instance|Counter|Description|  
|------------|--------------|-------------|-----------------|  
|BizTalk Messaging|RxHost|Documents Received/Sec|Incoming Rate|  
|BizTalk Messaging|TxHost|Documents Processed/Sec|Outgoing Rate|  
|XLANGs/Orchestrations|PxHost|Orchestrations Completed/Sec|Processing Rate|  
|BizTalk: MessageBox: General Counters|MsgBoxName|Spool Size|Cumulative size of all Host Queues|  
|BizTalk: MessageBox: General Counters|MsgBoxName|Tracking Data Size|Size of TrackingData table on the MessageBox|  
|BizTalk: MessageBox: Host Counters|PxHost:MsgBoxName|Host Queue - Length|Number of messages in the specific Host Queue|  
|BizTalk: MessageBox: Host Counters|TxHost:MsgBoxName|Host Queue - Length|Number of messages in the specific Host Queue|  
|BizTalk: Message Agent|RxHost|Database Size|Size of publishing (PxHost) Queue|  
|BizTalk: Message Agent|PxHost|Database Size|Size of publishing (TxHost) Queue|  
|BizTalk: Message Agent|HostName|Message Delivery Throttling State|Affects XLANG and Outbound transports|  
|BizTalk: Message Agent|HostName|Message Publishing Throttling State|Affects XLANG and Inbound transports|  
  
## In This Section  
  
-   [Monitoring for Throttling](../technical-guides/monitoring-for-throttling.md)