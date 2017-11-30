---
title: "Disaster Recovery for Computers Running BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10a2c26d-55d5-45d1-9fb1-e0664f005c21
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Disaster Recovery for Computers Running BizTalk Server
If the computer running BizTalk Server in your organization suffers an unrecoverable hardware failure, you should replace it with an identical computer. This assumes that the BizTalk Server databases are intact, and that the failure is in any one of the computers running BizTalk Server.  
  
 One possible approach is to maintain an updated image of every computer running BizTalk Server in your installation. When a computer suffers a hardware failure, the recovery action is as simple as deploying the stored image on a new computer. The disaster recovery topics address the case where storing such images is not feasible.  
## Recovering Different Editions of BizTalk Server  
 The recovery approach is different depending on the edition of BizTalk Server running on the computer.  
  
 For BizTalk Server Developer Edition and BizTalk Server Enterprise Edition, multiple computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are permitted. When one of the computers running BizTalk Server fails, you can prepare a replacement computer and join it to the existing BizTalk group. In this case, you can join a computer with either the same name or a different name to the BizTalk group.  
  
 For BizTalk Server Standard Edition, you cannot join the computer to a BizTalk group, so the above approach is not suitable. Instead, we outline the steps needed to set up a new computer and restore the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration settings so that it can function as a replacement. For more information, see [How to Recover the BizTalk Group](../core/how-to-recover-the-biztalk-group.md).  
  
## Recovery Phases  
 The recovery of a computer running BizTalk Server can be classified into the following three phases:  
  
1.  **Preparing the Base Platform**  
  
     This phase includes the preparation of a computer with the base platform including the operating system, software prerequisites and appropriate BizTalk Server components. This guide assumes that before you attempt to restore the BizTalk Server configuration, you have a computer with the base platform, prerequisites, and BizTalk Server components installed. This guide does not cover base platform restoration.  
  
2.  **Restoring the BizTalk Server Configuration**  
  
     This phase assumes that you have a record of the features configured on the failed computer, including a copy of the BizTalk Server configuration file for that computer. This guide provides guidance for restoring the BizTalk Server configuration.  
  
3.  **Restoring BizTalk Applications**  
  
     This phase involves restoring the .NET assemblies connected with the applications that are hosted by the BizTalk Server processes on the replacement computer. Any artifacts that are needed, such as user assemblies apart from BizTalk assemblies, should be installed in their respective locations or the global assembly cache (GAC) on the computer. This guide provides some guidance on this phase. However, there are no separate scripts or tools for restoring BizTalk applications.  
  
## See Also  
 [Backing Up and Restoring BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md)