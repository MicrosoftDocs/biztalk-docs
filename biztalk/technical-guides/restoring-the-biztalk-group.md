---
title: "Restoring the BizTalk Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14a9af44-d6de-49c7-9600-21ece389727f
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Restoring the BizTalk Group
The BizTalk group is represented by the set of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases, SSIS packages, and SQL Agent Jobs. This section describes the process for restoring the BizTalk group.  
  
 In the event that a switchover to the destination system (disaster recovery site) is required, the following steps must be completed:  
  
1. Restore [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and Analysis Services databases.  
  
2. Restore BizTalk Server runtime servers and applications.  
  
   Upon completion of these steps, the BizTalk group has been established at the disaster recovery site, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime servers can be configured, and the applications can be deployed into the BizTalk group. The topics in this section cover the details of this process.  
  
## In This Section  
  
-   [Stopping Application Processing on the Source System](../technical-guides/stopping-application-processing-on-the-source-system.md)  
  
-   [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)  
  
-   [Restoring Databases Not Included in the Backup BizTalk Server Job](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)