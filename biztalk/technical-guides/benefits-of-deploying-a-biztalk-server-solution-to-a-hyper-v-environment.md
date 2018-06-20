---
title: "Potential Benefits of Deploying a BizTalk Server Solution to a Hyper-V Virtualized Environment | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 588c70f0-68f0-4e58-8f3d-aa6834397bd4
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Potential Benefits of Deploying a BizTalk Server Solution to a Hyper-V Virtualized Environment
This topic describes some of the benefits of deploying your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution to a Hyper-V virtualized environment.  
  
## Benefits of Running a BizTalk Server Solution on a Hyper-V Virtualized Environment  
 Deploying your BizTalk Server solution to run on a Hyper-V virtualized environment provides the following flexibility and functionality:  
  
- **Ability to define multiple distinct logical security boundaries on a single physical computer -** Hyper-V accommodates the creation of distinct logical security boundaries or partitions within a single physical hardware resource. A partition is a single logical unit of isolation, supported by the hypervisor, in which operating systems execute. For example, you could create multiple BizTalk Server groups to run on a single Hyper-V host computer whereas you would not be able to do this when installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on the host operating system of a single host computer.  
  
- **Ease of deployment and management –** Consolidation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers into fewer physical servers simplifies deployment. [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] uses a simplified method for physical and virtual computer deployments by using .vhd files. Furthermore, a comprehensive Hyper-V management solution is available with System Center Virtual Machine Manager. For more information about System Center Virtual Machine Manager, see [http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303).  
  
- **Fault tolerance support through Hyper-V clustering -** Because Hyper-V is a cluster aware application, Windows Server 2008 provides native host clustering support for virtual machines created in a Hyper-V virtualized environment.  
  
- **Ease of scale-out -** Additional processing power, network bandwidth, and storage capacity can be accommodated for your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution quickly and easily by apportioning additional available resources from the host computer to the guest virtual machine(s). This may require that the host computer is upgraded or that the guest virtual machines are moved to a more capable host computer. The live migration feature of [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] allows you to move running VMs to the best physical computer for performance, scaling, or optimal consolidation without impacting users.  
  
- **Consolidation of hardware resources -** Multiple physical servers can be easily consolidated into comparatively fewer servers by implementing virtualization with Hyper-V. Consolidation accommodates full use of deployed hardware resources.  
  
  To find out more detailed information about the features and benefits Hyper-V provides, see [Virtualization with Hyper-V](http://go.microsoft.com/fwlink/?LinkID=202438).