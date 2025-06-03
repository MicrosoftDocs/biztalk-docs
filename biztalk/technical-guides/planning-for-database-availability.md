---
description: "Learn more about: Planning for Database Availability"
title: "Planning for Database Availability"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Planning for Database Availability
The BizTalk Server Messaging engine ensures that business processes are reliable and durable by persisting process state and business data to a SQL Server database known as the BizTalk Messagebox database. Because the reliability and durability of the persisted data is only as good as the underlying data store, planning for high availability of the BizTalk Server databases is critically important.  
  
## Hardware Considerations  
 To ensure high availability for the BizTalk Server databases, consider the following when planning for hardware:  
  
1.  Consider implementing a storage area network (SAN) to house the BizTalk Server databases. The SAN disks should be configured using RAID 1+0 (a stripe of mirror sets) topology if possible for maximum performance and high availability. 
  
2.  Plan on installing multiple computers running SQL Server to house the BizTalk Server databases. Multiple computers running SQL Server will be required for SQL Server clustering (recommended) and/or housing certain BizTalk Server databases on separate physical SQL Server instances (also recommended).  
  
3.  Plan on installing one or more computers running SQL Server to implement SQL Server log shipping for purposes of disaster recovery. BizTalk Server implements database standby capabilities through the use of SQL Server log shipping. SQL Server log shipping automates the backup and restore of database and transaction log files, allowing a standby server to resume database processing in the event that the production server fails. For more information about implementing SQL Server log shipping for purposes of disaster recovery, see [What Is BizTalk Server Log Shipping?](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## Software Considerations  
 To ensure high availability for the BizTalk Server databases, consider the following when planning for software: Plan to install a version and edition of SQL Server that supports failover clustering support and/or BizTalk log shipping support. For a complete list of the features supported by the SQL Server editions, see [Editions and supported features](/sql/sql-server/editions-and-components-of-sql-server-2016).
  
## High Availability vs. Disaster Recovery  
 There are two distinct methods for increasing availability for a BizTalk Server environment: providing high availability using fault tolerance and/or load balancing, or providing availability using disaster recovery. While each method increases availability, a key difference between them is that fault tolerance and/or load balancing typically provide much faster recovery time than disaster recovery does. Therefore, a solution built on fault tolerance or load balancing is more commonly thought of as providing high availability as opposed to merely providing availability. Both methods should be employed in a production BizTalk Server environment.  
  
 Provide high availability for the BizTalk Server databases using fault tolerance with Windows Clustering. For more information about providing high availability for the BizTalk Server databases, see [High Availability for Databases](../technical-guides/high-availability-for-databases.md).  
  
 Increase availability with disaster recovery using BizTalk Server log shipping. To increase availability of the BizTalk Server databases with disaster recovery, follow the steps in the topic [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md).
