---
title: "How to Avoid Disk Contention2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37bdf6bd-cb34-4540-819e-908d83a22d40
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Avoid Disk Contention
BizTalk Server is designed as a persistent system. For high throughput scenarios, the MessageBox and BizTalk Tracking databases can experience severe contention. This contention can be aggravated by slow disks. If the disks are slow (greater than 15ms on average for Avg. Disk sec/Read or Avg. Disk sec/Write), it may cause SQL Server to hold onto locks longer (high Lock Wait Time and high Lock Timeouts). This, in turn, can cause the MessageBox tables (Spool and Application Queues) to grow, causing database bloat and throttling. This situation ultimately results in lower overall sustainable throughput.  
  
> [!NOTE]  
>  For information about identifying if a server has a disk bottleneck, see [Windows Performance Monitor](http://go.microsoft.com/fwlink/?LinkID=204007) (http://go.microsoft.com/fwlink/?LinkID=204007). Windows Performance Monitor is a Microsoft Management Console (MMC) snap-in that provides tools for analyzing system performance.  
  
 To avoid disk contention, do the following:  
  
|Steps|Reference|  
|-----------|---------------|  
|Use Raid10/0+1 disk configurations.|[Best Practices for Avoiding Bottlenecks](../technical-guides/best-practices-for-avoiding-bottlenecks.md)|  
|If possible, deploy the databases on a high-speed SAN. If multiple databases are sharing the same disks, we recommend configuring them on separate **dedicated** disks. In addition, we recommend separating the MDF and LDF files for the MessageBox database onto separate disks.|[Optimizing Filegroups for the Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md)|  
|Consider allocating multiple files for the TEMPDB database, as this will significantly reduce disk contention and spread the load across multiple data files.|[Pre-Configuration Database Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)|  
|Consider separating the MessageBox database onto a dedicated server that is separate from the BizTalk Tracking databases.|[Post-Configuration Database Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)|  
|Assign the MSDTC log file directory to a separate dedicated drive.|[Optimizing Operating System Performance](../technical-guides/optimizing-operating-system-performance.md)|  
|If there is contention on the local drive due to the PageFile or MSDTC log, try moving the PageFile and/or the MSDTC log to a separate drive.|[Best Practices for Avoiding Bottlenecks](../technical-guides/best-practices-for-avoiding-bottlenecks.md)|  
|Optimize the Tracking database for write operations.|[How to Identify Bottlenecks in the Tracking Database](../technical-guides/how-to-identify-bottlenecks-in-the-tracking-database.md)|  
|Optimize the MessageBox database for read and write operations.|[How to Identify Bottlenecks in the MessageBox Database1](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md)|  
|If a BizTalk host instance is saturating the CPU, consider separating sending, receiving, processing, and tracking functionality into multiple hosts. This configures the system so that the orchestration functionality runs on a separate dedicated server to improve overall system throughput.|[Optimizing BizTalk Server Performance](../technical-guides/optimizing-biztalk-server-performance.md)|  
|If multiple orchestrations are deployed, consider enlisting them in different dedicated orchestration hosts. This isolates the different orchestrations and prevents contention for shared resources either in the same physical address space or on the same server.|[Optimizing BizTalk Server Performance](../technical-guides/optimizing-biztalk-server-performance.md)|  
|Consider using Windows Performance Monitor to diagnose disk contention issues..|[Windows Performance Monitor](http://go.microsoft.com/fwlink/?LinkID=204007)|  
  
 For more information about disk performance analysis, see the following resources:  
  
- [Ruling Out Disk-Bound Problems](http://go.microsoft.com/fwlink/?LinkId=120947) (HYPERLINK "<http://go.microsoft.com/fwlink/?LinkId=120947>" \t "_blank"<http://go.microsoft.com/fwlink/?LinkId=120947>).  
  
- [SQL Server Predeployment I/O Best Practices](http://go.microsoft.com/fwlink/?LinkId=120948) (http://go.microsoft.com/fwlink/?LinkId=120948).  
  
- “I/O Bottlenecks” section of [Troubleshooting Performance Problems in SQL Server 2008](http://go.microsoft.com/fwlink/?LinkID=153586) (http://go.microsoft.com/fwlink/?LinkID=153586).  
  
## See Also  
 [Bottlenecks in the Database Tier](../technical-guides/bottlenecks-in-the-database-tier.md)