---
title: "How to Identify Bottlenecks in the Tracking Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b72e726-6225-47a0-8e1d-0f5a9cf745d3
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Identify Bottlenecks in the Tracking Database
To identify bottlenecks in the BizTalk Tracking (BizTalkDTADb) database, perform the following steps:  
  
1. Ensure that the SQL-Agent Service is running.  
  
2. Ensure that the Archive/Purge Job is running and completing successfully.  
  
3. Ensure that the TrackedMessages_Copy_BizTalkMsgBoxDB Job is running and completing successfully.  
  
4. Verify that sufficient free disk space is available for the DTADb archives and database growth.  
  
5. Use a dedicated host for tracking and measure the Host Queue Length performance counter when under load.  
  
6. Check the Spool Table size performance counter for an increasing trend over time.  
  
7. Check the Archive/Purge job execution duration for long execution times.  
  
8. Check disk responsiveness (Disk Seconds per Read/Write performance counter) on the disk hosting the BizTalk Tracking database.  
  
   We strongly recommend tuning down the value of the following parameters of the dtasp_BackupAndPurgeTrackingDatabase or dtasp_PurgeTrackingDatabase invoked by the DTA Purge and Archive job:  
  
- @nLiveHours tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data. Default is 0 hours.  
  
- @nLiveDays tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data. Default interval is 1 day.  
  
- @nHardDeleteDays tinyint — All data (even if incomplete) older than this will be deleted. The time interval specified for HardDeleteDays should be greater than the live window of data. The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database. Anything older than this interval is eligible to be archived at the next archive and then purged. Default is 30 days.  
  
  These parameters should be set in accordance with data retention policies in a production environment, whereas in a performance lab tests we recommend that you use values as follows:  
  
  declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate()  
  exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup  
  
## See Also  
 [Bottlenecks in the Database Tier](../technical-guides/bottlenecks-in-the-database-tier.md)