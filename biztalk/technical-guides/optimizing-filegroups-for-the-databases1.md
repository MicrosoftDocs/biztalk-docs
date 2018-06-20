---
title: "Optimize Database Filegroups | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7dbed4d-95d6-4a41-a69e-737a6f2f5a82
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Optimizing Filegroups for the Databases
File input/output (I/O) contention is frequently a limiting factor, or bottleneck, in a production BizTalk Server environment. BizTalk Server is a very database intensive application and in turn, the SQL Server database used by BizTalk Server is very file I/O intensive.  
  
 This topic describes how to make optimal use of the files and filegroups feature of SQL Server to minimize the occurrence of file I/O contention and improve the overall performance of a BizTalk Server solution.  
  
## Overview  
 Every BizTalk Server solution will eventually encounter file I/O contention as throughput is increased. The I/O subsystem, or storage engine, is a key component of any relational database. A successful database implementation typically requires careful planning at the early stages of a project. This planning should include consideration of the following issues:  
  
- What type of disk hardware to use, such as RAID (redundant array of independent disks) devices. 
  
- How to apportion data on the disks using files and filegroups. For more information about using files and filegroups in SQL Server, see [Database Files and Filegroups](https://docs.microsoft.com/sql/relational-databases/databases/database-files-and-filegroups).
  
- Implementing the optimal index design for improving performance when accessing data. For more information about designing indexes, see [Designing Indexes](https://docs.microsoft.com/sql/relational-databases/sql-server-index-design-guide).
  
- How to set SQL Server configuration parameters for optimal performance. For more information about setting optimal configuration parameters for SQL Server, see [Server Configuration Options](https://docs.microsoft.com/sql/database-engine/configure-windows/server-configuration-options-sql-server). 
  
  One of the primary design goals of BizTalk Server is to ensure that a message is **never** lost. In order to mitigate the possibility of message loss, messages are frequently written to the MessageBox database as the message is processed. When messages are processed by an Orchestration, the message is written to the MessageBox database at every persistence point in the orchestration. These persistence points cause the MessageBox to write the message and related state to physical disk. At higher throughputs, this persistence can result in considerable disk contention and can potentially become a bottleneck.  
  
  Making optimal use of the files and filegroups feature in SQL Server has been shown to effectively address File IO bottlenecks and improve overall performance in BizTalk Server solutions. This optimization should only be done by an experienced SQL Server database administrator and only after all BizTalk Server databases have been properly backed up. This optimization should be performed on all SQL Server computers in the BizTalk Server environment.  
  
  SQL Server files and filegroups can be utilized to improve database performance because this functionality allows a database be created across multiple disks, multiple disk controllers, or RAID (redundant array of independent disks) systems. For example, if your computer has four disks, you can create a database that is made up of three data files and one log file, with one file on each disk. As data is accessed, four read/write heads can concurrently access the data in parallel. This speeds up database operations significantly. For more information about implementing hardware solutions for SQL Server disks, see “Database Performance” in the SQL Server Books online at [http://go.microsoft.com/fwlink/?LinkID=71419](http://go.microsoft.com/fwlink/?LinkID=71419).  
  
  Additionally, files and filegroups enable data placement, because tables can be created in specific filegroups. This improves performance, because all file I/O for a given table can be directed at a specific disk. For example, a heavily used table can be placed on a file in a filegroup, located on one disk, and the other less heavily accessed tables in the database can be located on different files in another filegroup, located on a second disk.  
  
  File IO bottlenecks are discussed in considerable detail in [Bottlenecks in the Database Tier](../technical-guides/bottlenecks-in-the-database-tier.md). The most common indicator that File I/O (Disk I/O) is a bottleneck is the value of the “Physical Disk:Average Disk Queue Length” counter. When the value of the “Physical Disk:Average Disk Queue Length” counter is greater than about 3 for any given disk on any of the SQL Servers, then file I/O is likely a bottleneck.  
  
  If applying file or filegroup optimization doesn't resolve a file I/O bottleneck problem, then it may be necessary to increase the throughput of the disk subsystem by adding additional physical or SAN drives.  
  
  This topic describes how to manually apply file and filegroup optimizations but these optimizations can also be scripted. A sample SQL script is provided at the end of this topic. It is important to note that this script would need to be modified to accommodate the file, filegroup, and disk configuration used by the SQL Server database(s) for any given BizTalk Server solution.  
  
 
## Databases created with a default BizTalk Server configuration  
 Depending on which features are enabled when configuring BizTalk Server, up to 13 different databases may be created in SQL Server and all of these databases are created in the default file group. The default filegroup for SQL Server is the PRIMARY filegroup unless the default filegroup is changed by using the ALTER DATABASE command. The table below lists the databases that are created in SQL Server if all features are enabled when configuring BizTalk Server.  
  
### BizTalk Server Databases  
  
||||  
|-|-|-|  
|**Database**|**Default Database Name**|**Description**|  
|Configuration database|BizTalkMgmtDb|The central meta-information store for all instances of BizTalk Server in the BizTalk Server group.|  
|BizTalk MessageBox database|BizTalkMsgBoxDb|Stores subscriptions predicates. It is a host platform, and keeps queues and state tables for each BizTalk Server host. The MessageBox database also stores the messages and message properties.|  
|BizTalk Tracking database|BizTalkDTADb|Stores business and health monitoring data tracked by the BizTalk Server tracking engine.|  
|BAM Analysis database|BAMAnalysis|SQL Server Analysis Services database that keeps the aggregated historical data for Business Activities.|  
|BAM Star Schema database|BAMStarSchema|Transforms the data collected from Business Activity Monitoring for OLAP Processing. This database is required when using the BAM Analysis database.|  
|BAM Primary Import database|BAMPrimaryImport|Stores the events from Business Activities and then queries for the progress and data after activity instances. This database also performs real-time aggregations.|  
|BAM Archive database|BAMArchive|Stores subscription predicates. The BAM Archive database minimizes the accumulation of Business Activity data in the BAM Primary Import database.|  
|SSO database|SSODB|Securely stores the configuration information for receive locations. Stores information for SSO affiliate applications, as well as the encrypted user credentials to all the affiliate applications.|  
|Rule Engine database|BizTalkRuleEngineDb|Repository for:<br /><br /> -   Policies, which are sets of related rules.<br />-   Vocabularies, which are collections of user-friendly, domain-specific names for data references in rules.|  
|Tracking Analysis Server Administration database|BizTalkAnalysisDb|Stores both business and health monitoring OLAP cubes.|  
  
## Separation of data files and log files  
 As noted above, a default BizTalk Server configuration places the MessageBox Database into a single file in the default filegroup. By default, the data and transaction logs for the MessageBox database are placed on the same drive and path. This is done to accommodate systems with a single disk. A single file/filegroup/disk configuration is **not optimal** in a production environment. For optimal performance, the data files and log files should be placed on separate disks.  
  
> [!NOTE]  
>  Log files are never part of a filegroup. Log space is managed separately from data space.  
  
## The 80/20 rule of distributing BizTalk Server databases  
 The main source of contention in most BizTalk Server solutions, either because of disk I/O contention or database contention, is the BizTalk Server MessageBox database. This is true in both single and multi-MessageBox scenarios. It is reasonable to assume that as much as 80% of the value of distributing BizTalk databases will be derived from optimizing the MessageBox data files and log file. The sample scenario detailed below is focused on optimizing the data files for a MessageBox database. These steps can then be followed for other databases as needed, for example, if the solution requires extensive tracking, then the Tracking database can also be optimized.  
  
## Manually adding files to the MessageBox database, step-by-step  
 This section describes the steps that can be followed to manually add files to the MessageBox database. In this example three filegroups are added and then a file is added to each filegroup to distribute the files for the MessageBox across multiple disks.   
  
> [!NOTE]  
>  For purposes of the performance testing done for this guide, filegroups were optimized through the use of a script which will be published as part of the BizTalk Server Performance Optimizations Guide. The steps below are provided for reference purposes only.  
  
### Manually adding files to the MessageBox database on SQL Server
  
1. Open **SQL Server Management Studio** to display the **Connect to Server** dialog box.  
  
     ![SQL Server Administration login screen](../technical-guides/media/641a03f4-362c-4dde-8c9d-ac313d8881e3.gif "641a03f4-362c-4dde-8c9d-ac313d8881e3")  
  
2.  In the **Server name** field of the **Connect to Server** dialog box, enter the name of the SQL Server instance that houses the BizTalk Server MessageBox databases, and then click the **Connect** button to display the **Microsoft SQL Server Management Studio** dialog box.  
  
     In the **Object Explorer** pane of SQL Server Management Studio, expand **Databases** to view the databases for this instance of SQL Server.  
  
     ![SQL Server Management Studio, Object Explorer](../technical-guides/media/81f13912-fedc-48c3-9669-c18863e637b1.gif "81f13912-fedc-48c3-9669-c18863e637b1")  
  
3.  Right-click the database for which to add the files, and then click **Properties** to display the **Database Properties** dialog box for the database.  
  
     ![SQL Server Database Properties dialog box](../technical-guides/media/82ae7c11-5b3a-4312-876c-70876abdd65c.gif "82ae7c11-5b3a-4312-876c-70876abdd65c")  
  
4.  In the **Database Properties** dialog box, select the **Filegroups** page. Click the **Add** button to create additional filegroups for the BizTalkMsgBoxDb databases. In the example below, three additional filegroups are added.  
  
     ![SQL Server, adding filegroups to a database](../technical-guides/media/6be47c0e-06c3-45d9-bce2-a42453da7d19.gif "6be47c0e-06c3-45d9-bce2-a42453da7d19")  
  
5.  In the **Database Properties** dialog box, select the **Files** page.  
  
     Click the **Add** button to create additional files to add to the filegroups, and then click **OK**. The MessageBox database is now distributed across multiple disks, which will provide a significant performance advantage over a single disk configuration.  
  
     In the example below, a file is created for each of the filegroups that were created earlier and each file is placed on a separate disk.  
  
     ![SQL Server, adding files to a filegroup](../technical-guides/media/d5d5c5df-d483-4f01-8128-f98228de51b9.gif "d5d5c5df-d483-4f01-8128-f98228de51b9")  
  
## Sample SQL script for adding filegroups and files to the BizTalk MessageBox database  
 The sample SQL script below performs the same tasks that were completed manually in the previous section.  
This sample script assumes the existence of distinct logical drives G through J. The script creates filegroups and files for each filegroup and places the log files on the J drive.  
  
> [!NOTE]  
>  Because SQL Server writes to its log files sequentially, there is no performance advantage realized by creating multiple log files for a SQL Server database.  
  
```  
-- Filegroup changes are made using the master database  
USE [master]  
GO  
  
-- Script-wide declarations  
DECLARE @CommandBuffer nvarchar(2048)  
DECLARE @FG1_Path nvarchar(1024)  
DECLARE @FG2_Path nvarchar(1024)  
DECLARE @FG3_Path nvarchar(1024)  
DECLARE @Log_Path nvarchar(1024)  
  
-- Set the default path for all filegroups  
SET @FG1_Path = N'G:\BizTalkMsgBoxDATA\'  
SET @FG2_Path = N'H:\BizTalkMsgBoxDATA\'  
SET @FG3_Path = N'I:\BizTalkMsgBoxDATA\'  
SET @Log_Path = N'J:\BizTalkMsgBoxLog\'  
  
ALTER DATABASE [BizTalkMsgBoxDb] ADD FILEGROUP [BTS_MsgBox_FG1]  
SET @CommandBuffer = N'ALTER DATABASE [BizTalkMsgBoxDb] ADD FILE ( NAME = N''BizTalkMsgBoxDb_FG1'', FILENAME = N''' + @FG1_Path +   
N'BizTalkMsgBoxDb_FG1.ndf'' , SIZE = 102400KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB ) TO FILEGROUP [BTS_MsgBox_FG1]'  
EXECUTE (@CommandBuffer)  
  
ALTER DATABASE [BizTalkMsgBoxDb] ADD FILEGROUP [BTS_MsgBox_FG2]  
SET @CommandBuffer = N'ALTER DATABASE [BizTalkMsgBoxDb] ADD FILE ( NAME = N''BizTalkMsgBoxDb_FG1'', FILENAME = N''' + @FG2_Path +   
N'BizTalkMsgBoxDb_FG2.ndf'' , SIZE = 102400KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB ) TO FILEGROUP [BTS_MsgBox_FG2]'  
EXECUTE (@CommandBuffer)  
  
ALTER DATABASE [BizTalkMsgBoxDb] ADD FILEGROUP [BTS_MsgBox_FG3]  
SET @CommandBuffer = N'ALTER DATABASE [BizTalkMsgBoxDb] ADD FILE ( NAME = N''BizTalkMsgBoxDb_FG1'', FILENAME = N''' + @FG3_Path +   
N'BizTalkMsgBoxDb_FG3.ndf'' , SIZE = 102400KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB ) TO FILEGROUP [BTS_MsgBox_FG3]'  
EXECUTE (@CommandBuffer)  
  
ALTER DATABASE [BizTalkMsgBoxDb] MODIFY FILE ( NAME = N'BizTalkMsgBoxDb_log', SIZE = 10240KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB )  
  
GO -- Completes the previous batch, as necessary  
```  
  
 The sample SQL script below could be used to set a particular filegroup as the default filegroup:  
  
```  
USE [BizTalkMsgBoxDb]  
GO  
declare @isdefault bit  
SELECT @isdefault=convert(bit, (status & 0x10)) FROM sysfilegroups WHERE groupname=N'BTS_MsgBox_FG1'  
if(@isdefault=0)  
ALTER DATABASE [BizTalkMsgBoxDb] MODIFY FILEGROUP [BTS_MsgBox_FG1] DEFAULT  
GO  
```  
  
 The advantage to scripting is that scripts can perform multiple tasks quickly, can be reproduced precisely, and reduce the possibility of human error. The disadvantage of scripting is that the execution of an incorrectly written script can potentially cause serious problems that could require the BizTalk Server databases to be re-configured from scratch. Therefore, it is of utmost importance that SQL scripts such as the sample script listed in this topic are thoroughly tested before being executed in a production environment.