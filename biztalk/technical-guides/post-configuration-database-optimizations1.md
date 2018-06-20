---
title: "Post-Configuration Database Optimizations1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 763b5358-97ed-4ada-8318-0ad07388ba89
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Post-Configuration Database Optimizations
In addition to following the recommendations in [Pre-Configuration Database Optimizations](../technical-guides/post-configuration-database-optimizations1.md), several steps should be followed to optimize BizTalk Server database performance on SQL Server *after* BizTalk Server has been installed and the BizTalk Server databases have been configured. This topic provides a list of these optimizations.  
  
## Pre-allocate space for BizTalk Server databases and define auto-growth settings for BizTalk Server databases to a fixed value instead of a percentage value  
  
-   SQL Server database auto-growth is a blocking operation that hinders BizTalk Server database performance. Therefore it is important to allocate sufficient space for the BizTalk Server databases in advance to minimize the occurrence of database auto-growth.  
  
-   Database auto-growth should be set to a fixed number of megabytes instead of to a percentage (specify file growth **In Megabytes**). This should be done so if auto-growth occurs, it does so in a measured fashion which reduces the likelihood of excessive database growth. The growth increment should generally be no larger than 100 MB (for large files), 10 MB (for medium-sized files), or 1 MB (for small files).  
  
-   When SQL Server increases the size of a file, the new space must first be initialized before it can be used. This is a blocking operation that involves filling the new space with empty pages. SQL Server 2005 running on Windows Server 2003 or later supports “instant file initialization.” This can greatly reduce the performance impact of a file growth operation. For more information, see "Database File Initialization" in the SQL Server 2008 documentation at [http://go.microsoft.com/fwlink/?LinkId=132063](http://go.microsoft.com/fwlink/?LinkId=132063). This topic provides steps for enabling instant file initialization.  
  
## Move the Backup BizTalk Server output directory to a dedicated LUN  
 Move the Backup BizTalk Server (Full and Log backup) output directory to dedicated LUN, Edit steps 1 and 2 (insert new output path) of the Backup BizTalk Server [BizTalkMgmtDb] job. Moving the Backup BizTalk Server output directory to a dedicated LUN will reduce disk I/O contention when the job is running by writing to a different disk than the job is reading from.  
  
## Verify the BizTalk Server SQL Agent Jobs are running  
 BizTalk Server includes several SQL Server Agent jobs that perform important functions to keep your servers operational and healthy. You should monitor the health of these jobs and ensure they are running without errors. One of the most common causes of performance problems in BizTalk Server is the BizTalk Server SQL Agent Jobs are not running, which in turn can cause the MessageBox and Tracking databases to grow unchecked. Follow these steps to ensure the BizTalk Server SQL Agent Jobs are running without problems:  
  
 One of the most common causes of performance problems in BizTalk Server is the BizTalk Server SQL Agent Jobs are not running, which in turn can cause the MessageBox and Tracking databases to grow unchecked. Follow these steps to ensure the BizTalk Server SQL Agent Jobs are running without problems:  
  
-   **Verify the SQL Server Agent service is running**.  
  
-   **Verify the SQL Server Agent jobs installed by BizTalk Server are enabled and running successfully**.  
  
     The BizTalk Server SQL Server Agent jobs are crucial—if they are not running, system performance will degrade over time.  
  
-   **Verify the BizTalk Server SQL Server Agent jobs are completing in a timely manner**.  
  
     Set up Microsoft Operations Manager (MOM) 2005 or Microsoft System Center Operations Manager 2007 to monitor the jobs.  
  
     You should be aware of schedules that are particular to certain jobs:  
  
    -   The MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job runs continuously by default. Monitoring software should take this schedule into account and not produce warnings.  
  
    -   The MessageBox_Message_Cleanup_BizTalkMsgBoxDb job is not enabled or scheduled, but it is started by the MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job every 10 seconds. Therefore, this job should not be enabled, scheduled, or manually started.  
  
-   **Verify the Startup type of the SQL Server Agent service is configured correctly**.  
  
     Verify the SQL Server Agent service is configured with a **Startup type** of **Automatic** unless the SQL Server Agent service is configured as a cluster resource on a Windows Server cluster. If the SQL Server Agent service is configured as a cluster resource, then you should configure the **Startup type** as **Manual** because the service will be managed by the Cluster service.  
  
## Configure Purging and Archiving of Tracking Data  
 Follow these steps to ensure that purging and archiving of tracking data is configured correctly:  
  
-   Ensure the SQL Agent job “DTA Purge and Archive” is properly configured, enabled, and successfully completing. For more information, see "How to Configure the DTA Purge and Archive Job" in the BizTalk Server documentation at [http://go.microsoft.com/fwlink/?LinkId=104908](http://go.microsoft.com/fwlink/?LinkId=104908).  
  
-   Ensure the job is able to purge the tracking data as fast as the incoming tracking data is generated. For more information, see "Measuring Maximum Sustainable Tracking Throughput" in the BizTalk Server 2006 R2 documentation at [http://go.microsoft.com/fwlink/?LinkId=104909](http://go.microsoft.com/fwlink/?LinkId=104909).  
  
-   Review the soft purge and hard purge parameters to ensure you are keeping data for the optimal length of time. For more information, see "Archiving and Purging the BizTalk Tracking Database" in the BizTalk Server documentation at [http://go.microsoft.com/fwlink/?LinkId=101585](http://go.microsoft.com/fwlink/?LinkId=101585).  
  
-   If you only need to purge the old data and do not need to archive it first, change the SQL Agent job to call the stored procedure “dtasp_PurgeTrackingDatabase.” For more information, see "How to Purge Data from the BizTalk Tracking Database" in the BizTalk Server documentation at [http://go.microsoft.com/fwlink/?LinkId=101584](http://go.microsoft.com/fwlink/?LinkId=101584).  
  
## Monitor and reduce DTC log file disk I/O contention  
 The Microsoft Distributed Transaction Coordinator (MS DTC) log file can become a disk I/O bottleneck in transaction-intensive environments. This is especially true when using adapters that support transactions, such as SQL Server, MSMQ, or MQSeries, or in a multi-MessageBox environment. Transactional adapters use DTC transactions, and multi-MessageBox environments make extensive use of DTC transactions. To ensure the DTC log file does not become a disk I/O bottleneck, you should monitor the disk I/O usage for the disk where the DTC log file resides on the SQL Server database server(s). If disk I/O usage for the disk where the DTC log file resides becomes excessive then consider moving the DTC log file to a faster disk. In an environment where SQL Server is clustered, this is not as much of a concern because the log file will already be on a shared drive, which will likely be a fast SAN drive with multiple spindles. You should nevertheless still monitor the disk I/O usage because it can become a bottleneck in non-clustered environments or when the DTC log file is on a shared disk with other disk-intensive files.  
  
 To ensure the DTC log file does not become a disk I/O bottleneck, you should monitor the disk I/O usage for the disk where the DTC log file resides on the SQL Server database server(s). If disk I/O usage for the disk where the DTC log file resides becomes excessive, then consider moving the DTC log file to a faster disk.  
  
 In an environment where SQL Server is clustered, this is not as much of a concern because the log file will already be on a shared drive, which will likely be a fast SAN drive with multiple spindles. You should nevertheless still monitor the disk I/O usage because it can become a bottleneck in non-clustered environments or when the DTC log file is on a shared disk with other disk-intensive files.  
  
## Separate the MessageBox and Tracking Databases  
 Because the BizTalk MessageBox and BizTalk Tracking databases are the most active, we recommend you place the data files and transaction log files for each of these on dedicated drives to reduce the likelihood of problems with disk I/O contention. For example, you would need four drives for the MessageBox and BizTalk Tracking database files, one drive for each of the following:  
  
- MessageBox data file(s)  
  
- MessageBox transaction log file(s)  
  
- BizTalk Tracking (DTA) data file(s)  
  
- BizTalk Tracking (DTA) transaction log file(s)  
  
  Separating the BizTalk MessageBox and BizTalk Tracking databases and separating the database files and transaction log files on different physical disks are considered best practices for reducing disk I/O contention. Try to spread the disk I/O across as many physical spindles as possible. You can also reduce disk I/O contention by placing the BizTalk Tracking database on a dedicated SQL Server, however, you should still follow the practices above with regards to separating data files and transaction log files.  
  
## Optimize filegroups for the BizTalk Server databases  
 Follow the steps in [Optimizing Filegroups for the Databases1](../technical-guides/optimizing-filegroups-for-the-databases1.md) and the "BizTalk Server Database Optimization" whitepaper at [http://go.microsoft.com/fwlink/?LinkId=101578](http://go.microsoft.com/fwlink/?LinkId=101578) to create additional filegroups and files for the BizTalk Server databases. This will greatly increase the performance of the BizTalk Server databases from a single disk configuration.