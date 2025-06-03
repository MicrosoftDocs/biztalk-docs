---
description: "Learn more about: Best Practices for Avoiding Bottlenecks"
title: "Best Practices for Avoiding Bottlenecks"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: best-practice
---
# Best Practices for Avoiding Bottlenecks
While the default settings in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provide optimal performance for many hardware and software configurations, in some scenarios it may be beneficial to modify the settings or deployment configuration. When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consider the following performance guidelines:  
  
-   To prevent resource contention, isolate receiving, orchestration, and sending on separate hosts. To further minimize contention, isolate the tracking service from other hosts.  
  
-   If CPU processing on the computer running BizTalk Server is the bottleneck, scale up the computer running BizTalk Server by including additional CPUs or upgrading to faster CPUs.  
  
## SQL Server Guidelines  
 Consider the following performance guidelines when configuring Microsoft SQL Server with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
-   Whenever possible, use a fast disk subsystem with SQL Server. Use a redundant array of independent disks type 10 (RAID10/0+1) or a storage area network (SAN) with backup power supply.  
  
-   Isolate each MessageBox database on a separate server from the BizTalk Tracking database (BizTalkDTADb). For smaller deployments if CPU resources are available, it might be sufficient to isolate the MessageBox database on a separate physical disk from the BizTalk Tracking database.  
  
-   The primary MessageBox database could be the bottleneck due to CPU processor saturation or latency from disk operations (average disk queue length). If CPU processing is the bottleneck, add CPU processors to the primary MessageBox. If not, try to disable publishing on the master MessageBox database. This way the master MessageBox database can more efficiently handle routing of messages to the other MessageBox databases. The option to disable publishing is valid when you are using multiple MessageBox databases.  
  
-   If disk operations are the bottleneck, move the BizTalk Tracking database to a dedicated SQL Server computer and/or dedicated disk. If CPU processing and disk operations on the primary MessageBox database are not the bottleneck, you can create new MessageBox databases on the same SQL Server computer to leverage your existing hardware.  
  
-   Follow recommendations in [Optimizing Filegroups for the Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md)to isolate the transaction and data log files for the MessageBox and BizTalk Tracking databases onto separate physical disks.  
  
-   Allocate sufficient storage space for the data and log files. Otherwise SQL Server will automatically consume all of the available space on the disks where the log files are kept. The initial size of the log files depends on the specific requirements in your scenario. Estimate the average file size in your deployment based on testing results, and expand the storage space before implementing your solution.  
  
-   Allocate sufficient storage space for high-disk-use databases, such as the MessageBox, Health and Activity Tracking (HAT), and Business Activity Monitoring (BAM). If your solution uses the BizTalk Framework messaging protocol, allocate sufficient storage space for the BizTalk Configuration database (BizTalkMgmtDb).  
  
-   Depending on business needs, such as data retention periods, and the volume of data processed in your scenario, configure the "DTA Archive and Purge" SQL Server Agent job on the HAT-Tracking database such that the BizTalk Tracking database does not grow too large. The growth of this database can degrade performance because reaching the full capacity of the database imposes a limit on the rate of data insertion. This is especially true when one BizTalk Tracking database supports multiple MessageBox databases.  
  
-   Scale up the servers hosting the MessageBox and BizTalk Tracking databases if they are the bottleneck. You can scale up the hardware by adding CPUs, adding memory, upgrading to faster CPUs, and using high-speed dedicated disks.  
  
-   Splitting the TempDB files across multiple files may resolve performance issues related to I/O operations. As a general guideline, create one file data file per processor and use the same size for all files created.  
  
-   Change the database auto-grow settings to a fixed value such as 100-150MB. By default the database growth is configured to 10%, which can lead to delays when growing larger databases.  
  
-   SQL Server memory should be set to a fixed value by setting both Min Server Memory and Max Server Memory to the same value. In general, allocate 75% of physical memory to SQL Server and leave 25% for the rest of the operating system and any applications. If this is a dedicated SQL Server, you can decrease the amount reserved for the operating system to a minimum of 1GB.  
  
## See Also  
 [Finding and Eliminating Bottlenecks](../technical-guides/finding-and-eliminating-bottlenecks.md)
