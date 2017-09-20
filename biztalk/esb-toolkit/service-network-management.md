---
title: "Service Network Management | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21469dad-6c64-470a-bd58-8309d789ce6c
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Service Network Management
Effective run-time governance requires knowledge of the services deployed into the run-time environment. AmberPoint SMS can discover the actual receive locations and send ports deployed within a BizTalk Management Group, as shown in Figure 1.  
  
 ![AmberPoint Container Discovery](../esb-toolkit/media/ch9-amberpointcontainerdiscovery.gif "Ch9-AmberPointContainerDiscovery")  
  
 **Figure 1**  
  
 **The AmberPoint SMS Container Discovery screens**  
  
 Using information on the deployed services, AmberPoint SMS presents various perspectives of the services that help users to understand the run-time configuration and appreciate their dependencies on other services within the running service network. Figure 2 shows the service profile and dependencies screens.  
  
 ![AmberPoint Service Profile](../esb-toolkit/media/ch9-amberpointserviceprofile.gif "Ch9-AmberPointServiceProfile")  
  
 **Figure 2**  
  
 **The AmberPoint SMS service profile and dependencies screens**  
  
 AmberPoint SMS can publish and forward service discoveries and run-time metadata to existing Universal Description, Discovery, and Integration (UDDI) registries, custom configuration management repositories, and master system management consoles, such as Microsoft Operations Manager 2004 (MOM) and System Center Operations Manager 2007 (SCOM).