---
description: "Learn more about: Log Shipping"
title: "Log Shipping"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Log Shipping
Log shipping provides standby server capabilities, sometimes called a warm backup, which reduces downtime in the event of a system failure.  
  
 Due to the distributed database design of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], when you produce backups you must be certain to provide a consistent point to which the backups can be restored. Transactions can span multiple databases; if one database goes offline and must be restored, then all related databases must be restored to a single point in time to ensure that the system is in a consistent state. Not all databases participate in distributed transactions. For more information, see [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md).  
  
 The Backup BizTalk Server job uses Microsoft SQL Server log marking to provide an automated process that produces database backup sets. These backup sets include synchronized points that are used during the restoration process. As part of the process of restoring a set of databases produced by the Backup BizTalk Server job, the last log backup file for each database is restored to a specific log mark, using the second to last mark. This enables you to restore your databases to a consistent state and significantly reduce the amount of data lost. The log mark before the last one should be used. Although SQL Server includes a log shipping feature, you should only use the BizTalk Server log shipping feature when backing up and restoring BizTalk Server databases.  
  
> [!NOTE]
>  The SQL Server simple recovery model is not supported for use with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases because the simple recovery model does not backup the transaction log and therefore does not maintain a record of activity since the most recent backup.  Configure SQL Server to use the full recovery model to ensure the integrity of data in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backup sets.  
  
## See Also  
 [Advanced Information About Backup and Restore](../core/advanced-information-about-backup-and-restore1.md)
