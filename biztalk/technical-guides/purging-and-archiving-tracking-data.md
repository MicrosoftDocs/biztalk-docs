---
description: "Learn more about: Purging and Archiving Tracking Data"
title: "Purging and Archiving Tracking Data | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 14094fda-3fd9-4d45-9bbb-cd9377c2cbad
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Purging and Archiving Tracking Data
It is important to configure and enable the DTA Purge and Archive SQL Agent job. This job archives and purges old data from the BizTalk Tracking (DTA) database. This is essential for a healthy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system. A large Tracking database will begin to affect the performance of the tracking host and any other processes that query the Tracking database. If the tracking data is not purged from the Tracking database, the database will continue to grow.

## Guidelines for Using the DTA Purge and Archive Job

-   **Ensure that the DTA Purge and Archive SQL Agent job is properly configured, enabled, and successfully completing.**

     This job is not enabled by default because you must first configure it to include a directory where the archive files can be written.

-   **If you only need to purge the old data and do not need to archive it first, then change the SQL Agent job to call the stored procedure “dtasp_PurgeTrackingDatabase”.**

     This skips the archive step, and just does the purge. For more information about this stored procedure and changing the SQL Agent job to use it, see ["How to Purge Data from the BizTalk Tracking Database"](https://go.microsoft.com/fwlink/?LinkId=153817) (https://go.microsoft.com/fwlink/?LinkId=153817).

-   **Ensure that the job is able to purge the tracking data as fast as the incoming tracking data is generated.**

     It is acceptable for the job to get behind during peak load times, but it should always be able to catch up. If the purge job gets behind and is never able to catch up, the Tracking database will continue to grow, and performance will eventually be adversely affected.

-   **Review the soft purge and hard purge parameters to ensure that you are keeping data for the optimal length of time.**

     For more information about these parameters see ["Archiving and Purging the BizTalk Tracking Database"](https://go.microsoft.com/fwlink/?LinkId=153816) (https://go.microsoft.com/fwlink/?LinkId=153816).

-   **If you need to keep the tracking archive files, ensure that you have a process in place to successfully restore and use them.**

## See Also
 [Checklist: Configuring SQL Server](~/technical-guides/checklist-configuring-sql-server.md)
