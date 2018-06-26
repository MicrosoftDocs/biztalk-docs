---
title: "Guidelines for Avoiding Bottlenecks | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 640ab399-b22d-4f71-b41d-ea8d778e064a
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Guidelines for Avoiding Bottlenecks
While the default settings in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provide optimal performance for many hardware and software configurations, in some scenarios it may be beneficial to modify the settings or deployment configuration. When configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consider the following performance guidelines:  

-   To prevent resource contention, isolate receiving, orchestration, and sending onto separate hosts. To further minimize contention, isolate the tracking service from other hosts.  

-   If CPU processing on the BizTalk Server is the bottleneck, scale up BizTalk Server by including additional CPUs or upgrading to faster CPUs.  

## SQL Server Guidelines  
 Consider the following performance guidelines when configuring Microsoft SQL Server with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  

- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases should be configured to run on a dedicated SQL Server instance whenever possible. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is a databases intensive application, so separation of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer(s) and the SQL Server computer(s) that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases will improve performance and should be considered a best practice in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  

- Whenever possible, use a fast disk subsystem with SQL Server. Use a redundant array of independent disks type 5 (RAID5/10) or a storage area network (SAN) with backup power supply.  

- Use the SQL Server disaster recovery process to back up your databases regularly. The BizTalk Server service automatically recovers from SQL Server connection malfunctions.  

- Isolate each message box onto a separate server from the BizTalk Tracking database (BizTalkDTADb). For smaller deployments if CPU resources are available, isolating the message box onto a separate physical disk from the BizTalkDTADb database might be sufficient.  

- The primary MessageBox could be the bottleneck due to CPU processor saturation or latency from disk operations (average disk queue length). If CPU processing is the bottleneck, add CPU processors to the primary message box. If not try disabling publishing on the Master MessageBox, this way the Master MessageBox can more efficiently handle routing of messages to the other MessageBox databases.  

- If disk operations are the bottleneck, move the BizTalkDTADb database to a dedicated SQL Server computer and/or dedicated disk. If CPU processing and disk operations on the primary message box are not the bottleneck, you can create new MessageBox databases on the same SQL Server computer to leverage your existing hardware.  

- Follow SQL Server best practices to isolate the transaction and data log files for the MessageBox and BizTalkDTADb databases onto separate physical disks.  

- Allocate sufficient storage space for the data and log files; otherwise SQL Server will automatically consume all of the available space on the disks that the log files are kept. Initial size of the log files will depend on the specific requirements in your particular scenario. Estimate the average file size in your deployment based on testing results, and expand the storage space before implementing your solution.  

- Allocate sufficient storage space for high-disk-usage databases, such as the MessageBox, Tracking, and Business Activity Monitoring (BAM) databases. If your solution uses the BizTalk Framework messaging protocol, allocate sufficient storage space for the BizTalk Configuration database (BizTalkMgmtDb).  

- Depending on business needs [data retention periods] and the volume of data processed in your particular scenario, configure the Archive/Purge jobs on the Tracking database such that the BizTalkDTADb database does not grow too large. The growth of this database can degrade performance (especially when one BizTalkDTADb database supports multiple message boxes) because reaching the full capacity of the database imposes a limit on the rate of data insertion.  

- Scale up the servers hosting the MessageBox and BizTalkDTADb databases if they are the bottleneck. You can scale up the hardware by adding CPUs, adding memory, upgrading to faster CPUs and using high-speed dedicated disks.
