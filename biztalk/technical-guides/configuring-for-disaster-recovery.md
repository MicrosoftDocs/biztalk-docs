---
description: "Learn more about: Configuring for Disaster Recovery"
title: "Configuring for Disaster Recovery | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: acdafe68-c8bf-4064-afca-6dfd22d15052
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring for Disaster Recovery
The BizTalk Server Log Shipping feature extends the existing Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job. BizTalk Server Log Shipping eliminates the need to manually restore a series of backup sets produced by the backup job, and reduces downtime in the event of a system failure. BizTalk Server Log Shipping is a critical component for BizTalk disaster recovery procedures.  
  
> [!NOTE]  
>  Each application team must have a documented backup and restore plan for disaster recovery that complements the concepts provided in this topic. The overall plan should address the entire system, including applications and the components of the operating system.  
  
 Performing a disaster recovery operation is very similar to manually performing a restore of a BizTalk group to a new set of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances. The primary difference is that BizTalk Server log shipping applies logs continuously at the disaster recovery site, saving many manual steps. Therefore, only the last set of logs must be restored manually when BizTalk Server log shipping is implemented. Otherwise, the last full backup followed by all log backups since the last full backup would have to be manually restored. BizTalk Server log shipping reduces the effort for this manual process, speeding restoration of the disaster recovery site.  
  
 This section covers recommendations on production configuration to facilitate the disaster recovery process.  
  
## In This Section  
  
-   [Prepare the Disaster Recovery Site](../technical-guides/prepare-the-disaster-recovery-site.md)  
  
-   [Log Shipping User Accounts and Roles](../technical-guides/log-shipping-user-accounts-and-roles.md)  
  
-   [Configuring BizTalk Server Log Shipping](../technical-guides/configuring-biztalk-server-log-shipping.md)  
  
## See Also  
 [Disaster Recovery](../technical-guides/disaster-recovery.md)
