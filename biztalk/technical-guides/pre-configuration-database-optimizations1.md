---
title: "Pre-Configuration Database Optimizations1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ebd0b32a-490d-4db2-a1fc-bf3bef93aeea
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Pre-Configuration Database Optimizations
BizTalk Server is an extremely database-intensive application that may require the creation of up to 13 separate databases in Microsoft SQL Server. Because of the critical role that SQL Server plays in any BizTalk Server environment, it is of paramount importance that SQL Server is configured/tuned for optimal performance. If SQL Server is not tuned to perform well, then the databases used by BizTalk Server will become a bottleneck and the overall performance of the BizTalk Server environment will suffer. This topic describes several SQL Server performance optimizations that should be followed before installing BizTalk Server and configuring the BizTalk Server databases.  
  
## Set NTFS File Allocation Unit  
 SQL Server stores its data in **Extents**, which are groups of eight 8K pages. Therefore, to optimize disk performance, set the NTFS Allocation Unit size to 64KB as described in the “Disk Configuration Best Practices” section of the SQL Server best practices article “Predeployment I/O Best Practices” available at [http://go.microsoft.com/fwlink/?LinkId=140818](http://go.microsoft.com/fwlink/?LinkId=140818). For more information about SQL Server pages and extents see the SQL Server Books Online topic [Understanding Pages and Extents](http://go.microsoft.com/fwlink/?LinkId=148939) ( HYPERLINK "<http://go.microsoft.com/fwlink/?LinkId=148939>" <http://go.microsoft.com/fwlink/?LinkId=148939>).  
  
## Database planning considerations  
 We recommend that you host your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases on fast storage (for example, fast SAN disks or fast SCSI disks). We recommend RAID 10 (1+0) instead of RAID 5 because raid 5 is slower at writing. Newer SAN disks have very large memory caches, so in these cases, the RAID selection is not as important. To increase performance, databases and their log files can reside on different physical disks.  
  
## Install the latest service pack and cumulative updates for SQL Server  
 Install the latest service packs and the latest cumulative updates for SQL Server 2005 and SQL Server 2008 as well as the latest .NET Framework service packs.  
  
## Install SQL Service Packs on both BizTalk Server and SQL Server  
 When installing service packs for SQL Server, also install the service pack on the BizTalk Server computer. BizTalk Server uses SQL Client components that are updated by the SQL Server service packs.  
  
## Consider implementing the SQL Server 2008 Data Collector and Management Data Warehouse  
 SQL Server 2008 accommodates the use of the new Data Collector and Management Data Warehouse to collect environment/database performance related data for test and trend analysis. The Data Collector persists all collected data to the specified Management Data Warehouse. While this is not a performance optimization, this will be useful for analysis of any performance issues.  
  
## Grant the account which is used for SQL Server the Windows Lock Pages In Memory privilege  
 Grant the Windows “Lock Pages in Memory” privilege to the SQL Server service account. This should be done to prevent the Windows operating system from paging out the buffer pool memory of the SQL Server process by locking memory that is allocated for the buffer pool in physical memory. For more information, see Microsoft Knowledge Base article 914483 “How to reduce paging of buffer pool memory in the 64-bit version of SQL Server 2005” at [http://go.microsoft.com/fwlink/?LinkId=148948](http://go.microsoft.com/fwlink/?LinkId=148948).  
  
## Grant the SE_MANAGE_VOLUME_NAME right to the SQL Server Service account  
 Ensure the account running the SQL Server service has the “Perform Volume Maintenance Tasks” Windows privilege or ensure it belongs to a security group which does. This will allow instant file initialization ensuring optimum performance if a database has to auto-grow.  
  
## Set Min and Max Server Memory  
 The computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that host the BizTalk Server databases should be dedicated to running SQL Server. We recommend that the “min server memory” and “max server memory” options on each SQL Server instance are set to specify the fixed amount of memory to allocate to SQL Server. In this case, you should set the “min server memory” and “max server memory” to the same value (equal to the maximum amount of physical memory that SQL Server will use). This will reduce overhead that would otherwise be used by SQL Server dynamically managing these values. Run the following T-SQL commands on each SQL Server computer to specify the fixed amount of memory to allocate to SQL Server:  
  
```  
sp_configure ‘Max Server memory (MB)’,(max size in MB)  
sp_configure ‘Min Server memory (MB)’,(min size in MB)  
```  
  
 Before you set the amount of memory for SQL Server, determine the appropriate memory setting by subtracting the memory required for Windows Server from the total physical memory. This is the maximum amount of memory you can assign to SQL Server.  
  
> [!NOTE]  
>  If the computer(s) running SQL Server that host the BizTalk Server databases also host the Enterprise Single Sign-On Master Secret Server, then you may need to adjust this value to ensure that there is sufficient memory available to run the Enterprise Single Sign-On Service. It is not an uncommon practice to run a clustered instance of the Enterprise Single Sign-On service on a SQL Server cluster to provide high availability for the Master Secret Server. For more information about clustering the Enterprise Single Sign-On Master Secret Server, see the topic “How to Cluster the Master Secret Server” in the BizTalk Serverdocumentation at [http://go.microsoft.com/fwlink/?LinkID=106874](http://go.microsoft.com/fwlink/?LinkID=106874).  
  
## Split the tempdb database into multiple data files of equal size on each SQL Server instance used by BizTalk Server  
 Ensuring that the data files used for the tempdb are of equal size is critical because the proportional fill algorithm used by [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is based on the size of the data files. This algorithm attempts to ensure that [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] fills each file in proportion to the free space left in that file so that they reach their maximum capacity at about the same time. If data files are created with unequal sizes, the proportional fill algorithm will use the largest file more for GAM allocations rather than spreading the allocations between all the files, thereby defeating the purpose of creating multiple data files. The number of data files for the tempdb database should be configured to be at least equal to the number of processors assigned for SQL Server.  
  
## Enable Trace Flag T1118 as a startup parameter for all instances of SQL Server  
 Implementing Trace Flag –T1118 helps reduce contention across the SQL Server instances by removing almost all single page allocations. For more information, see Microsoft Knowledge Base article 328551 "PRB: Concurrency enhancements for the tempdb database" at [http://go.microsoft.com/fwlink/?LinkID=103713](http://go.microsoft.com/fwlink/?LinkID=103713).  
  
## Do not change default SQL Server settings for max degree of parallelism, SQL Server statistics, or database index rebuilds and defragmentation  
 If a SQL Server instance will house BizTalk Server databases, then certain SQL Server settings should not be changed. Specifically, the SQL Server max degree of parallelism, the SQL Server statistics on the MessageBox database, and the settings for the database index rebuilds and defragmentation should not be modified. For more information, see the topic “SQL Server Settings That Should Not Be Changed” in the BizTalk Server Operations Guide at [http://go.microsoft.com/fwlink/?LinkId=114358](http://go.microsoft.com/fwlink/?LinkId=114358).