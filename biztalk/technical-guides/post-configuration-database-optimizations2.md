---
title: "Post-Configuration Database Optimizations2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 609eda22-8399-4b7c-b860-21b495d2f68d
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Post-Configuration Database Optimizations
In addition to following the recommendations in [Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md), several steps should be followed to optimize BizTalk Server database performance on SQL Server *after* BizTalk Server has been installed and the BizTalk Server databases have been configured. This topic provides a list of these optimizations.  
  
## Consider setting the 'text in row' table option on specific MessageBox database tables  
 SQL Server provides a table option called **text in row** to declare that the contents of the fields of type **text**, **ntext**, or **image** data whose dimensions are smaller than those of a data page (8Kb) must be stored in a data row. By setting this option on BizTalkMsgBoxDb tables (Parts table, Spool table and DynamicStateInfo Tables) , you can increase message throughput when working with small messages which have a small context and orchestrations that have a small persistence size.  
  
- **Parts Table**: When the message size is smaller than the dimensions of a data page that are of 8kb, applying the **text in row** table option on the Parts table can lead to BizTalk Server performance improvement. The Parts table contains the following fields:  
  
  - **ImgPart**: Contains a message part or message part fragment.  
  
  - **ImgPropBag**: Contains the message part property bag.  
  
    This way, when looping against the MessageBox, the Message Agent running within a BizTalk host can retrieve a batch of messages from the Parts table by reading small amount of pages. Depending on the specific scenario and hardware configuration, this technique can reduce CPU utilization both on the SQL Server and BizTalk Server, and provide a significant improvement in terms of latency and throughput.  
  
- **Spool Table**: When the average size of the message context is less than 8 kb, enabling the **text in row** table option on the Spool table helps you reduce the number of accesses when reading messages from the MessageBox along with their context. To apply this option to the Spool table, you must eliminate unnecessary context properties and distinguished fields to reduce the size of the message context lower than 8 Kb.  
  
- **DynamicStateInfo Tables** These tables, one for each host, contain a field of type image called imgData that contains binary-serialized orchestration state when they encounter a persistence point during their execution. When the internal state of orchestrations within a host HostA is so small that its size once serialized is less than 8 kb, the **text in row** technique can successfully be applied to the DynamicStateInfo_HostA table. Therefore we recommend that you keep the internal state of orchestrations as small as possible. This technique can significantly reduce the time that is spent by the XLANG Engine to serialize, persist, de-serialize and restore the internal state of an orchestration in case of persistence point.  
  
  We used the following settings in our lab tests:  
  
- EXEC sp_tableoption N'Spool', 'text in row', '6000'  
  
- EXEC sp_tableoption N'Parts', 'text in row', '6000'  
  
## Define auto-growth settings for BizTalk Server databases to a fixed value instead of a percentage value  
  
-   SQL Server database auto-growth is a blocking operation, which hinders BizTalk Server database performance. Therefore it is important to allocate sufficient space for the BizTalk Server databases in advance to minimize the occurrence of database auto-growth.  
  
-   Database auto-growth should be set to a fixed number of megabytes instead of to a percentage (specify file growth **In Megabytes**). This should be done so that, if auto-growth occurs, it does so in a measured fashion. This reduces the likelihood of excessive database growth. The growth increment for BizTalk Server databases should generally be no lower than 100 MB.  
  
