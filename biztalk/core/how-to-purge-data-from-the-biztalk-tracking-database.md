---
title: "How to Purge Data from the BizTalk Tracking Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tracking database, purging"
  - "purging"
  - "DTA Purge and Archive job, purging data"
  - "purging, DTA Purge and Archive job"
ms.assetid: cdf12866-442d-4c1f-b10f-ebf8d665d521
caps.latest.revision: 27
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Purge Data from the BizTalk Tracking Database
When you purge data from the BizTalk Tracking (BizTalkDTADb) database, the DTA Purge and Archive job purges different types of tracking information such as message and service instance information, orchestration event information, and rules engine tracking data from the BizTalk Tracking (BizTalkDTADb) database.  
  
> [!IMPORTANT]
>  The BizTalk Tracking (BizTalkDTADb) database is not archived using this procedure.  
  
> [!WARNING]
>  If an exception is caught and handled in an orchestration without tracking turned on, an orphaned tracking instance with a Started state and exception information may be inserted into the BizTalk Tracking (BizTalkDTADb) database. This record will remain after purging the database.  
  
## Prerequisites  
 You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.  
  
### To purge data from the BizTalk Tracking database  
  
1.  Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to Server** dialog box, specify the name of the SQL Server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the SQL Server.  
  
3.  In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.  
  
4.  In the **Object Explorer Details** pane, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then click **Properties**.  
  
5.  In the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **Steps**.  
  
6.  In the **Job step list**, click **Archive and Purge**, and then click **Edit**.  
  
7.  In the **Job Step Properties - Archive and Purge** dialog box, on the **General** page, in the **Command** box, change **exec dtasp_BackupAndPurgeTrackingDatabase** to **exec dtasp_PurgeTrackingDatabase**.  
  
    > [!CAUTION]
    >  The **exec dtasp_PurgeTrackingDatabase** stored procedure does not archive the BizTalk Tracking (BizTalkDTADb) database. Before using this option, be certain that you no longer require archived tracking data.  
  
8.  In the **Command** box, edit the following parameters as appropriate, and then click **OK**.  
  
    -   @nHours tinyint — Any completed instance older than (live hours) + (live days) will be deleted along with all associated data.  
  
    -   @nDays tinyint — Any completed instance older than (live hours) + (live days) will be deleted along with all associated data. Default interval is 1 day.  
  
    -   @nHardDays tinyint — All data older than this day will be deleted, even if the data is incomplete. The time interval specified for HardDeleteDays should be greater than the live window of data. The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database. Anything older than this interval is eligible to be archived at the next archive and then purged.  
  
    -   @dtLastBackup — Set this to **GetUTCDate()** to purge data from the BizTalk Tracking (BizTalkDTADb) database. When set to **NULL**, data is not purged from the database.  
  
     Your edited script should look similar to this:  
  
    ```  
    declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate() exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup  
    ```  
  
9. On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **General**, select the **Enabled** check box, and then click **OK**.  
  
## See Also  
 [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md)