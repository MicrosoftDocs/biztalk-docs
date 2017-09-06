---
title: "How to Configure the DTA Purge and Archive Job | Microsoft Docs"
ms.custom: ""
ms.date: "2015-11-09"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "purging, configuring"
  - "DTA Purge and Archive job, configuring"
  - "archiving [Tracking database], DTA Purge and Archive job"
  - "archiving [Tracking database], configuring"
  - "purging, DTA Purge and Archive job"
ms.assetid: 156ccf9b-284f-4b96-a395-92936e8cebcf
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the DTA Purge and Archive Job
Before you can archive or purge data from the BizTalk Tracking (BizTalkDTADb) database, you must configure the DTA Purge and Archive (BizTalkDTADb) job. This job is configured to call the dtasp_BackupAndPurgeTrackingDatabase store procedure, which uses six parameters you must configure.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to follow these steps.  
  
### To configure the DTA purge and archive job  
  
1.  On the SQL Server that hosts the BizTalk Tracking (BizTalkDTADb) database, open **SQL Server Management Studio**.  
  
2.  In **Connect to Server**, enter the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides, enter the authentication type, and then select **Connect** to connect to the SQL server.  
  
3.  In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.  
  
4.  In the **Object Explorer Details** pane, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then click **Properties**.  
  
5.  In the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **Steps**.  
  
6.  In the **Job step list**, click **Archive and Purge**, and then click **Edit**.  
  
7.  On the **General** page, in the **Command** box, edit the following parameters as appropriate, and then click **OK**.  
  
    -   @nLiveHours tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data. This is a required parameter with no default value.  
  
    -   @nLiveDays tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data. Default interval is 0 days.  
  
        > [!NOTE]
        >  For the purposes of the BizTalk Tracking (BizTalkDTADb) database, the sum of LiveHours plus LiveDays is the live window of data you want to maintain in your BizTalk Server environment. All data associated with a completed instance older than the live window of data is deleted.  
  
    -   @nHardDeleteDays tinyint — All data (even if incomplete) older than this will be deleted. The time interval specified for HardDeleteDays should be greater than the live window of data. The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database. Anything older than this interval is eligible to be archived at the next archive and then purged. Default is 0 days.  
  
    -   @nvcFolder nvarchar(1024) — Folder in which to put the backup files. This is a required parameter with no default value.  
  
    -   @nvcValidatingServer sysname — Server on which validation will be done. NULL value indicates no validation is being done. Default is NULL.  
  
    -   @fForceBackup int — Default is 0. This is reserved for future use.  
  
     The edited command should look similar to the following. In the following example, there is a live window of 1 hour and a hard purge of 1 day:  
  
    ```  
    exec dtasp_BackupAndPurgeTrackingDatabase 1, 0, 1, '\\MyBizTalkServer\backup', null, 0  
    ```  
  
8.  On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **General**, select the **Enabled** check box, and then click **OK**.  
  
## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)