---
title: "Best Practices for Monitoring with Operations Manager 2007 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67a5026c-ef59-498b-9bef-ea0f1c932eae
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Monitoring with Operations Manager 2007
Adhere to the best practices listed in this topic to effectively monitor your applications using Operations Manager 2007.  
  
 **Install additional management packs for more complete coverage**  
  
- To help ensure that Operations Manager 2007 monitors the key applications in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, you should install the following management packs:  
  
  - [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (required)  
  
  - Windows Server Operating System (optional)  
  
  - Microsoft Windows Server Failover Cluster (if clusters are used, optional)  
  
  - SQL Server Monitoring  
  
  - Internet Information Services 7  
  
  - Message Queuing (MSMQ) 5.0 (optional)  
  
  **Review and prioritize alerts on a daily basis**  
  
- Reviewing and prioritizing alerts on a daily basis helps to ensure that issues are resolved in a timely manner.  
  
  **Verify that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is communicating with the Operations Manager 2007 server.**  
  
- If communication fails between the servers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the monitoring infrastructure, you will not receive alerts.  
  
  **Enable and disable rules as necessary**  
  
- By default, some of the rules in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack are disabled. These disabled rules are of the following types: rules needing customization, rules that serve as templates, and rules for monitoring additional [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] events. Make sure the relevant rules for your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment are enabled.  
  
  **Customize rules as necessary for your environment**  
  
- You should customize the rules in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] management pack to suit your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment. Some rules require monitoring thresholds or time thresholds that are best defined based on your specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment.  
  
  **Create additional rules as necessary, based on the rules included in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack**  
  
- Rules are provided for use as templates for artifacts that you create, such as [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hosts. You should use these template rules as a reference when creating artifact-specific rules such as:  
  
  -   Host-specific rules, for example, host queue monitoring, and host throttling monitoring  
  
  -   MessageBox-specific rules  
  
  -   Rules for additional third party components, for example, MQSeries adapter  
  
  **Monitor all the BizTalk Server related components**  
  
  The components of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment that you should monitor to ensure that they are running include, but are not necessarily limited to:  
  
- BizTalk Host instances  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent jobs installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
- Any custom services developed for the BizTalk solution  
  
- Status of any custom databases developed for the BizTalk solution  
  
- Any custom event log entries relevant to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment  
  
## See Also  
 [Monitoring BizTalk Server with System Center Operations Manager 2007](../technical-guides/monitoring-biztalk-server-with-system-center-operations-manager-2007.md)