---
title: "Dynamic Send Port Handler is Configurable | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5eb8f5ef-af95-4b2e-9a43-6f1240b25855
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Dynamic Send Port Handler is Configurable
When creating a Dynamic Send Port, an adapter Send Handler is configurable for *every* installed adapter. Consider the following scenario:  
  
 **Scenario**  
  
 There are two ESB itineraries in an application. Itinerary1 uses a Dynamic Send Port to send data to a File share. Itinerary2 uses a Dynamic Send Port to send e-mail. In the past, Dynamic send ports execute in the adapter's default host. Itinerary1 is designed to target a low volume - big message size scenario. Itinerary2 targets a high volume - small message size scenario. Since there is only one default host for an adapter, all messages are routed using the same host, decreasing the performance.  
  
 **The Change**  
  
 To improve the performance of Dynamic Send Ports, an adapter Send Handler is configurable to use any host. In the ESB scenario, Itinerary1 uses HostA to send data to a File share. Itinerary2 uses HostB Port to send e-mail.  
  
## Select a Send Handler  
 When creating a Dynamic One-Way Send Port or Dynamic Solicit-Response Send Port, the Send Handler is configurable for every installed adapter. Steps:  
  
1. In the **BizTalk Server Administration** console, expand **BizTalk Group [*GroupName*]**, expand **Applications**, and then expand the application to contain the send port.  
  
2. Right-click **Send Ports**, click **New**, and then click **Dynamic One-way Send Port** or **Dynamic Solicit-Response Send Port**.  
  
3. In  **Properties**, click **Configure**.  
  
    The adapters are listed with the default Send Handler. Click the down arrow to select a different host.  
  
4. Click **OK** save the settings.  
  
5. Unenlist and reenlist the new dynamic send port.  
  
6. Restart the original host instance.  
  
7. Restart the new host instance.  
  
   Additional Send Port configuration options include:  
  
- [How to Configure Transport Advanced Options for a Send Port](http://go.microsoft.com/fwlink/p/?LinkId=267697)  
  
- [How to Configure Backup Transport Options for a Send Port](http://go.microsoft.com/fwlink/p/?LinkId=267698)  
  
- [How to Configure Outbound Maps for a Send Port](http://go.microsoft.com/fwlink/p/?LinkId=267699)  
  
- [How to Configure Filters for a Send Port](http://go.microsoft.com/fwlink/p/?LinkId=267700)  
  
- [How to Assign a Certificate to a Send Port](http://go.microsoft.com/fwlink/p/?LinkId=267701)  
  
- [How to Configure Tracking for a Send Port](http://go.microsoft.com/fwlink/p/?LinkId=267702)  
  
  The different hosts can be fine-tuned. The following links discuss performance optimization:  
  
  [General BizTalk Server Optimizations](http://go.microsoft.com/fwlink/p/?LinkId=267703)  
  
  [Managing BizTalk Server Performance Settings](http://go.microsoft.com/fwlink/p/?LinkId=267704)