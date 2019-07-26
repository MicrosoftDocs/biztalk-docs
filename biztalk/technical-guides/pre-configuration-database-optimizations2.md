---
title: "Pre-Configuration Database Optimizations2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c525c3a-249c-4694-b287-a8c35a6aa524
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Pre-Configuration Database Optimizations
Because of the critical role that SQL Server plays in any BizTalk Server environment, it is of paramount importance that SQL Server be configured/tuned for optimal performance. If SQL Server is not tuned to perform well, then the databases used by BizTalk Server will become a bottleneck and the overall performance of the BizTalk Server environment will suffer. This topic describes several SQL Server performance optimizations that should be followed before installing BizTalk Server and configuring the BizTalk Server databases.  
  
## Set NTFS File Allocation Unit  
 SQL Server stores its data in **Extents**, which are collections of eight physically contiguous 8K pages, or 64 KB. Therefore, to optimize disk performance, set the NTFS Allocation Unit size to 64KB as described in the “Disk Configuration Best Practices” at  [Predeployment I/O Best Practices](https://msdn.microsoft.com/library/cc966412.aspx).  
  
## Considerations for the version and edition of SQL Server  
 Various versions and editions of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provide different features that can affect the performance of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. For example, under high-load conditions, the number of database locks that are available for the 32-bit version of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] might be exceeded, which is detrimental to the performance of the BizTalk solution. Consider housing your MessageBox database on a 64-bit version of SQL Server if you are experiencing "out of lock" errors in your test environment. The number of available locks is significantly higher on the 64-bit version of SQL Server.  
  
 Consider the following table when deciding on the database engine features that you will need for your BizTalk environment. For large scale, enterprise-level solutions that require clustering support, BizTalk Server log shipping support, or Analysis Services support, then you need SQL Server Enterprise Edition to host the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases.   

 For a complete list of the features supported by the SQL Server editions, see [SQL Server Editions and supported features](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016).
  
## Database planning considerations  
 We recommend that you host your SQL Server databases on fast storage (for example, fast SAN disks or fast SCSI disks). We recommend RAID 10 (1+0) instead of RAID 5 since raid 5 is slower at writing. Newer SAN disks have very large memory caches, so in these cases the raid selection is not as important. To increase performance, databases and their log files can reside on different physical disks.  
  
 Also consider tuning the host bus adapter (HBA) queue depth if using a storage area network (SAN). This can significantly impact I/O throughput and out-of-the box values can be insufficient for SQL Server. Testing is required to determine optimal value, although queue depth of 64 is generally accepted as a good starting point in the absence of any specific vendor recommendations  
  
## Install the latest service pack and cumulative updates for SQL Server  
 Install the latest service packs and the latest cumulative updates for SQL Server as well as the latest .NET Framework service packs.  
  
## Install SQL Service Packs and cumulative updates on both BizTalk Server and SQL Server  
 When installing service packs or cumulative updates for SQL Server, also install the service pack or cumulative update on the BizTalk Server computer. BizTalk Server uses SQL Client components that are updated by SQL Server service packs and cumulative updates.  
  
