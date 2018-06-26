---
title: "Planning for High Availability and Disaster Recovery | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7efba36-6d9c-4ae0-a4f5-893eb5d62a05
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for High Availability and Disaster Recovery
Solutions developed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are often mission-critical enterprise-level applications that require maximum availability. When these solutions are placed into production, costs associated with downtime can be measured in thousands of dollars per second. For this reason, you should employ specific strategies to maximize the high availability and disaster recovery capabilities that are available with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the dependency software and hardware required to support a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.  
  
## Hardware Considerations  
 To ensure high availability for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, consider the following when planning for hardware:  
  
- Plan on running multiple (at least two) BizTalk servers in a BizTalk group to accommodate running multiple instances of BizTalk Hosts across the BizTalk servers in the group. This will accommodate load balancing and fault tolerance of processes running in the host instances.  
  
- Consider implementing a storage area network (SAN) to house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. The SAN disks should be configured using RAID 1+0 (a stripe of mirror sets) topology if possible for maximum performance and high availability. For more information about using a SAN to house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, see the [BizTalk Server Database Optimization white paper](http://go.microsoft.com/fwlink/?LinkID=101578) (<http://go.microsoft.com/fwlink/?LinkID=101578>).  
  
- Plan on installing multiple SQL servers to house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. Multiple SQL servers are required for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] clustering (recommended) and/or housing certain [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases on separate physical [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances (also recommended).  
  
- Consider using a virtual environment to control the hardware costs. Microsoft offers a range of virtualization products such as Microsoft Virtual Server 2005 R2, Windows Server 2008 Hyper-V, and Microsoft Hyper-V Server 2008. For recommendations on using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a virtual environment, see [BizTalk Server 2009 Hyper-V Guide](http://go.microsoft.com/fwlink/?LinkId=151834) (<http://go.microsoft.com/fwlink/?LinkId=151834>).  
  
- Plan on installing one or more Windows servers in a perimeter network domain to provide Internet-related services for your organization. Configure multiple Windows servers in the perimeter network domain using a network load balancing (NLB) solution. For more information, see [Network Load Balancing Deployment Guide](http://go.microsoft.com/fwlink/?LinkId=153139) (http://go.microsoft.com/fwlink/?LinkId=153139).  
  
   For more information about installing servers in a perimeter network, see [Configuring Your Domain When Exposing Transports to the Internet](../technical-guides/planning-for-sending-and-receiving.md#BKMK_InternetTrans).  
  
  > [!NOTE]  
  >  A perimeter network is also known as a DMZ, demilitarized zone, and screened subnet.  
  
## Software Considerations  
 To ensure high availability for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, consider the following when planning for software:  
  
- Consider investing in the Enterprise Edition of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to accommodate scenarios that would benefit from clustering of BizTalk Hosts or that would benefit from running multiple MessageBox databases. Typically, the only reason that you should cluster a BizTalk Host would be to provide high availability for certain BizTalk adapters. For more information about providing high availability for BizTalk adapters using host clustering, see [Considerations for Running Adapter Handlers within a Clustered Host](http://go.microsoft.com/fwlink/?LinkID=151284) (<http://go.microsoft.com/fwlink/?LinkID=151284>).  
  
- Plan on implementing a Windows Server cluster to house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and the Enterprise Single Sign-On master secret server. For more information about using Windows Server cluster to provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and the Enterprise Single Sign-On master secret server, see [High Availability for Databases](../technical-guides/high-availability-for-databases.md) and [High Availability for the Master Secret Server](../technical-guides/high-availability-for-the-master-secret-server.md).  
  
## High Availability vs. Disaster Recovery  
 There are two prescribed methods for increasing availability for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment: providing high availability using fault tolerance and/or load balancing, or providing increased availability using disaster recovery. While each method increases availability, a key difference between them is that fault tolerance and/or load balancing typically provide much faster recovery time than disaster recovery. Fault tolerance and/or load balancing provide **high availability** whereas disaster recovery provides **increased availability**. For more information about implementing disaster recovery, see [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md) and [Disaster Recovery](../technical-guides/disaster-recovery.md).  
  
## See Also  
 [Increasing Availability for BizTalk Server](../technical-guides/increasing-availability-for-biztalk-server.md)   
 [Checklist: Providing High Availability with Fault Tolerance or Load Balancing](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)