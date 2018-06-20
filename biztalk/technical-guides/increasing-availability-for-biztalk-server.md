---
title: "Increasing Availability for BizTalk Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72d9ce5e-d775-4f8e-b1a4-bf3c7c05f571
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Increasing Availability for BizTalk Server
This section describes ways you can increase the availability of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.  
  
## Strategies for Increasing Availability  
 Strategies for increasing availability include the following:  
  
- **Providing high availability using Windows Server 2003 server clustering or Windows Server 2008 failover clustering**. A server/failover cluster is a group of independent computer systems, known as nodes, working together as a single system to ensure that critical applications and resources remain available to clients. If one of the nodes becomes unavailable as a result of failure or maintenance downtime requirements, another node immediately begins providing service (a process known as failover).  
  
  - A server/failover cluster is typically recommended for the computers running SQL Server that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.  
  
  - A server cluster may be required to provide high availability for certain BizTalk adapters.  
  
  - A server cluster is typically recommended for the Enterprise Single Sign-On master secret server.  
  
- **Providing high availability using a form of load balancing**.  
  
  - Network load balancing (NLB). NLB delivers high availability by redirecting incoming network traffic to working NLB cluster hosts if a host fails or is offline. Unlike server clusters, NLB does not require special hardware.  
  
  - BizTalk host load balancing. BizTalk host load balancing is provided for BizTalk Hosts by adding multiple servers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group and then configuring multiple instances of an in-process host to run on these servers. This distributes the execution of services and artifacts configured in that host across multiple instances of the host, which enhances its availability and scalability.  
  
    > [!NOTE]  
    >  Host load balancing functionality is available for in-process hosts only.  
  
  - Load balancing is provided for SQL Server disks through the use of a SAN or by adding multiple MessageBox databases.  
  
- Strategies for providing **increased availability**. These strategies provide increased availability but usually also require that an administrator perform one or more actions at runtime. Therefore these strategies are typically thought of as providing increased availability as opposed to high availability:  
  
  - Increasing availability using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping and disaster recovery.  
  
  - Increasing availability through implementation of the appropriate monitoring and maintenance strategies.  
  
## Difference Between Clustering and Disaster Recovery  
 While clusters and disaster recovery both increase availability, a key difference between them is that clusters typically provide much faster recovery time than disaster recovery does. Therefore a solution built on server/failover clusters or load balancing is commonly thought of as providing high availability as opposed to merely providing availability.  
  
 Disaster recovery allows you to resume operation of a failed system but is typically a manual process and requires more recovery time than a high-availability implementation. Therefore, a disaster recovery implementation provides availability but not high availability. You should employ both high availability through server/failover clusters and load balancing, and availability through disaster recovery, in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  
  
## In This Section  
  
-   [Providing High Availability](../technical-guides/providing-high-availability.md)  
  
-   [Disaster Recovery](../technical-guides/disaster-recovery.md)  
  
## See Also  
 [Checklist: Providing High Availability with Fault Tolerance or Load Balancing](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)   
 [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)