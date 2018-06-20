---
title: "Planning for Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ffc8573-1b4a-47c7-96ab-0471f43facf5
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for Tracking
Message tracking is the process by which parts of a message instance, such as the message body, message properties, and metadata are stored in a database, typically for archival purposes. Message instance parts that are tracked can subsequently be viewed by running queries from the Group Hub page in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. In addition to accessing archived data, you can also view live data, which can be a helpful tool for identifying and fixing problems in a development or staging environment.  
  
 Since the process of message tracking can be very resource intensive, you should review this topic before creating your plan.  
  
 For more information about tracking, see [Health and Activity Tracking](http://go.microsoft.com/fwlink/?LinkId=154187) (http://go.microsoft.com/fwlink/?LinkId=154187).  
  
## Configuring and Enabling the DTA Purge and Archive SQL Agent Job  
 This job archives and purges old data from the BizTalk Tracking database, thus keeping it from becoming too large. This is essential for a healthy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system. A large tracking database will begin to affect the performance of the tracking host and any other processes that query the tracking database.  
  
-   **Ensure that the DTA Purge and Archive SQL Agent job is properly configured, enabled, and successfully completing.** This job is not enabled by default because you must first configure it to include a directory where the archive files can be written.  
  
-   **Ensure that the job is able to purge the tracking data as fast as the incoming tracking data is generated.** It is acceptable for the job to get behind during peak load times, but it should always be able to catch up. If the purge job gets behind and is never able to catch up, the BizTalk Tracking database will continue to grow, and performance will eventually be adversely affected.  
  
-   **Review the soft purge and hard purge parameters to ensure you are keeping data long enough but not too long.** For more information about these parameters see [Archiving and Purging the BizTalk Tracking Database](http://go.microsoft.com/fwlink/?LinkID=153816) (http://go.microsoft.com/fwlink/?LinkID=153816).  
  
-   **If you only need to purge the old data and do not need to archive it first, then change the SQL Agent job to call the stored procedure “dtasp_PurgeTrackingDatabase”.** This skips the archive step, and just does the purge. For more information about this stored procedure and changing the SQL Agent job to use it, see [How to Purge Data from the BizTalk Tracking Database](http://go.microsoft.com/fwlink/?LinkID=153817) (http://go.microsoft.com/fwlink/?LinkID=153817).  
  
-   **If you need to keep the BizTalk Tracking database archive files, ensure that you have a process in place to successfully restore and use them.**  
  
-   **If you are having performance issues that are momentarily addressed by purging the BizTalk tracking database, and you want to configure BizTalk to no longer collect tracking information, you may want to consider turning off global tracking.** For information about how to turn off global tracking, see the topic [How to Turn Off Global Tracking](http://go.microsoft.com/fwlink/?LinkID=154193) (http://go.microsoft.com/fwlink/?LinkID=154193).  
  
## Creating a Dedicated Tracking Host  
 When the option to **Allow Host Tracking** is enabled for a host in the BizTalk Server Administration console, instances of that host will run the Tracking Data Decode Service (TDDS) to move tracked data from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database to the BizTalk Tracking database. Since TDDS may be resource intensive, consider creating a "dedicated" tracking host for which the **Allow Host Tracking** option is enabled and which does not run any other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes (such as adapters or orchestrations). If your BizTalk group contains more than one BizTalk server, it is also considered a best practice to create an instance of this host on each server in the group to provide high availability for TDDS.  
  
## Testing to Measure Maximum Sustainable Tracking Throughput  
 Extensive message tracking is a very resource intensive activity and if not properly managed can have an extremely adverse effect on the performance of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. Therefore, you should measure maximum sustainable tracking throughput for your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment to ensure that the system is sustainable and will run indefinitely at a given message flow rate. For more information about measuring maximum sustainable tracking throughput, see [Measuring Maximum Sustainable Tracking Throughput](http://go.microsoft.com/fwlink/?LinkID=153815) (<http://go.microsoft.com/fwlink/?LinkID=153815>).  
  
##  <a name="BKMK_TrackingBP"></a> Best Practices for Tracking  
  
- **Determine the information you need to track during planning** : You should decide during the planning stages which information you need to track, so that after you deploy the project you can set the tracking options and limit the amount of tracked data to give you only the information you need.  
  
- **Do not track all messages**: We recommend that you not track all messages, because each time a message is touched, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes another copy. You can instead narrow the scope by tracking only a specific port. This helps to maximize the performance of your system and to keep the databases uncluttered.  
  
- **Set tracking on send ports and receive ports instead of on a pipeline**: If you set tracking options on pipelines, you will also set the tracking options globally for every port that uses the pipeline. This in turn may result in far more data being tracked than you intend, which will slow system performance. Instead, you can set tracking options on send ports and receive ports.  
  
- **Take into account various factors when you size the BizTalk Tracking database**:  
  
  -   When sizing the BizTalk Tracking database, account for SQL Server factors, such as index size, by adding a contingency multiplier to your calculations.  
  
  -   When determining the size of messages in the BizTalk Tracking database, add the average size of the message context to the message size if it is significant compared to the message size.  
  
  -   To limit the size of messages in the BizTalk Tracking database, limit the number of properties that you promote. You should only use promoted properties if you need them for routing purposes, otherwise use distinguished fields.  
  
  -   If the orchestration **Shape start and end** option is enabled, take into account that a start and stop event for each shape in each orchestration instance is saved in the BizTalk Tracking database.