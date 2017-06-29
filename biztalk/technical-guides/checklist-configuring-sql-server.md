---
title: "Checklist: Configuring SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: edd20f24-8a72-40b7-abee-81fbd3ceefda
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Configuring SQL Server
This topic lists steps that you should follow when preparing [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] or [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] for use in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] production environment.  
  
-   [Checklist: Configuring SQL Server](../technical-guides/checklist-configuring-sql-server.md)  
  
-   [Performing SQL Server Maintenance Procedures](../technical-guides/checklist-configuring-sql-server.md#BKMK_Maintain)  
  
-   [Backing Up the BizTalk Server Databases](../technical-guides/checklist-configuring-sql-server.md#BKMK_Backup)  
  
-   [Using SQL Server Log Shipping For Disaster Recovery](../technical-guides/checklist-configuring-sql-server.md#BKMK_Disaster)  
  
-   [Monitoring BizTalk Server SQL Agent Jobs](../technical-guides/checklist-configuring-sql-server.md#BKMK_Jobs)  
  
-   [Purging and Archiving Tracking Data](../technical-guides/checklist-configuring-sql-server.md#BKMK_Purge)  
  
<a name="BKMK_Config"></a>   
## Configuring SQL Server  
  
|Steps|Reference|  
|-----------|---------------|  
|Monitor and reduce [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database files disk I/O contention.|-   We recommend that you proactively monitor the disk I/O usage for the disks that house the data and transaction log files.<br />-   We recommend that the data files and transaction log files for each of these be placed on dedicated drives to reduce the likelihood of disk I/O contention becoming a problem.<br />-   You can reduce disk I/O contention by separating the MessageBox and Tracking (DTA) databases, and by separating the database files and transaction log files on different physical disks.<br /><br /> For more information, see [Monitoring and Reducing Database IO Contention](../Topic/Monitoring%20and%20Reducing%20Database%20IO%20Contention.md)|  
|Ensure [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is configured on properly-aligned disk partitions|Properly aligned disk partitions could result in significant decrease in latency thereby improving the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance, which in turn enhances [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance. On the contrary, nonaligned disk partitions can negatively affect I/O performance, thereby degrading the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance.<br /><br /> For more information about how properly aligned disk partitions can positively affect performance, see ["Disk Partition Alignment Best Practices for SQL Server”](http://go.microsoft.com/fwlink/?LinkId=154073) (http://go.microsoft.com/fwlink/?LinkId=154073).|  
|Keep the events you monitor with the SQL Server Profiler|Use SQL Server Profiler to monitor only the events in which you are interested. If traces become too large, you can filter them based on the information you want, so that only a subset of the event data is collected. Monitoring too many events adds overhead to the server and the monitoring process, and can cause the trace file or trace table to grow very large, especially when the monitoring process takes place over a long period of time.|  
|Monitor and reduce DTC log file disk I/O contention.|[Monitoring and Reducing DTC Log File Disk IO Contention](../Topic/Monitoring%20and%20Reducing%20DTC%20Log%20File%20Disk%20IO%20Contention.md)|  
|Provide high availability for the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases.|[Planning for Database Availability](../Topic/Planning%20for%20Database%20Availability.md)|  
|Review active/active SQL Server cluster configuration for failover scenarios.|[Reviewing and Testing SQL Server Cluster Configuration for Failover Scenarios](../Topic/Reviewing%20and%20Testing%20SQL%20Server%20Cluster%20Configuration%20for%20Failover%20Scenarios.md)|  
|Use default configuration settings for:<br /><br /> -   Max Degree of Parallelism (MDOP).<br />-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] statistics on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox database.<br />-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database index rebuilds and defragmentation.|[SQL Server Settings That Should Not Be Changed](../Topic/SQL%20Server%20Settings%20That%20Should%20Not%20Be%20Changed.md)|  
|Enable trace flag 1118 (TF1118) as a startup parameter for all instances of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].|Implementing TF1118 helps reduce contention across the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances by removing almost all single page allocations. For more information see Microsoft Knowledge Base article 328551, ["Concurrency enhancements for the tempdb database"](http://go.microsoft.com/fwlink/?LinkId=153694) (http://go.microsoft.com/fwlink/?LinkId=153694). **Note:**  For more information about TF1118 see [“Misconceptions around TF1118”](http://go.microsoft.com/fwlink/?LinkId=158271) (http://go.microsoft.com/fwlink/?LinkId=158271). Note that the content at this link is not owned by Microsoft and Microsoft does not guarantee the accuracy of the content.|  
|Split the tempdb database into multiple data files of equal size on each [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|Ensure that the data files used for the tempdb are of equal size. This is critical because the proportional fill algorithm used by [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is based on the size of the data files. If data files are created with unequal sizes, the proportional fill algorithm will use the largest file more for Global Allocation Map (GAM) allocations rather than spreading the allocations between all the files, thereby defeating the purpose of creating multiple data files. As a general guideline, create one data file for each CPU on the server and then adjust the number of files up or down as necessary. Note that a dual-core CPU is considered to be two CPUs. In any event, the number of data files must not be greater than 8 no matter how many additional cores are available on the computer. For more information about tempdb files, see [Optimizing tempdb Performance](http://go.microsoft.com/fwlink/?LinkId=158272) (http://go.microsoft.com/fwlink/?LinkId=158272) in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation.|  
|If you are running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and hosting your databases on computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] with sufficient physical memory, configure the instances of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] to use Address Windowing Extensions (AWE) memory.|On an x86 computer, [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] should be configured to use more than 2 GB of physical memory. [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] includes support for the use of Microsoft Windows Address Windowing Extensions (AWE) to address up to 32 GB of memory. With AWE, [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] can reserve memory that is not in use for other applications and the operating system. Each instance that uses this memory, however, must statically allocate the memory it needs. [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] can only use this AWE allocated memory for the data cache and not for executables, drivers, DLLs, and so forth. For more information, see:<br /><br /> -   Microsoft Knowledge Base article 274750, ["How to configure SQL Server to use more than 2 GB of physical memory"](http://go.microsoft.com/fwlink/?LinkId=153718) (http://go.microsoft.com/fwlink/?LinkId=153718).<br />-   [Using AWE](http://go.microsoft.com/fwlink/?LinkId=153720) (http://go.microsoft.com/fwlink/?LinkId=153720) in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation.<br />-   [Enabling AWE Memory for SQL Server](http://go.microsoft.com/fwlink/?LinkId=158273) (http://go.microsoft.com/fwlink/?LinkId=158273) in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation.|  
|Set the Minimum and Maximum Server memory to the same values on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s) that host the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.|The computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that host the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases should be dedicated to running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. When the computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that host the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases **are** dedicated to running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], we recommend that the 'min server memory' and 'max server memory' options on each [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance be set to specify the fixed amount of memory to allocate to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. In this case, you should set the 'min server memory' and 'max server memory' to the same value (equal to the maximum amount of physical memory that SQL Server will use). This will reduce overhead that would otherwise be used by [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] dynamically managing these values. Execute the following T-SQL commands on each computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] to specify the fixed amount of memory to allocate to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]:<br /><br /> sp_configure ‘Max Server memory (MB)’,(max size in MB)sp_configure ‘Min Server memory (MB)’,(min size in MB)<br /><br /> Before you set the amount of memory for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], determine the appropriate memory setting by subtracting the memory required for Windows Server from the total physical memory. This is the maximum amount of memory you can assign to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. **Note:**  If the computer(s) running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that host the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases also host the Enterprise Single Sign-On master secret as described in the topic [Clustering the Master Secret Server](../Topic/Clustering%20the%20Master%20Secret%20Server.md) then you may need to adjust this value to ensure that there is sufficient memory available to run the Enterprise Single Sign-On Service.|  
|Account for the size of BizTalk Tracking database|-   When determining the size of messages in the BizTalk Tracking (DTA) database, add the average size of the message context to the message size if it is significant compared to the message size.<br />-   To limit the size of messages in the BizTalk Tracking database, limit the number of properties that you promote.<br />-   If the orchestration debugger option is enabled, take into account that the status of each shape in the orchestration is saved in the BizTalk Tracking database.|  
  
<a name="BKMK_Maintain"></a>   
## Performing SQL Server Maintenance Procedures  
  
|Steps|Reference|  
|-----------|---------------|  
|Define auto-growth settings for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.|-   Database auto-growth should be set to a fixed number of megabytes instead of a percentage, especially for the MessageBox and Tracking databases. Depending on your BizTalk Server application and throughput, the MessageBox and Tracking databases can get quite large. If auto-growth is set to a percentage, then the auto-growth can be substantial as well.<br />-   Instant file initialization can greatly reduce the performance impact of a file growth operation.<br />-   Ideally, the size of files supporting the file groups should be pre-allocated, and if possible, set to a static size.<br /><br /> For more information, see [Defining Auto-Growth Settings for Databases](../Topic/Defining%20Auto-Growth%20Settings%20for%20Databases.md).|  
|Back up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases|-   We recommend running the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] backup job to prevent the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database transaction logs from growing in an unbounded fashion.<br />-   You should restore the entire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment on a regular basis, and you should carefully document the process.<br />-   We recommend that you archive old backup files.<br /><br /> For more information, see [Backing Up Databases](../Topic/Backing%20Up%20Databases.md).|  
|Monitor the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Agent jobs.|Monitor the health of these jobs, and ensure that they are running without errors. For more information, see [Monitoring SQL Server Agent Jobs](../Topic/Monitoring%20SQL%20Server%20Agent%20Jobs.md).|  
|Enable [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tracking and archiving|The “DTA Purge and Archive” SQL Agent job archives and purges old data from the BizTalk Tracking database, thus keeping it from growing out of control. This is essential for a healthy [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system. For more information, see [Purging and Archiving Tracking Data](../Topic/Purging%20and%20Archiving%20Tracking%20Data.md).|  
  
<a name="BKMK_Backup"></a>   
## Backing Up the BizTalk Server Databases  
  
|Steps|Reference|  
|-----------|---------------|  
|Verify that the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Agent job is configured.|-   See ["How to Configure the Backup BizTalk Server Job"](http://go.microsoft.com/fwlink/?LinkId=153813) (http://go.microsoft.com/fwlink/?LinkId=153813).<br />-   See [Backing Up Databases](../Topic/Backing%20Up%20Databases.md).|  
|Configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Agent job to delete backup files that are older than the number of days specified by the @DaysToKeep variable. If the backup files are not deleted they can grow unbounded over time which can fill up the disk(s) that contain the backup files and cause problems that relate to limited disk space.|See Microsoft Knowledge Base Article 982546, [The "Backup BizTalk Server" job fails when backup files accumulate over time in Microsoft BizTalk Dababase Server](http://go.microsoft.com/fwlink/?LinkId=202858) (http://go.microsoft.com/fwlink/?LinkId=202858).|  
|Verify that the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Agent job is enabled and running.|[Monitoring SQL Server Agent Jobs](../Topic/Monitoring%20SQL%20Server%20Agent%20Jobs.md)|  
  
<a name="BKMK_Disaster"></a>   
## Using SQL Server Log Shipping For Disaster Recovery  
  
|Steps|Reference|  
|-----------|---------------|  
|Verify that the disaster recovery servers have the capacity to handle production load.|See [Using BizTalk Server Log Shipping for Disaster Recovery](../Topic/Using%20BizTalk%20Server%20Log%20Shipping%20for%20Disaster%20Recovery.md)|  
|Ensure that the specifics of your disaster recovery routine are well documented.|See [Using BizTalk Server Log Shipping for Disaster Recovery](../Topic/Using%20BizTalk%20Server%20Log%20Shipping%20for%20Disaster%20Recovery.md)|  
|As part of regular testing, practice failover to the disaster recovery site, especially as new BizTalk applications are put in production.|See [Using BizTalk Server Log Shipping for Disaster Recovery](../Topic/Using%20BizTalk%20Server%20Log%20Shipping%20for%20Disaster%20Recovery.md)|  
  
<a name="BKMK_Jobs"></a>   
## Monitoring BizTalk Server SQL Agent Jobs  
  
|Steps|Reference|  
|-----------|---------------|  
|Verify that the SQL Server Agent service is running.|See [Monitoring SQL Server Agent Jobs](../Topic/Monitoring%20SQL%20Server%20Agent%20Jobs.md)|  
|Verify that the SQL Server Agent jobs installed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are enabled and running successfully.|See [Monitoring SQL Server Agent Jobs](../Topic/Monitoring%20SQL%20Server%20Agent%20Jobs.md)|  
|Verify that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SQL Agent jobs are completing in a timely manner.|See [Monitoring SQL Server Agent Jobs](../Topic/Monitoring%20SQL%20Server%20Agent%20Jobs.md)|  
  
<a name="BKMK_Purge"></a>   
## Purging and Archiving Tracking Data  
  
|Steps|Reference|  
|-----------|---------------|  
|Ensure that the SQL Agent job "DTA Purge and Archive" is properly configured, enabled, and successfully completing.|See ["How to Configure the DTA Purge and Archive Job"](http://go.microsoft.com/fwlink/?LinkId=153814) (http://go.microsoft.com/fwlink/?LinkId=153814).|  
|Ensure that the job is able to purge the tracking data as fast as the incoming tracking data is generated.|See ["Measuring Maximum Sustainable Tracking Throughput"](http://go.microsoft.com/fwlink/?LinkId=153815) (http://go.microsoft.com/fwlink/?LinkId=153815).|  
|Review the soft purge and hard purge parameters to ensure you are keeping data for the optimal length of time.|See ["Archiving and Purging the BizTalk Tracking Database"](http://go.microsoft.com/fwlink/?LinkId=153816) (http://go.microsoft.com/fwlink/?LinkId=153816).|  
|If you only need to purge the old data and do not need to archive it first, change the SQL Agent job to call the stored procedure "dtasp_PurgeTrackingDatabase."|See ["How to Purge Data from the BizTalk Tracking Database"](http://go.microsoft.com/fwlink/?LinkId=153817) (http://go.microsoft.com/fwlink/?LinkId=153817).|  
  
## In This Section  
  
-   [SQL Server Settings That Should Not Be Changed](../Topic/SQL%20Server%20Settings%20That%20Should%20Not%20Be%20Changed.md)  
  
-   [Monitoring and Reducing Database IO Contention](../Topic/Monitoring%20and%20Reducing%20Database%20IO%20Contention.md)  
  
-   [Reviewing and Testing SQL Server Cluster Configuration for Failover Scenarios](../Topic/Reviewing%20and%20Testing%20SQL%20Server%20Cluster%20Configuration%20for%20Failover%20Scenarios.md)  
  
-   [Defining Auto-Growth Settings for Databases](../Topic/Defining%20Auto-Growth%20Settings%20for%20Databases.md)  
  
-   [Backing Up Databases](../Topic/Backing%20Up%20Databases.md)  
  
-   [Using BizTalk Server Log Shipping for Disaster Recovery](../Topic/Using%20BizTalk%20Server%20Log%20Shipping%20for%20Disaster%20Recovery.md)  
  
-   [Monitoring SQL Server Agent Jobs](../Topic/Monitoring%20SQL%20Server%20Agent%20Jobs.md)  
  
-   [Purging and Archiving Tracking Data](../Topic/Purging%20and%20Archiving%20Tracking%20Data.md)