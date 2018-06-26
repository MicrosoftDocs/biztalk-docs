---
title: "Backing Up Databases | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0524a8f0-15a3-4731-a7bd-c0c935fff6c8
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Backing Up Databases
Because[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses distributed transactions across multiple databases, the Backup BizTalk Server job creates synchronized backups of all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. This is accomplished by using marked transactions with the “Full” database recovery model. This is required for the backups to be transactionally consistent across databases. For more information, see ["Marked Transactions, Full Backups, and Log Backups"](http://go.microsoft.com/fwlink/?LinkId=151565) (<http://go.microsoft.com/fwlink/?LinkId=151565>) in the BizTalk Server documentation.  
  
## Advantages of the Backup BizTalk Server Job  
 The Backup BizTalk Server job is the only supported method for backing up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. Use of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] jobs to back up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases in a production environment is not supported.  
  
 If the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job is not run, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database transaction logs will grow unbounded. The backup job truncates the transaction logs, which keep them from growing unbounded. If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database transaction logs continue to grow, they could at some point fill the disk they are housed on.  
  
> [!NOTE]
>  Using both the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job and log shipping is currently the only fully documented and supported method for performing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backup and restore.  
  
## Guidelines for the Backup BizTalk Server Job  
 You should restore the entire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment on a regular basis. This includes not only the SQL server(s) and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, but also the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. You should document and practice these procedures before a failure actually occurs.  
  
> [!NOTE]
>  The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job does not delete old backup files. You must define and put processes in place to archive the old backup files and move them from the backup directory that the backup job uses.  
  
## Additional Resources  
 See the following topics in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation:  
  
- For more information about specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] backup and restore tasks, see ["Checklist: Backup and Restore"](http://go.microsoft.com/fwlink/?LinkId=154070) (<http://go.microsoft.com/fwlink/?LinkId=154070>).  
  
- For an overview of Backing up and restoring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see ["Backing Up and Restoring BizTalk Server"](http://go.microsoft.com/fwlink/?LinkId=154071) (<http://go.microsoft.com/fwlink/?LinkId=154071>).  
  
- For more information about configuring the Backup BizTalk Server job, see ["How to Configure the Backup BizTalk Server Job"](http://go.microsoft.com/fwlink/?LinkId=154072) (http://go.microsoft.com/fwlink/?LinkId=154072).  
  
## See Also  
 [Using BizTalk Server Log Shipping for Disaster Recovery](../technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)