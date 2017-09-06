---
title: "Best Practices for Message and Instance Data Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HAT, best practices"
  - "best practices, HAT"
ms.assetid: 2ac5c87b-2059-4912-9cec-2ae4eaac56df
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Best Practices for Message and Instance Data Tracking
Review the following best practices for using historical and tracked data.  
  
-   **Review the security considerations for using historical and tracked data**  
  
    -   For more information about security considerations for historical and tracked data, see [Security Considerations for Message and Instance Data Tracking](../core/security-considerations-for-message-and-instance-data-tracking.md).  
  
-   **Ensure that the SQL Server Agent service is running on all MessageBox databases**  
  
    -   SQL Server Agent makes message bodies available to WMI, and historical and tracked data. This enables you to run jobs to clean up the MessageBox databases. For more information about SQL Server Agent, see SQL Server Books Online.  
  
-   **Enable message body tracking**  
  
    -   Message body tracking is required to save messages after service instances processing is complete.  
  
-   **Configure tracking as appropriate for your business needs**  
  
    -   Before you can view historical and tracked data, you must first configure tracking using the BizTalk Server Administration Console. There are multiple considerations to keep in mind when enabling or disabling tracking options. The more data you track, the faster your BizTalk Tracking (BizTalkDTADb) database will grow in size, which can adversely affect your runtime performance. For more information, see [Configuring Tracking Using the BizTalk Server Administration Console](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef).  
  
-   **Select the appropriate type of tracking for troubleshooting or auditing**  
  
    -   For troubleshooting either in a development environment, or in a staging or production environment, you should enable all tracking options so that you can see artifact events, message properties, message bodies and orchestration events in detail. This provides a rich set of tracked information that you can use to recreate the sequence of events in your system and debug your application.  
  
    -   For production level auditing, carefully choose the events you want to audit and then enable tracking only for those events. For example, many enterprises want to be able to prove that a message entered and exited the system. To achieve this, you should enable inbound tracking on the corresponding receive port and enable outbound tracking on the corresponding send port. If necessary, you can add message property and message body tracking.  
  
    -   For measuring business Key Performance Indicators (KPIs) or progress as measured by the achievement of specified business milestones, you should use Business Activity Monitoring (BAM) tracking. BAM tracking has limited abilities to track and store message bodies, so if this is important, you should use historical and tracked data  in conjunction with BAM tracking. For more information about BAM tracking, see [Using Business Activity Monitoring](../core/using-business-activity-monitoring.md).  
  
-   **Archive and purge data from the BizTalk Tracking (BizTalkDTADb) database on a regular basis**  
  
    -   If you have enabled tracking, you should archive and purge data from the BizTalk Tracking database on a regular basis to help keep the database appropriately sized, which helps improve system performance. For more information, see [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md).  
  
## See Also  
 [Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md)