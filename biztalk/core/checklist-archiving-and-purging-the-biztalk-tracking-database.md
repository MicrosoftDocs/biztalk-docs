---
title: "Checklist: Archiving and Purging the BizTalk Tracking Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "archiving [Tracking database], checklist"
  - "checklists, purging [Tracking database]"
  - "purging, checklist"
  - "checklists, archiving [Tracking database]"
ms.assetid: dccbf471-2add-498e-b292-287d9a94161b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Archiving and Purging the BizTalk Tracking Database

|Step|Reference|  
|----------|---------------|  
|Read the Archiving and Purging overview to become more familiar with the process of archiving and purging tracking data.|[Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)|  
|Although you can run the DTA Purge and Archive job using your logon credentials, for added security, you should configure the BTS_BACKUP_USERS role with the necessary SQL Server credentials to run the DTA Purge and Archive job. This helps to prevent elevation of privileges.|[How to Configure the BTS_BACKUP_USERS Role for Archiving and Purging Data from the BizTalk Tracking Database](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)|  
|Configure the DTA Purge and Archive job.|[How to Configure the DTA Purge and Archive Job](../core/how-to-configure-the-dta-purge-and-archive-job.md)|  
|Run the DTA Purge and Archive job, which archives the data in your BizTalk Tracking (BizTalkDTADb) database and purges old data.|[How to Purge Data from the BizTalk Tracking Database](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)|  
|Optionally, you can manually purge data from the BizTalk Tracking (BizTalkDTADb) database.|[How to Manually Purge Data from the BizTalk Tracking Database](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)|  
|Enable automatic validation of the archived data from the BizTalk Tracking (BizTalkDTADb) database.|[How to Enable Automatic Archive Validation](../core/how-to-enable-automatic-archive-validation.md)|  
|Copy tracked messages into the BizTalk Tracking (BizTalkDTADb) database. This is required in order to purge data using the DTA Purge and Archive job.|[How to Copy Tracked Messages into the BizTalk Tracking Database](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)|  

## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)