---
title: "Planning for Database Availability | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6aa74257-4159-46f6-b538-f7e9083d74ad
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for Database Availability
The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Messaging engine ensures that business processes are reliable and durable by persisting process state and business data to a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database known as the BizTalk Messagebox database. Because the reliability and durability of the persisted data is only as good as the underlying data store, planning for high availability of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases is critically important.  
  
## Hardware Considerations  
 To ensure high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, consider the following when planning for hardware:  
  
1.  Consider implementing a storage area network (SAN) to house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. The SAN disks should be configured using RAID 1+0 (a stripe of mirror sets) topology if possible for maximum performance and high availability. For more information about using a SAN to house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases see the [BizTalk Server Database Optimization](http://go.microsoft.com/fwlink/?LinkID=101578) white paper ([http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578)).  
  
2.  Plan on installing multiple computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] to house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. Multiple computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] will be required for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] clustering (recommended) and/or housing certain [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases on separate physical [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances (also recommended).  
  
3.  Plan on installing one or more computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] to implement [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] log shipping for purposes of disaster recovery. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implements database standby capabilities through the use of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] log shipping. [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] log shipping automates the backup and restore of database and transaction log files, allowing a standby server to resume database processing in the event that the production server fails. For more information about implementing [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] log shipping for purposes of disaster recovery, see [What Is BizTalk Server Log Shipping?](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## Software Considerations  
 To ensure high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, consider the following when planning for software: Plan to install a version and edition of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that supports failover clustering support and/or BizTalk log shipping support. For a complete list of the features supported by the editions of [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], see [Features Supported by the Editions of SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=151940) ([http://go.microsoft.com/fwlink/?LinkId=151940](http://go.microsoft.com/fwlink/?LinkId=151940)) in the [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] documentation.  
  
## High Availability vs. Disaster Recovery  
 There are two distinct methods for increasing availability for a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment: providing high availability using fault tolerance and/or load balancing, or providing availability using disaster recovery. While each method increases availability, a key difference between them is that fault tolerance and/or load balancing typically provide much faster recovery time than disaster recovery does. Therefore, a solution built on fault tolerance or load balancing is more commonly thought of as providing high availability as opposed to merely providing availability. Both methods should be employed in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  
  
 Provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases using fault tolerance with Windows Clustering. For more information about providing high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, see [High Availability for Databases](../technical-guides/high-availability-for-databases.md).  
  
 Increase availability with disaster recovery using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping. To increase availability of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases with disaster recovery, follow the steps in the topic [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md).