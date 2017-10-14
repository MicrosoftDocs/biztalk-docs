---
title: "Configure the DTA Purge and Archive Job | Microsoft Docs"
description: Set the DTA Purge and Archive job parameters in SQL Server Agent to maintain the Tracking database in BizTalk Server
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 156ccf9b-284f-4b96-a395-92936e8cebcf
caps.latest.revision: 22
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the DTA Purge and Archive Job
Before you can archive or purge data from the BizTalk Tracking (BizTalkDTADb) database, you must configure the DTA Purge and Archive (BizTalkDTADb) job. This job is configured to call the dtasp_BackupAndPurgeTrackingDatabase store procedure, which uses six parameters you must configure.  
  
## Prerequisites  
 Sign in with an account that is a member of the SQL Server sysadmin fixed server role.  
  
## Configure the DTA purge and archive job  
  
1.  On the SQL Server that hosts the BizTalk Tracking (BizTalkDTADb) database, open **SQL Server Management Studio**.  
  
2.  In **Connect to Server**, enter the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides, enter the authentication type, and then select **Connect** to connect to the SQL server.  
  
3. Double-click **SQL Server Agent**, and then select **Jobs**.  
  
4.  In **Object Explorer Details**, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then select **Properties**.  
  
5.  In **Job Properties - DTA Purge and Archive (BizTalkDTADb)**, under **Select a page**, select **Steps**.  
  
6.  In the **Job step list**, select **Archive and Purge**, and then select **Edit**.  
  
7.  In **General**, in the **Command** box, update the following parameters, and then select **OK**.  
  
    -   @nLiveHours tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data. This is a required parameter with no default value.  
  
    -   @nLiveDays tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data. Default interval is 0 days.  
  
        > [!NOTE]
        >  For the purposes of the BizTalk Tracking (BizTalkDTADb) database, the sum of LiveHours plus LiveDays is the live window of data you want to maintain in your BizTalk Server environment. All data associated with a completed instance older than the live window of data is deleted.  
  
    -   @nHardDeleteDays tinyint — All data (even if incomplete) older than this will be deleted. The time interval specified for HardDeleteDays should be greater than the live window of data. The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database. Anything older than this interval is eligible to be archived at the next archive and then purged. Default is 0 days.  
  
    -   @nvcFolder nvarchar(1024) — Folder in which to put the backup files. This is a required parameter with no default value.  
  
    -   @nvcValidatingServer sysname — Server on which validation will be done. NULL value indicates no validation is being done. Default is NULL.  
  
    -   @fForceBackup int — Default is 0. This is reserved for future use.  
  
    -   @fHardDeleteRunningInstances int - Default is 0. When set to 1, it deletes all running service instances older than the @nHardDeleteDays value. 
    
        > [!NOTE]
        > The @fHardDeleteRunningInstances property is available starting with [BizTalk Server 2016 Cumulative Update 1](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016), [BizTalk Server 2013 R2 Cumulative Update 6](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2), and [BizTalk Server 2013 Cumulative Update 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013).  
  
    Your edited command should look similar to the following. In the following example, there is a live window of 1 hour, a hard purge of 1 day, and deletes all running service instances older than 1 day:  
  
    ```  
    exec dtasp_BackupAndPurgeTrackingDatabase 1, 0, 1, '\\MyBizTalkServer\backup', null, 0, 1  
    ```  
  
8.  On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, select **General**, select the **Enabled** check box, and then select **OK**.  
  
## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)