## Consider using a fast solid state drive (SSD) to house the SQL Server tembdb  
 Consider using one or more Solid State Disk (SSD) drives to house the TempDB. SSD drives offer significant performance advantages over traditional hard drives and are quickly dropping in price as they enter mainstream markets. Because TempDB performance is often a key factor for overall [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance, the added initial cost of the drives will often be quickly recouped by the overall increased [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance, especially when running enterprise applications for which [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance is critical.  
  
## Consider implementing the SQL Server 2008 R2 Data Collector and Management Data Warehouse  
 SQL Server 2008 R2 accommodates the use of the new Data Collector and Management Data Warehouse to collect environment/database performance related data for test and trend analysis. The Data Collector persists all collected data to the specified Management Data Warehouse. While this is not a performance optimization this will be useful for analysis of any performance issues.  
  
## Grant the account which is used for SQL Server the Windows Lock Pages In Memory privilege  
 Grant the Windows Lock Pages in Memory privilege to the SQL Server service account. This should be done to prevent the Windows operating system from paging out the buffer pool memory of the SQL Server process by locking memory that is allocated for the buffer pool in physical memory.  
  
 In our lab environment, the Windows policy **Lock Pages in Memory** option was enabled by default. See [Enable the Lock Pages in Memory Option](https://docs.microsoft.com/sql/database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows).  
  
> [!IMPORTANT]  
>  Certain limitations apply when granting the SQL Server service account the Windows Lock Pages in Memory privilege. See the following: 
>   
> - [Buffer Pool Extension](https://docs.microsoft.com/sql/database-engine/configure-windows/buffer-pool-extension)  
> - [Enable the Lock Pages in Memory Option](https://docs.microsoft.com/sql/database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows)  
  
## Grant the SE_MANAGE_VOLUME_NAME right to the SQL Server Service Account  
 Ensure the account running the SQL Server service has the ‘Perform Volume Maintenance Tasks’ Windows privilege or ensure it belongs to a group that does. This will allow instant file Initialization ensuring optimum performance if a database has to Auto-grow.  
  
## Set Min and Max Server Memory  
 The computers running SQL Server that host the BizTalk Server databases should be dedicated to running SQL Server. When the computers running SQL Server that host the BizTalk Server databases are dedicated to running SQL Server, we recommend that the 'min server memory' and 'max server memory' options on each SQL Server instance are set to specify the fixed amount of memory to allocate to SQL Server. In this case, you should set the “min server memory” and “max server memory” to the same value (equal to the maximum amount of physical memory that SQL Server will use). This will reduce overhead that would otherwise be used by SQL Server dynamically managing these values. Run the following T-SQL commands on each computer running SQL Server to specify the fixed amount of memory to allocate to SQL Server:  
  
```  
sp_configure ‘Max Server memory (MB)’,(max size in MB)  
sp_configure ‘Min Server memory (MB)’,(min size in MB)  
```  
  
 Before you set the amount of memory for SQL Server, determine the appropriate memory setting by subtracting the memory required for Windows Server from the total physical memory. This is the maximum amount of memory you can assign to SQL Server.  
  
> [!NOTE]  
>  If the computers running SQL Server that host the BizTalk Server databases also host the Enterprise Single Sign-On Master Secret Server, then you may need to adjust this value to ensure that there is sufficient memory available to run the Enterprise Single Sign-On Service. It is not an uncommon practice to run a clustered instance of the Enterprise Single Sign-On service on a SQL Server cluster to provide high availability for the Master Secret Server. See [Clustering the Master Secret Server](../technical-guides/clustering-the-master-secret-server.md)  
  
## Split the tempdb database into multiple data files of equal size on each SQL Server instance used by BizTalk Server  
 Ensuring that the data files used for the tempdb are of equal size is critical because the proportional fill algorithm used by SQL Server is based on the size of the data files. If data files are created with unequal sizes, the proportional fill algorithm will use the largest file more for GAM allocations rather than spreading the allocations between all the files, thereby defeating the purpose of creating multiple data files. The optimal number of tempdb data files depends on the degree of latch contention seen in tempdb. As a general rule of thumb, the number of data files should be equal to number of processor cores/CPUs where number of CPUs is 8 or less. For servers with more than 8 CPUs, create data files for half the number of CPUs (again, only you have latch contention).  
  
 In our lab environment, we used the script below to create 8 TempDB data files each of which had a file size of 1024 MB with 100 MB growth and a log file of 512 MB with 100 MB growth. The data files are moved to drive H: and log file are moved to drive I:.  
  
> [!IMPORTANT]  
>  This script is provided “as is,” is intended for demo or educational purposes only, and is to be used at your own risk. Use of this script is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this script.  
  
```  
--<<<<<<<<<<----------------------------------------------------------------->>>>>>>>>>--  
-- Use of included script samples are subject to the terms specified at   
-- http://www.microsoft.com/info/cpyright.htm  
--<<<<<<<<<<----------------------------------------------------------------->>>>>>>>>>--  
--***Instructions***  
-- 1. If running the script from a remote server, change the context in SSMS to target instance  
-- 2. Enable SQLCMD mode (add & click toolbar button or toggle by clicking Query > SQLCMD Mode)  
-- 3. Commence execution of scripts (recommend running statements discretely to more easily remedy potential problems)  
-- 4. Examine servername & temp configuration  
-- 5. If necessary, 1) Replace instance name in path to reflect target instance *all throughout script*  
      --            2) Modify root drives to reflect drives designated for data & log (folder creation *and* ALTER DB statements)  
-- 6. Resume script execution  
-- 7. If necessary, create new folders  
-- 8. Modify/Add data & log files   
-- 9. Recycle SQL service using sqlservermanager10.msc  
--10. Examine results & if appropriate, delete original tempdb data log files   
 --(if they were "moved", the original files aren't automatically deleted)  
  
--<<<<<<<<<<----------------------------------------------------------------->>>>>>>>>>--  
--1. If running the script from a remote server, change the context in SSMS to target instance  
--2. Enable SQLCMD mode (add & click toolbar button or toggle by clicking Query > SQLCMD Mode)  
--3. Commence execution of scripts (recommend running statements discretely to more easily remedy potential problems)  
--4. Examine servername & temp configuration  
SELECT @@SERVERNAME  
EXEC dbo.sp_helpdb tempdb  
--tempdev   1   C:\tempdb.mdf   PRIMARY  8192 KB  Unlimited  10%  data only  
--templog   2   C:\templog.ldf  NULL      512 KB  Unlimited  10%  log only  
GO  
--5. If necessary, 1) Replace instance name in path to reflect target instance *all throughout script*  
     --            2) Modify root drives to reflect drives designated for data & log (folder creation *and* ALTER DB statements)  
--6. Resume script execution  
--7. If necessary, create new folders  
--!!md H:\MSSQL10.<instance>  
--!!md H:\MSSQL10.<instance>\MSSQL  
--!!md H:\MSSQL10.<instance>\MSSQL\DATA  
GO  
-- 8. Modify/Add data & log files   
 --note: even if the out-of-box mdf is already where it needs to be,   
   --the first command is necessary to modify size & filegrowth  
ALTER DATABASE tempdb MODIFY FILE (NAME = tempdev  , FILENAME = 'H:\tempdb.mdf'   , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat2 , FILENAME = 'H:\tempdat2.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat3 , FILENAME = 'H:\tempdat3.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat4 , FILENAME = 'H:\tempdat4.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat5 , FILENAME = 'H:\tempdat5.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat6 , FILENAME = 'H:\tempdat6.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat7 , FILENAME = 'H:\tempdat7.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat8 , FILENAME = 'H:\tempdat8.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
GO  
ALTER DATABASE tempdb MODIFY FILE (NAME = templog , FILENAME = 'I:\templog.ldf', SIZE =  512MB , FILEGROWTH = 100MB)  
GO  
--8b. Modify log file:  modify drive & instance name to reflect designated destination for tempdb log   
--!!md I:\MSSQL10.<instance>  
--!!md I:\MSSQL10.<instance>\MSSQL  
--!!md I:\MSSQL10.<instance>\MSSQL\DATA  
GO  
-- 9. Recycle SQL service in SQL Server Services node of sqlservermanager10.msc  
    --note, if running script from a UNC share, SSMS will report an error,   
      --but SQL Server Configuration Manager will open if its location is in %path%  
!!sqlservermanager10.msc  
  
--10. Examine results & if appropriate, delete original tempdb data log files   
 --(if they were "moved", the original files aren't automatically deleted)  
EXEC dbo.sp_helpdb tempdb  
--!!del C:\tempdb.mdf     
--!!del C:\templog.ldf  
GO  
  
```  
  
 Use the SQL Server 2008 Activity Monitor or the SQL Server 2005 Performance Dashboard Reports described in [Monitoring SQL Server Performance](../technical-guides/monitoring-sql-server-performance.md) to identify problems with latch contention.  
  
## Manually set SQL Server Process Affinity  
 The Process Affinity option can provide performance enhancements in high-end, enterprise-level SQL Server environments that are running on non-NUMA computers with 16 or more CPUs. This is especially true in high-throughput BizTalk environments where you have contention on shared tables in the MessageBox database. Because the SQL Server computers that were used in our lab environment were not NUMA-enabled and had 16 cores, to optimize performance, we used the commands below to set process affinity:  
  
 **To manually set the SQL Server Process Affinity from 0 to 15**  
  
```  
ALTER SERVER CONFIGURATION  
SET PROCESS AFFINITY CPU = 0 to 15  
```  
  
 For more information, see [ALTER SERVER CONFIGURATION (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-server-configuration-transact-sql).
  
## Configure MSDTC  
 To facilitate transactions between SQL Server and BizTalk Server, you must enable Microsoft Distributed Transaction Coordinator (MS DTC). To configure MSDTC on SQL Server, see the topic [General Guidelines for Improving Operating System Performance](../technical-guides/general-guidelines-for-improving-operating-system-performance.md).  
  
## Enable Trace Flag T1118 as a startup parameter for all instances of SQL Server  
 Implementing Trace Flag –T1118 helps reduce contention across the SQL Server instances by removing almost all single page allocations. For more information, see [KB 328551: PRB: Concurrency enhancements for the tempdb database](https://support.microsoft.com/help/328551/concurrency-enhancements-for-the-tempdb-database).
  
## Do not change default SQL Server settings for max degree of parallelism, SQL Server statistics, or database index rebuilds and defragmentation  
 If a SQL Server instance will house BizTalk Server databases, then there are certain SQL Server settings that should not be changed. Specifically, the SQL Server max degree of parallelism, the SQL Server statistics on the MessageBox database, and the settings for the database index rebuilds and defragmentation should not be modified. See [SQL Server Settings That Should Not Be Changed](../technical-guides/sql-server-settings-that-should-not-be-changed.md).
  
## See Also  
 [Optimizing Database Performance](../technical-guides/optimizing-database-performance.md)
