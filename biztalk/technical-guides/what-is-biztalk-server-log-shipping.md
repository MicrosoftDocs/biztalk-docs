---
title: "What Is BizTalk Server Log Shipping? | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79a2088a-ff36-4590-97c9-51d5bb245486
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Is BizTalk Server Log Shipping?
BizTalk Server disaster recovery procedures are built around BizTalk log shipping. BizTalk log shipping simplifies database restoration in the event of a disaster by continuously applying transaction log updates to the disaster recovery site databases.  
  
 While BizTalk log shipping is based on similar principles as [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] log shipping, [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] log shipping is not supported for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases backed up as part of the Backup BizTalk Server SQL Agent Job.  
  
## How Does BizTalk Log Shipping Work?  
 BizTalk log shipping functions in a manner similar to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] log shipping. The production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group is configured to back up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases to a UNC location. By default, the Backup BizTalk SQL Agent job performs a full backup every hour and a log backup every 15 minutes. The Backup BizTalk Server job implements logic to automatically start a full backup if a backup failure is detected.  
  
 When the disaster recovery [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances are configured for BizTalk log shipping, the backup files created by the Backup BizTalk Server SQL Agent job are restored at the disaster recovery site every 15 minutes by default. The backup files are copied over the network by a SQL RESTORE command. Full backup files are copied only in the following situations:  
  
- When BizTalk log shipping is first configured  
  
- When a new database is added to the Backup BizTalk Server job.  
  
- When a RESTORE failure occurs at the disaster recovery site  
  
  Each [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance at the disaster recovery site is configured individually as part of BizTalk log shipping to restore databases hosted on a production [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instance. When a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance is configured for BizTalk Server log shipping and the **BTS Log Shipping Restore Databases** job is enabled, the **BTS Log Shipping Restore Databases** job will connect to the BizTalk Management database on the production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.  
  
  As described above, when the destination server is first configured the full database backup is restored to the destination server. Most of the time only the logs are restored when the **BTS Log Shipping Restore Databases** job runs.  
  
  When viewing the disaster recovery [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances with [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio, the databases will be displayed in a “Loading” state. This is because the last log in a backup set is never restored automatically. Once a new log is available, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping restores the next to last log. When a disaster recovery event occurs and the disaster recovery site must be brought online, the last log is restored using the STOPATMARK command to recover the databases and the databases will no longer be displayed as being in a “Loading” state.