---
title: "Monitoring for Throttling | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d1d4c72-6942-4572-b27f-c58d37c94062
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitoring for Throttling
The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack monitors performance counters that indicate the throttling state of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Some key factors to understand about throttling are listed below.  
  
- Rate-based throttling is per host and is based on the rate of messages inbound vs. outbound messages.  
  
- For delivery throttling (**MsgBox -> Send Port or Orchestration**), inbound rate is the rate at which messages are received from the message box. Outbound rate is the rate at which messages are successfully delivered via the adapters.  
  
- For publishing throttling (**Receive adapters** or **Orchestrations -> MsgBox),** inbound rate is the rate at which messages are received from the adapters and outbound rate is the rate messages are plugged into the MsgBox.  
  
- No throttling mechanism exists between hosts other than total messages in the database.  
  
  For additional background information, refer to the topic [How BizTalk Server Implements Host Throttling](http://go.microsoft.com/fwlink/?LinkID=155286) (<http://go.microsoft.com/fwlink/?LinkID=155286>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] incorporates self-throttling, which helps to prevent overloading of the server based on various parameters. A temporary overload that causes throttling to occur is not an operationally significant event. Persistent throttling, however, is not expected in a stable environment and could indicate underlying problems at the infrastructure level. The management pack provides proactive monitoring of such persistent throttling conditions with performance threshold rules.  
  
  Four utilization/performance tracking rules monitor for extended periods of throttling caused by four different conditions as indicated in the following table.  
  
|                                                     Condition                                                     |                                        Rule                                         |
|-------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
|     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] service process memory     |     Warning: BizTalk Throttled on High Process Memory for a significant period      |
|                                        Number of messages being processed                                         | Warning: BizTalk Throttled on High Inprocess Message Count for a significant period |
| Number of threads in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process |      Warning: BizTalk Throttled on High Thread Count for a significant period       |
|  Size of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database queues   |      Warning: BizTalk Throttled on High Database Size for a significant period      |
  
 These threshold rules use data providers based on throttling state indicator performance counters. For more information about these performance counters, refer to the section [Performance Counters](http://go.microsoft.com/fwlink/?LinkId=157269) (<http://go.microsoft.com/fwlink/?LinkId=157269>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.  
  
 These rules are configured to raise an alert if the average of over a certain number of samples crosses a particular threshold (default is 30). For example, “Warning: BizTalk Throttled on High Database Size for a significant period” is a rule monitoring the throttling state of all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes in a given computer. This rule uses a data provider based on the throttling state indicator performance counter “BizTalk:Message Agent-High database size.” If this performance counter value is 1, then the associated process is throttling because of high database size.  
  
 The preceding rule is configured to take an average of 30 samples and raise an alert if the average of the samples is more than 0.6. Since each sample is taken at an interval of one minute, this implies that over the past 30 minutes, at least one or more BizTalk Server processes in that computer were throttling because of high database size, 60 percent of the time.  
  
 This heuristic may not suit your particular application scenario. Based on the historical behavior in your environment as described before, you should configure these rules with the correct values by either:  
  
-   Adjusting the samples.  
  
-   Adjusting the threshold value.  
  
-   If necessary, modifying the interval of sampling for the provider.