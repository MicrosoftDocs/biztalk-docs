---
title: "Archive and Purge the Tracking Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7014cf31-86e8-4829-8055-056442329009
caps.latest.revision: 37
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Archive and Purge the BizTalkDTADb Database

## Overview
As BizTalk Server processes more and more data on your system, the BizTalk Tracking (BizTalkDTADb) database continues to grow in size. Unchecked growth decreases system performance and may generate errors in the Tracking Data Decode Service (TDDS). In addition to general tracking data, tracked messages can also accumulate in the MessageBox database, causing poor disk performance.  
  
BizTalk Server automates both processes using the DTA Purge and Archive job. By archiving and purging data from the BizTalk Tracking database, you can maintain a healthy system, as well as keep your tracking data archived for future use. Because BizTalk Tracking database archives accumulate over time and consume disk space, it is a good idea to move the BizTalk Tracking database archives to secondary storage on a regular basis.  
  
 When you purge data from the BizTalk Tracking database, the DTA Purge and Archive job purges different types of tracking information such as message and service instance information, orchestration event information, and rules engine tracking data.  
  
 The age of a tracking data record is based on the time the tracking data was inserted into the BizTalk Tracking database. The DTA Purge and Archive job uses the time stamp to continuously verify whether the record is older than the live window of data. After every live window period, the BizTalk Tracking database is archived and a new archive file is created. At each SQL Server Agent job interval specified by the job schedule, all completed tracking data older than the live window period is purged.  
  
 BizTalk Server uses the concept of a soft purge and a hard purge. The soft purge is used to purge completed instances, while the hard purge is only used to purge incomplete instances.  
  
## Soft purge
  
 In the DTA Archive and Purge job, the sum of the LiveHours and LiveDays parameters is the live window of data you want to maintain in your BizTalk Server environment. All data associated with a completed instance older than this live window of data is purged. By default, the DTA Archive and Purge job is not enabled. You must first configure and then enable the job.  
  
 For example, you can configure the DTA Purge and Archive job to run every 20 minutes, and set LiveHours=1 and LiveDays=0. The first time this SQL Server Agent job runs (T0), it takes a backup of the tracking database by creating an archive and an entry is saved in the database with this timestamp. A successful archive is necessary in order to purge tracking data. If the archive was successful, then all the data associated with the instances that completed over an hour ago is purged. Each time the job runs, completed data over one hour old is purged. On the 3rd run (after one hour), a new archive is created that contains the data for all instances that were inserted into the tracking database in the last one hour segment.  
  
 Here is how you would configure the Archive and Purge step in the DTA Purge and Archive job to match the example:  
  
```  
exec dtasp_BackupAndPurgeTrackingDatabase  
1, --@nLiveHours 1,   
0, --@nLiveDays   
1, --@nHardDeleteDays   
‘\\server\backup’, --@nvcFolder   
null, --@nvcValidatingServer   
0 --@fForceBackup Soft purge process  
```  
  
 The time stamp of the last backup is stored in the BizTalk Tracking database and ensures that data is only purged if it is in the previous archive. For additional reliability, archives are overlapped by approximately 10 minutes. The following figure, based on the example above, shows the soft purge process. Note that the archiving and purging tasks do not necessarily happen at the same time.  
  
 **Soft purge process**  
  
 ![Soft purge process](../core/media/archivingandpurging.gif "archivingandpurging")  
  
## Hard purge
  
 Because the soft purge only purges data associated with completed instances, if you have many looping instances that run indefinitely, then your tracking database would grow and these instances would never be purged. The hard purge date allows all information older than the specified interval to be purged except for information indicating a service's existence. You set the hard purge using the <strong>@nHardDeleteDays</strong> parameter in the Archive and Purge step in the DTA Archive and Purge job. The hard purge setting should always be greater than your soft purge setting. In other words, <strong>@nHardDeleteDays</strong> should be greater than the sum of <strong>@nLiveHours</strong> and <strong>@nLiveDays</strong>.  
  
 Archiving and purging includes the features described in the following table:  
  
|Feature|Description|  
|-------------|-----------------|  
|Hard purge|Enables you to configure a time interval to purge information for incomplete instances older than a specified date.|  
|Copying tracked messages to tracking database|Using the CopyTrackedMessageToDTA option, you can directly copy tracked messages from the MessageBox servers to your BizTalk Tracking database. This is required in order to purge data using the DTA Purge and Archive job.|  
|Archive validation|Enables you to optionally set up a secondary database server to validate the archives as they are created.|  
|Tracking support for multiple BizTalk Tracking database versions|Enables you to use tracking support with BizTalk Server database archives.|  
|Reduction of tracking data|Substantially reduces the amount of tracking data stored without reducing any tracking information generated. This results in slower growth of the tracking database.|  
|Faster tracking operations, significant optimization in database schemas|Enables you to use tracking tasks for finding messages and service instances on large databases; this feature has been significantly optimized.|  
  
> [!NOTE]
>  If you are having performance issues that are momentarily addressed by purging the BizTalk tracking database, and you want to configure BizTalk to no longer collect tracking information, you may want to consider turning off global tracking. See [Turn Off Global Tracking](../core/how-to-turn-off-global-tracking.md).  
  
## Next steps
  
-   [Checklist: Archiving and Purging the BizTalk Tracking Database](../core/checklist-archiving-and-purging-the-biztalk-tracking-database.md)  
  
-   [Configure the BTS_BACKUP_USERS Role for Archiving and Purging Data from the BizTalk Tracking Database](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)  
  
-   [Configure the DTA Purge and Archive Job](../core/how-to-configure-the-dta-purge-and-archive-job.md)  
  
-   [Purge Data from the BizTalk Tracking Database](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [Manually Purge Data from the BizTalk Tracking Database](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)  
  
-   [Enable Automatic Archive Validation](../core/how-to-enable-automatic-archive-validation.md)  
  
-   [Copy Tracked Messages into the BizTalk Tracking Database](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)  
  
-   [Improving the Performance of the Archiving and Purging Process](../core/improving-the-performance-of-the-archiving-and-purging-process.md)  
  
-   [Turn Off Global Tracking](../core/how-to-turn-off-global-tracking.md)