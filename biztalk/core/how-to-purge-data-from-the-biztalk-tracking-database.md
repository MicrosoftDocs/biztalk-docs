---
title: "Purge Data from the BizTalk Tracking Database | Microsoft Docs"
description: Configure the dtasp_PurgeTrackingDatabase stored procedure to purge the tracking database (BizTalkDTADB) in BizTalk Server
ms.custom: ""
ms.date: "10/11/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdf12866-442d-4c1f-b10f-ebf8d665d521
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Purge Data from the BizTalk Tracking Database
When you purge data from the BizTalk Tracking (BizTalkDTADb) database, the DTA Purge and Archive job purges different types of tracking information such as message and service instance information, orchestration event information, and rules engine tracking data from the BizTalk Tracking (BizTalkDTADb) database.  
  
> [!IMPORTANT]
>  The BizTalk Tracking (BizTalkDTADb) database is not archived using this procedure.  
  
> [!WARNING]
>  If an exception is caught and handled in an orchestration without tracking turned on, an orphaned tracking instance with a Started state and exception information may be inserted into the BizTalk Tracking (BizTalkDTADb) database. This record will remain after purging the database.  
  
## Prerequisites  
Sign in with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
## Purge data from the BizTalk Tracking database  
  
1.  On the SQL Server that hosts the BizTalk Tracking (BizTalkDTADb) database, open **SQL Server Management Studio**. 
  
2.  In **Connect to Server**, enter the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides, enter the authentication type, and then select **Connect** to connect to the SQL server. 
  
3.  Double-click **SQL Server Agent**, and then select **Jobs**.  
  
4.  In **Object Explorer Details**, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then select **Properties**.  
  
5.  In **Job Properties - DTA Purge and Archive (BizTalkDTADb)**, under **Select a page**, select **Steps**.  
  
6.  In **Job step list**, select **Archive and Purge**, and then select **Edit**.  
  
7.  In **Job Step Properties - Archive and Purge**, on the **General** page, in the **Command** box, change **exec dtasp_BackupAndPurgeTrackingDatabase** to **exec dtasp_PurgeTrackingDatabase**.  
  
    > [!CAUTION]
    >  The **exec dtasp_PurgeTrackingDatabase** stored procedure does not archive the BizTalk Tracking (BizTalkDTADb) database. Before using this option, be certain that you no longer require archived tracking data.  
  
8.  In the **Command** box, update the following parameters, and then select **OK**.  
  
    -   @nHours tinyint — Any completed instance older than (live hours) + (live days) will be deleted along with all associated data.  
  
    -   @nDays tinyint — Any completed instance older than (live hours) + (live days) will be deleted along with all associated data. Default interval is 1 day.  
  
    -   @nHardDays tinyint — All data older than this day will be deleted, even if the data is incomplete. The time interval specified for HardDeleteDays should be greater than the live window of data. The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database. Anything older than this interval is eligible to be archived at the next archive and then purged.  
  
    -   @dtLastBackup — Set this to **GetUTCDate()** to purge data from the BizTalk Tracking (BizTalkDTADb) database. When set to **NULL**, data is not purged from the database.  

    -  @fHardDeleteRunningInstances int - Default is 0. When set to 1, it deletes all running service instances older than the @nHardDeleteDays value.  
    
        > [!NOTE] 
        > The @fHardDeleteRunningInstances property is available starting with [BizTalk Server 2016 Cumulative Update 1](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016), [BizTalk Server 2013 R2 Cumulative Update 6](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2), and [BizTalk Server 2013 Cumulative Update 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013).   

    Your edited script looks similar to the following:  
  
    ```  
    declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate() exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup, 1  
    ```  
    
9. On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, select **General**, select the **Enabled** check box, and then select **OK**.  
  
## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)