## Pre-size BizTalk Server databases to appropriate size with multiple data files  
 When SQL Server increases the size of a file, it must first initialize the new space before it can be used. This is a blocking operation that involves filling the new space with empty pages. SQL Server 2005 or later running on Windows Server 2003 or later supports “instant file initialization.” This can greatly reduce the performance impact of a file growth operation. For more information, see [Database File Initialization](http://go.microsoft.com/fwlink/?LinkId=132063) (http://go.microsoft.com/fwlink/?LinkId=132063) in the SQL Server books online. This topic provides steps for enabling instant file initialization.  
  
 The following list describes the BizTalk Server database configurations used in our lab tests:  
  
- **BizTalk DTADB (BizTalk Tracking database files):** Data file having a file size of 2048 MB with 100 MB growth and a log file of 1024 MB with 100 MB growth.  
  
- **BizTalkMgmtdb (BizTalk Management database files):** Data file having a file size of 512 MB with 100 MB growth and a log file of 512 MB with 100 MB growth.  
  
- **SSODB:** Data file having a file size of 512 MB with 100 MB growth and a log file of 512 MB with 100 MB growth.  
  
- **BizTalkMsgBoxDb (BizTalk MessageBox databases):** 8 data files, each having a file size of 2 GB with 100 MB growth and a log file of 20 GB with 100 MB growth. Because the BizTalk MessageBox databases are the most active, we recommend you place the data files and transaction log files on dedicated drives to reduce the likelihood of problems with disk I/O contention. In our lab environment, we used one drive for each of the following:  
  
  -   MessageBox data files  
  
  -   MessageBox transaction log files  
  
  The following SQL script can be used to pre-size BizTalkMsgBoxDb which initially has a data file on drive J (J:\BizTalkMsgBoxDb.mdf) and a log file on drive K (K:\BizTalkMsgBoxDb_log.LDF):  
  
> [!IMPORTANT]  
>  This script is provided “as is,” is intended for demo or educational purposes only, and is to be used at your own risk. Use of this script is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this script.  
  
```  
EXEC dbo.sp_helpdb BizTalkMsgBoxDb  
ALTER DATABASE BizTalkMsgBoxDb MODIFY FILE (NAME = BizTalkMsgBoxDb , FILENAME = 'J:\BizTalkMsgBoxDb.mdf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_2 , FILENAME = 'J:\BizTalkMsgBoxDb_2.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_3 , FILENAME = 'J:\BizTalkMsgBoxDb_3.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_4 , FILENAME = 'J:\BizTalkMsgBoxDb_4.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_5 , FILENAME = 'J:\BizTalkMsgBoxDb_5.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_6 , FILENAME = 'J:\BizTalkMsgBoxDb_6.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_7 , FILENAME = 'J:\BizTalkMsgBoxDb_7.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_8 , FILENAME = 'J:\BizTalkMsgBoxDb_8.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
GO  
ALTER DATABASE BizTalkMsgBoxDb MODIFY FILE (NAME = BizTalkMsgBoxDb_log , FILENAME = 'K:\BizTalkMsgBoxDb_log.LDF', SIZE =  20GB , FILEGROWTH = 100MB)  
GO  
```  
  
## Move the Backup BizTalk Server output directory to a dedicated LUN  
 Move the Backup BizTalk (Full and Log backup) output directory to a dedicated LUN, and then edit the Backup BizTalk Server job to point to the dedicated LUN. Moving the Backup BizTalk Server output directory to a dedicated LUN will reduce disk I/O contention when the job is running by writing to a different disk than the job is reading from. For more information about configuring the Backup BizTalk Server job see [How to Configure the Backup BizTalk Server Job](http://go.microsoft.com/fwlink/?LinkID=153813) (http://go.microsoft.com/fwlink/?LinkID=153813) in BizTalk Server 2010 help.  
  
## Verify that the BizTalk Server SQL Agent Jobs are running  
 BizTalk Server includes several SQL Server Agent jobs that perform important functions to keep your servers operational and healthy. You should monitor the health of these jobs and ensure they are running without errors. One of the most common causes of performance problems in BizTalk Server is the BizTalk Server SQL Agent Jobs are not running, which in turn can cause the MessageBox and Tracking databases to grow unchecked. Follow these steps to ensure the BizTalk Server SQL Agent Jobs are running without problems:  
  
1.  **Verify that the SQL Server Agent service is running**.  
  
2.  **Verify that the SQL Server Agent jobs installed by BizTalk Server are enabled and running successfully**.  
    The BizTalk Server SQL Server Agent jobs are crucial: if they are not running, system performance will degrade over time.  
  
3.  **Verify that the BizTalk Server SQL Server Agent jobs are completing in a timely manner**.   
    Set up the most recent version of Microsoft System Center Operations Manager to monitor the jobs.  
    You should be aware of schedules that are particular to certain jobs:  
  
    -   The MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job runs continuously by default. Monitoring software should take this schedule into account and not produce warnings.  
  
    -   The MessageBox_Message_Cleanup_BizTalkMsgBoxDb job is not enabled or scheduled, but it is started by the MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job every 10 seconds. Therefore, this job should not be enabled, scheduled, or manually started.  
  
4.  **Verify that the Startup type of the SQL Server Agent service is configured correctly**.  
    Verify the SQL Server Agent service is configured with a **Startup type** of **Automatic** unless the SQL Server Agent service is configured as a cluster resource on a Windows Server cluster. If the SQL Server Agent service is configured as a cluster resource, then you should configure the **Startup type** as **Manual** because the service will be managed by the Cluster service.  
  
## Configure Purging and Archiving of Tracking Data  
 Follow these steps to ensure that purging and archiving of tracking data is configured correctly:  
  
1.  Ensure the SQL Agent job “DTA Purge and Archive” is properly configured, enabled, and successfully completing. For more information, see [How to Configure the DTA Purge and Archive Job](http://go.microsoft.com/fwlink/?LinkID=153814) (http://go.microsoft.com/fwlink/?LinkID=153814) in the BizTalk Server documentation.  
  
2.  Ensure the job is able to purge the tracking data as fast as the incoming tracking data is generated. For more information, see [Measuring Maximum Sustainable Tracking Throughput](http://go.microsoft.com/fwlink/?LinkID=153815) (http://go.microsoft.com/fwlink/?LinkID=153815) in the BizTalk Server documentation.  
  
3.  Review the soft purge and hard purge parameters to ensure you are keeping data for the optimal length of time. For more information, see [Archiving and Purging the BizTalk Tracking Database](http://go.microsoft.com/fwlink/?LinkID=153816) (http://go.microsoft.com/fwlink/?LinkID=153816) in the BizTalk Server documentation.  
  
4.  If you only need to purge the old data and do not need to archive it first, change the SQL Agent job to call the stored procedure “dtasp_PurgeTrackingDatabase.” For more information, see [How to Purge Data from the BizTalk Tracking Database](http://go.microsoft.com/fwlink/?LinkID=153817) (http://go.microsoft.com/fwlink/?LinkID=153817) in the BizTalk Server documentation.  
  
## Monitor and reduce DTC log file disk I/O contention  
 The Distributed Transaction Coordinator (DTC) log file can become a disk I/O bottleneck in transaction-intensive environments. This is especially true when using adapters that support transactions, such as SQL Server, MSMQ, or MQSeries, or in a multi-MessageBox environment. Transactional adapters use DTC transactions, and multi-MessageBox environments make extensive use of DTC transactions. To ensure the DTC log file does not become a disk I/O bottleneck, you should monitor the disk I/O usage for the disk where the DTC log file resides on the SQL Server database servers. If disk I/O usage for the disk where the DTC log file resides becomes excessive, consider moving the DTC log file to a faster disk. In an environment where SQL Server is clustered, this is not as much of a concern because the log file will already be on a shared drive, which will likely be a fast SAN drive with multiple spindles. You should nevertheless still monitor the disk I/O usage. This is because it can become a bottleneck in non-clustered environments or when the DTC log file is on a shared disk with other disk-intensive files.  
  
## Separate the MessageBox and Tracking Databases  
 Because the BizTalk MessageBox and BizTalk Tracking databases are the most active, we recommend you place the data files and transaction log files for each of these on dedicated drives to reduce the likelihood of problems with disk I/O contention. For example, you would need four drives for the MessageBox and BizTalk Tracking database files, one drive for each of the following:  
  
- MessageBox data files  
  
- MessageBox transaction log files  
  
- BizTalk Tracking (DTA) data files  
  
- BizTalk Tracking (DTA) transaction log files  
  
  Separating the BizTalk MessageBox and BizTalk Tracking databases and separating the database files and transaction log files on different physical disks are considered best practices for reducing disk I/O contention. Try to spread the disk I/O across as many physical spindles as possible. You can also reduce disk I/O contention by placing the BizTalk Tracking database on a dedicated SQL Server; however, you should still follow the practices above with regards to separating data files and transaction log files.  
  
## Optimize filegroups for the BizTalk Server databases  
 Follow the steps in [Optimizing Filegroups for the Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md) and the [BizTalk Server Database Optimization](http://go.microsoft.com/fwlink/?LinkId=101578) white paper ([http://go.microsoft.com/fwlink/?LinkId=101578](http://go.microsoft.com/fwlink/?LinkId=101578)) to create additional filegroups and files for the BizTalk Server databases. This will greatly increase the performance of the BizTalk Server databases from a single disk configuration.  
  
## See Also  
 [Optimizing Database Performance](../technical-guides/optimizing-database-performance.md)