---
title: "How to Restore Databases in the Backup BizTalk Server Job | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9bcac40f-ef0b-4ff0-8743-cf1614e14422
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Restore Databases in the Backup BizTalk Server Job
This section covers the steps to bring online the databases in the BizTalk group that are backed up by the Backup BizTalk Server job. By default, all databases are backed up by using the Backup BizTalk Server job except for the BAM databases. See [Restoring Analysis Services and Supporting Databases](../technical-guides/restoring-analysis-services-and-supporting-databases.md) for more information about backup and restore of the BAM databases. You must restore all databases to the same mark to ensure a consistent transactional state among the databases. For more information, see [Marked Transactions, Full Backups, and Log Backups](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565).  
  
 For more information and instructions about restoring databases for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [How to Restore Your Databases](http://go.microsoft.com/fwlink/?LinkId=151406) (<http://go.microsoft.com/fwlink/?LinkId=151406>).  
  
## See Also  
 [Restoring Databases Not Included in the Backup BizTalk Server Job](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)