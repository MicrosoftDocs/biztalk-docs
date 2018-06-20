---
title: "Planning Your Platform for Fault Tolerance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backing up, BizTalk Server"
  - "MessageBox database, fault tolerance"
  - "clustering, fault tolerance"
  - "SQL Server RAID"
  - "databases [BAM], fault tolerance"
  - "BizTalk Server, planning"
  - "fault tolerance"
  - "clustering, fail-overs"
  - "planning, fault tolerance"
  - "Primary Import database [BAM]"
  - "BizTalk Server, backing up"
  - "fault tolerance, planning"
  - "planning, BizTalk Server"
  - "Primary Import database [BAM], fault tolerance"
  - "fail-over clustering"
ms.assetid: 512ed6b8-db1e-434a-8009-63e952cf5500
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning Your Platform for Fault Tolerance
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is built on the Microsoft Windows and Microsoft SQL Server platforms. The ability of BizTalk Server to survive or recover from a disaster depends on the ability of the underlying platform to survive or recover.  
  
 For your Business Activity Monitoring (BAM) databases and your MessageBox database, we recommend you do the following:  
  
- Set up fail-over clustering, which is available in SQL Server Enterprise Edition. Fail-over clustering enables SQL Server to automatically switch the processing for an instance of SQL Server from a failed server to a working server.  
  
   The BAM Primary Import database collects event data. In the event of a disaster, data that was written to the BAM Primary Import database since the last backup will be lost. Because there is no way to regenerate lost events, it is especially important that you enable fail over clustering on your BAM Primary Import database.  
  
- Use SQL Server RAID (redundant array of independent disks), especially for the MessageBox database and the BAM Primary Import database.  
  
  Use the following resources to design your Windows and SQL Server deployments for fault tolerance. Take time to learn about hardware and server redundancy technologies, such as clustering and disk mirroring, to prevent service outages and data loss.  
  
- [White Paper: High Availability—Always On Technologies](http://go.microsoft.com/fwlink/?LinkId=130376)  
  
   The “High Availability – Always On Technologies” whitepaper describes high availability features that are available with SQL Server 2008.  
  
- [High Availability Solutions Overview](http://go.microsoft.com/fwlink/?LinkId=130377)  
  
   Introduces several high-availability solutions for SQL Server 2008 that improve the availability of servers or databases.  
  
- [Chapter 15 - High Availability Options, SQL Server Resource Kit](http://go.microsoft.com/fwlink/?LinkId=24431)  
  
   The Microsoft SQL Server Resource Kit covers a wide range of administrative and deployment planning areas. Chapter 15 covers planning for fault tolerance and recovery.  
  
- [Windows Deployment Services Step-by-Step Guide](http://go.microsoft.com/fwlink/?LinkId=130379)  
  
   Contains step-by-step guidance for how to use the Windows Deployment Services role in Windows Server 2008  
  
- [Windows Server 2003 Deployment Kit: Planning Server Deployments](http://go.microsoft.com/fwlink/?LinkId=24433).  
  
   This book provides information about planning server storage, and information about designing and deploying file servers, print servers, and terminal servers in medium and large organizations.  
  
   You can also use the guidelines in this book to maximize the availability and scalability of your servers by planning for remote server management, designing and deploying server clusters, and designing and deploying Network Load Balancing clusters.  
  
## Backing Up Your Platform  
 After you have configured your system, prepare full backups of your servers so you can quickly restore an identical server in the event of data loss.  
  
 To back up your platform, perform the documented backup procedures for each of the following technologies:  
  
- Microsoft Windows Server Standard, Enterprise, or Datacenter Edition  
  
- Internet Information Services (IIS)  
  
- Microsoft SQL Server  
  
- Windows SharePoint Services, which is used by the Windows SharePoint Services adapter.  
  
  Follow the recommendations in the “BizTalk Server Operations Guide” for “Backing up BizTalk Server” available at [Checklist: Increasing Availability with Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=130498).  
  
  Thoroughly test your backup and restore procedures, and put them in a safe, remote location.  
  
## See Also  
 [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md)