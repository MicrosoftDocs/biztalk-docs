---
description: "Learn more about: Scaled-Out Processing Hosts"
title: "Scaled-Out Processing Hosts"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Scaled-Out Processing Hosts
A scaled-out processing host improves performance and provides high availability by isolating orchestration functionality onto two or more separate host computers. This isolation lets you add multiple computers to a processing host for redundancy. A processing host in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runs one or more host instances that coordinate various business processes and creates an instance of programmatic objects for orchestrations.  
  
 The following figure shows a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment that provides high availability for the processing host by having two computers that are running instances of the processing host. Note that in this figure the receiving and sending hosts are not highly available.  
  
 ![Scaled Out Processing Host](../core/media/tdi-ha-scaleprocess.gif "TDI_HA_ScaleProcess")  
  
 In this configuration, the work for processing orchestrations is load balanced between two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers that have instances of the processing host and run independently of each other. If one computer encounters errors or fails, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically uses the host instance on the other computer to process remaining orchestrations.  
  
## Maintaining Orchestration State  
 BizTalk Server maintains orchestration state centrally in Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and not locally on each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer. By persisting the state in the MessageBox database, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] overcomes the limitation of relying on a single processing host instance to process the orchestration, and lets any processing host instance process the orchestration. If an error occurs while [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes an orchestration, another instance of the same processing host can complete the orchestration from the last persisted state.  
  
## See Also  
 [Providing High Availability for BizTalk Hosts](../core/providing-high-availability-for-biztalk-hosts.md)
