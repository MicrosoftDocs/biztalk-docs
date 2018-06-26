---
title: "Monitoring Host Instances | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e7c6b80-7371-46ea-bf9c-82acb22012a3
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitoring Host Instances
This topic describes monitoring BizTalk host instances using Microsoft System Center Operations Manager.  
  
## Using Threshold Rules to Monitor Health  
 The BizTalk Server Management Pack incorporates performance threshold rules that provide a comprehensive view of the health of the BizTalk hosts. Two different types of threshold rules are provided:  
  
- Rules that apply generically (for example, to all BizTalk hosts and to all MessageBox databases).  
  
- Rules that are specific to a particular BizTalk host.  
  
  Generic rules monitor all the BizTalk hosts based on a common threshold. For example, the rule Monitor HostQ Size monitors the work queues of all BizTalk hosts based on a common threshold. If there are three different hosts, all their work queues are monitored by the same rule, and alerts occur when any of the host work queues cross the common threshold.  
  
  BizTalk host-specific rules enable you to configure different thresholds for different hosts. For example, the rule Monitor HostQ Size – BizTalkServerApplication is a host-specific rule that monitors the work queue of the BizTalkServerApplication host. In this example you can define a specific Operations Manager provider for the particular performance counter instance and use that provider in the threshold rule. Because these rules are host-specific, you must define rules specific to each newly created host.  
  
  BizTalk host-specific rules are provided as template rules for creating rules that are applicable in your environment. All threshold monitoring rules are disabled by default:  
  
- You should configure generic rules with threshold values specific to your environment.  
  
- You should create BizTalk host-specific rules based on the template rules and appropriate thresholds.  
  
## Monitoring BizTalk Host Instances  
 Rules that target specific BizTalk hosts are more flexible from a monitoring perspective. All threshold monitoring rules for the BizTalkServerApplication host provided in the BizTalk Server Management pack are template rules. In order to use these rules, you should use the Operations Manager Administrator console to:  
  
- Create a copy of the template rule in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] rule group and rename it.  
  
- Create a new Operations Manager provider for the BizTalk host-specific performance counter instance.  
  
- Modify the Operations Manager provider used by the rule and point it to the new one.  
  
  Suppose your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation has a BizTalk host ReceiveHost and you want to monitor the Host Queue size for this host. In this case, you should create a Operations Manager provider based on the ReceiveHost instance of the performance counter for the queue size for the BizTalk host. You should also set the threshold value in the rule appropriately for your environment.  
  
  If you are using host-specific threshold monitoring rules, you should disable generic monitoring rules. This prevents redundant alerts.  
  
## See Also  
 [Monitoring BizTalk Server with System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)