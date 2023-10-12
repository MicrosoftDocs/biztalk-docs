---
description: "Learn more about: Backing Up and Restoring BizTalk Server"
title: "Backing Up and Restoring BizTalk Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Backing Up and Restoring BizTalk Server
In the event of hardware failure, having a good backup of your BizTalk Server databases and components is essential. A good backup will enable you to recover with little or no data loss. How you restore BizTalk Server depends on which components were installed on the system where hardware failure occurred. This guide covers the following hardware failure scenarios:  
  
 **Hardware failure in the computer running BizTalk Server**  
  
 A hardware failure in the computer running BizTalk Server may cause system downtime or degraded performance if the BizTalk group is not designed for high availability. For more information about how to create a highly available BizTalk group, see [Planning for High Availability](../core/planning-for-high-availability3.md).  
  
 To ensure that you can replace a computer running BizTalk Server after a hardware failure, you must back up the BizTalk Server components on that computer. For more information about how to back up and restore a computer running BizTalk Server, see [Backing Up a Computer Running BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) and [Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md).  
  
 **Hardware failure in the computer running SQL Server**  
  
 You can minimize the risk of a hardware failure in a computer running SQL Server by using SQL Server clustering. Even when using SQL Server clustering, however, there may be situations when the SQL server(s) containing the BizTalk Server databases experiences an unrecoverable hardware failure. For example, the entire data tier suffered a failure. In these situations, you must revive the BizTalk group by restoring the most recent set of backed up databases.  
  
 For more information about providing fault tolerance for the BizTalk Server databases, see [Providing High Availability for BizTalk Server Databases](../core/providing-high-availability-for-biztalk-server-databases.md). In the case of a catastrophic SQL Server failure where downtime has occurred, you should follow the instructions in [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md).  
  
 If you experience a hardware failure on a computer where both SQL Server and BizTalk Server are installed, you should restore the BizTalk Server databases, and then recover the BizTalk Server components.  
  
## In This Section  
  
-   [Checklist: Backup and Restore](../core/checklist-backup-and-restore.md)  
  
-   [Best Practices for Backup and Restore](../core/best-practices-for-backup-and-restore.md)  
  
-   [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md)  
  
-   [Disaster Recovery for Computers Running BizTalk Server](../core/disaster-recovery-for-computers-running-biztalk-server.md)  
  
-   [Backing Up a Computer Running BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md)  
  
-   [Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)
