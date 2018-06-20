---
title: "Marked Transactions, Full Backups, and Log Backups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backing up, transaction logs"
  - "backing up, full backups"
  - "transaction logs"
  - "backing up, backup jobs"
ms.assetid: a383a16d-1e40-4b0b-a515-f1cb90bfb4d2
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Marked Transactions, Full Backups, and Log Backups
The Backup BizTalk Server Job creates synchronized backups of all BizTalk Server databases by using full database backups and transaction log backups, in conjunction with a type of transaction known as a *marked transaction*. Marked transactions are transactions that place a mark into the transaction log of all databases participating in the transaction. The marked transaction blocks new distributed transactions from starting, waits for the distributed transactions that are currently running to complete, and then executes to place the mark.  
  
 The mark represents a transaction point that is consistent across all databases; you can use the mark with subsequent log backups to restore your databases to that point.  
  
 For each BizTalk Server database, the Backup BizTalk Server job creates a marked transaction log backup every time it runs, and it creates a full backup based on a time period that you specify.  
  
## Full backups  
 When you run the Backup BizTalk Server job it runs the first backup process, *BackupFull*, once every period (not every time the job runs). For more information about how to schedule the Backup BizTalk Server job, see [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md).  
  
 The first time the Backup BizTalk Server job runs during a new period, it performs a full backup. For example, if you schedule the job to run every hour but configure the period to be daily, the Backup BizTalk Server job performs a full backup the first time it runs, and then every day at midnight.  
  
## Transaction log backups  
 The second process that the Backup BizTalk Server job performs is *MarkAndBackupLog*. This process places a mark in all BizTalk Server databases and performs a transaction log backup every time the job executes.  
  
 The mark is the string created by using *\<ServerName\>*<em>*\<DatabaseName\>*_Log\\</em>*\<LogMarkName\>*\_*\<Timestamp\>*.bak, where the *\<Log Mark Name\>* is configured in the SQL Server Agent job. This mark must be used when restoring the last log to each database.  
  
 For more information, see "Transaction Log Backups" and "Backup and Recovery of Related Databases" in SQL Server Books Online.  
  
## See Also  
 [Advanced Information About Backup and Restore](../core/advanced-information-about-backup-and-restore1.md)