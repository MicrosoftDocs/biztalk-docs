---
title: "How to Identify Bottlenecks in the BAM Primary Import Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0372f1f1-d892-4f7d-b6c4-e0f2b5a02f1c
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Identify Bottlenecks in the BAM Primary Import Database
To identify bottlenecks in the Business Activity Monitoring (BAM) database, perform the following steps:  
  
1. Ensure that the Active Instances count is not climbing.  
  
2. Ensure that the SQL-Agent Service is running.  
  
3. If OLAP Analysis is configured, ensure that the BAM_AN_\<activityname\> job is running at periodic intervals.  
  
4. Ensure that BAM_DM_\<activityname\> (Data Maintenance) job is scheduled to run at periodic intervals.  
  
   > [!NOTE]
   >  In high usage scenarios BAM database activity can impact the performance of other BizTalk Server databases, which will affect overall BizTalk Server performance. In this case consider taking the following actions:  
   > 
   > - Consider decreasing the duration of all BAM activities from the default value (6 months) to 1 month or less. This will reduce the time period for which BAM data is maintained in the BAMPrimaryImport database before being archived. Use the BAM Management Utility `set-activitywindow` command to modify the duration of BAM activities. For more information about the BAM Management Utility activity management commands see [Activity Management Commands](http://go.microsoft.com/fwlink/?LinkId=210417) (http://go.microsoft.com/fwlink/?LinkId=210417).  
   >   -   Move the BAM Archive database to an instance of SQL Server that does not host any BizTalk MessageBox databases. This will prevent these databases from competing for resources and improve overall performance.  
  
5. Use a dedicated host for tracking and measure the Host Queue Length performance counter when under load.  
  
6. Check the Spool Table size performance counter for an increasing trend over time.  
  
7. Check the Archive/Purge job execution duration for long execution times.  
  
8. Check disk responsiveness (Disk Seconds per Read/Write performance counter) on the disk hosting the BizTalk Tracking database.  
  
## See Also  
 [Bottlenecks in the Database Tier](../technical-guides/bottlenecks-in-the-database-tier.md)