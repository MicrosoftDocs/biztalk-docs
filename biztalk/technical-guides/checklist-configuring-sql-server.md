---
title: "Checklist: Configuring SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/29/2017"
ms.prod: "biztalk-server"
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
Steps to follow when preparing SQL Server for use in a BizTalk Server production environment.    
 
<a name="BKMK_Config"></a>   
## Configuring SQL Server  
  
|Steps|Reference|  
|-----------|---------------|  
|Monitor and reduce BizTalk Server database files disk I/O contention.|-   We recommend that you proactively monitor the disk I/O usage for the disks that house the data and transaction log files.<br />-   We recommend that the data files and transaction log files for each of these be placed on dedicated drives to reduce the likelihood of disk I/O contention becoming a problem.<br />-   You can reduce disk I/O contention by separating the MessageBox and Tracking (DTA) databases, and by separating the database files and transaction log files on different physical disks.<br /><br /> For more information, see [Monitoring and Reducing Database IO Contention](monitoring-and-reducing-database-i-o-contention.md)|  
|Ensure SQL Server is configured on properly-aligned disk partitions|Properly aligned disk partitions could result in significant decrease in latency thereby improving the SQL Server performance, which in turn enhances BizTalk Server performance. On the contrary, nonaligned disk partitions can negatively affect I/O performance, thereby degrading the SQL Server and BizTalk Server performance.<br /><br /> For more information about how properly aligned disk partitions can positively affect performance, see [Disk Partition Alignment Best Practices for SQL Server](http://go.microsoft.com/fwlink/?LinkId=154073).|  
|Keep the events you monitor with the SQL Server Profiler|Use SQL Server Profiler to monitor only the events in which you are interested. If traces become too large, you can filter them based on the information you want, so that only a subset of the event data is collected. Monitoring too many events adds overhead to the server and the monitoring process, and can cause the trace file or trace table to grow very large, especially when the monitoring process takes place over a long period of time.|  
|Monitor and reduce DTC log file disk I/O contention.|[Monitoring and Reducing DTC Log File Disk IO Contention](monitoring-and-reducing-dtc-log-file-disk-i-o-contention.md)|  
|Provide high availability for the SQL Server databases.|[Planning for Database Availability](planning-for-database-availability.md)|  
|Review active/active SQL Server cluster configuration for failover scenarios.|[Reviewing and Testing SQL Server Cluster Configuration for Failover Scenarios](reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)|  
|Use default configuration settings for:<br /><br /> -   Max Degree of Parallelism (MDOP).<br />-   SQL Server statistics on the BizTalk Server MessageBox database.<br />-   SQL Server database index rebuilds and defragmentation.|[SQL Server Settings That Should Not Be Changed](sql-server-settings-that-should-not-be-changed.md)|  
|Enable trace flag 1118 (TF1118) as a startup parameter for all instances of SQL Server.|Implementing TF1118 helps reduce contention across the SQL Server instances by removing almost all single page allocations. For more information see Microsoft Knowledge Base article [Concurrency enhancements for the tempdb database](https://support.microsoft.com/en-us/help/328551/concurrency-enhancements-for-the-tempdb-database). <br/><br/>**Note:**  For more information about TF1118 see [Misconceptions around TF1118](https://www.sqlskills.com/blogs/paul/misconceptions-around-tf-1118/). Note that the content at this link is not owned by Microsoft and Microsoft does not guarantee the accuracy of the content.|  
|Split the tempdb database into multiple data files of equal size on each SQL Server instance used by BizTalk Server.|Ensure that the data files used for the tempdb are of equal size. This is critical because the proportional fill algorithm used by SQL Server is based on the size of the data files. If data files are created with unequal sizes, the proportional fill algorithm will use the largest file more for Global Allocation Map (GAM) allocations rather than spreading the allocations between all the files, thereby defeating the purpose of creating multiple data files. As a general guideline, create one data file for each CPU on the server and then adjust the number of files up or down as necessary. Note that a dual-core CPU is considered to be two CPUs. In any event, the number of data files must not be greater than 8 no matter how many additional cores are available on the computer. For more information about tempdb files, see [Optimizing tempdb Performance](https://docs.microsoft.com/sql/relational-databases/databases/tempdb-database).|  
|Set the Minimum and Maximum Server memory to the same values on the SQL Server instance(s) that host the BizTalk Server databases.|The computers running SQL Server that host the BizTalk Server databases should be dedicated to running SQL Server. When the computers running SQL Server that host the BizTalk Server databases **are** dedicated to running SQL Server, we recommend that the 'min server memory' and 'max server memory' options on each SQL Server instance be set to specify the fixed amount of memory to allocate to SQL Server. In this case, you should set the 'min server memory' and 'max server memory' to the same value (equal to the maximum amount of physical memory that SQL Server will use). This will reduce overhead that would otherwise be used by SQL Server dynamically managing these values. Execute the following T-SQL commands on each computer running SQL Server to specify the fixed amount of memory to allocate to SQL Server:<br /><br /> sp_configure ‘Max Server memory (MB)’,(max size in MB)sp_configure ‘Min Server memory (MB)’,(min size in MB)<br /><br /> Before you set the amount of memory for SQL Server, determine the appropriate memory setting by subtracting the memory required for Windows Server from the total physical memory. This is the maximum amount of memory you can assign to SQL Server. **Note:**  If the computer(s) running SQL Server that host the BizTalk Server databases also host the Enterprise Single Sign-On master secret as described in the topic [Clustering the Master Secret Server](clustering-the-master-secret-server.md) then you may need to adjust this value to ensure that there is sufficient memory available to run the Enterprise Single Sign-On Service.|  
|Account for the size of BizTalk Tracking database|-   When determining the size of messages in the BizTalk Tracking (DTA) database, add the average size of the message context to the message size if it is significant compared to the message size.<br />-   To limit the size of messages in the BizTalk Tracking database, limit the number of properties that you promote.<br />-   If the orchestration debugger option is enabled, take into account that the status of each shape in the orchestration is saved in the BizTalk Tracking database.|  
  
<a name="BKMK_Maintain"></a>   
## Performing SQL Server Maintenance Procedures  
  
|Steps|Reference|  
|-----------|---------------|  
|Define auto-growth settings for the BizTalk Server databases.|-   Database auto-growth should be set to a fixed number of megabytes instead of a percentage, especially for the MessageBox and Tracking databases. Depending on your BizTalk Server application and throughput, the MessageBox and Tracking databases can get quite large. If auto-growth is set to a percentage, then the auto-growth can be substantial as well.<br />-   Instant file initialization can greatly reduce the performance impact of a file growth operation.<br />-   Ideally, the size of files supporting the file groups should be pre-allocated, and if possible, set to a static size.<br /><br /> For more information, see [Defining Auto-Growth Settings for Databases](defining-auto-growth-settings-for-databases.md).|  
|Back up the BizTalk Server databases|-   We recommend running the BizTalk Server backup job to prevent the BizTalk Server database transaction logs from growing in an unbounded fashion.<br />-   You should restore the entire BizTalk Server environment on a regular basis, and you should carefully document the process.<br />-   We recommend that you archive old backup files.<br /><br /> For more information, see [Backing Up Databases](backing-up-databases.md).|  
|Monitor the BizTalk Server SQL Agent jobs.|Monitor the health of these jobs, and ensure that they are running without errors. For more information, see [Monitoring SQL Server Agent Jobs](monitoring-sql-server-agent-jobs.md).|  
|Enable BizTalk Server tracking and archiving|The “DTA Purge and Archive” SQL Agent job archives and purges old data from the BizTalk Tracking database, thus keeping it from growing out of control. This is essential for a healthy BizTalk Server system. For more information, see [Purging and Archiving Tracking Data](purging-and-archiving-tracking-data.md).|  
  
<a name="BKMK_Backup"></a>   
## Backing Up the BizTalk Server Databases  
  
|Steps|Reference|  
|-----------|---------------|  
|Verify that the Backup BizTalk Server SQL Agent job is configured.|See [Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|Configure the Backup BizTalk Server SQL Agent job to delete backup files that are older than the number of days specified by the @DaysToKeep variable. If the backup files are not deleted they can grow unbounded over time which can fill up the disk(s) that contain the backup files and cause problems that relate to limited disk space.|See [Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|Verify that the Backup BizTalk Server SQL Agent job is enabled and running.|[Monitoring SQL Server Agent Jobs](monitoring-sql-server-agent-jobs.md)|  
  
<a name="BKMK_Disaster"></a>   
## Using SQL Server Log Shipping For Disaster Recovery  
  
|Steps|Reference|  
|-----------|---------------|  
|Verify that the disaster recovery servers have the capacity to handle production load.|See [Using BizTalk Server Log Shipping for Disaster Recovery](using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
|Ensure that the specifics of your disaster recovery routine are well documented.|See [Using BizTalk Server Log Shipping for Disaster Recovery](using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
|As part of regular testing, practice failover to the disaster recovery site, especially as new BizTalk applications are put in production.|See [Using BizTalk Server Log Shipping for Disaster Recovery](using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
  
<a name="BKMK_Jobs"></a>   
## Monitoring BizTalk Server SQL Agent Jobs  
  
|Steps|Reference|  
|-----------|---------------|  
|Verify that the SQL Server Agent service is running.|See [Monitoring SQL Server Agent Jobs](monitoring-sql-server-agent-jobs.md)|  
|Verify that the SQL Server Agent jobs installed by BizTalk Server are enabled and running successfully.|See [Monitoring SQL Server Agent Jobs](monitoring-sql-server-agent-jobs.md)|  
|Verify that the BizTalk Server SQL Agent jobs are completing in a timely manner.|See [Monitoring SQL Server Agent Jobs](monitoring-sql-server-agent-jobs.md)|  
  
<a name="BKMK_Purge"></a>   
## Purging and Archiving Tracking Data  
  
|Steps|Reference|  
|-----------|---------------|  
|Ensure that the SQL Agent job "DTA Purge and Archive" is properly configured, enabled, and successfully completing.|See [Configure the DTA Purge and Archive Job](../core/how-to-configure-the-dta-purge-and-archive-job.md).|  
|Ensure that the job is able to purge the tracking data as fast as the incoming tracking data is generated.|See [Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md)|  
|Review the soft purge and hard purge parameters to ensure you are keeping data for the optimal length of time.|See [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md).|  
|If you only need to purge the old data and do not need to archive it first, change the SQL Agent job to call the stored procedure "dtasp_PurgeTrackingDatabase."|See [Purge Data from the BizTalk Tracking Database](../core/how-to-purge-data-from-the-biztalk-tracking-database.md).|  
  
## Next
  
-   [SQL Server Settings That Should Not Be Changed](sql-server-settings-that-should-not-be-changed.md)  
  
-   [Monitoring and Reducing Database IO Contention](monitoring-and-reducing-database-i-o-contention.md)  
  
-   [Reviewing and Testing SQL Server Cluster Configuration for Failover Scenarios](reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)  
  
-   [Defining Auto-Growth Settings for Databases](defining-auto-growth-settings-for-databases.md)  
  
-   [Backing Up Databases](backing-up-databases.md)  
  
-   [Using BizTalk Server Log Shipping for Disaster Recovery](using-biztalk-server-log-shipping-for-disaster-recovery.md)  
  
-   [Monitoring SQL Server Agent Jobs](monitoring-sql-server-agent-jobs.md)  
  
-   [Purging and Archiving Tracking Data](purging-and-archiving-tracking-data.md)