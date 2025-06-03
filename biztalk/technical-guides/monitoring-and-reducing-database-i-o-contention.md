---
description: "Learn more about: Monitoring and Reducing Database I/O Contention"
title: "Monitoring and Reducing Database I/O Contention"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Monitoring and Reducing Database I/O Contention
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance is often predicated upon [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance, which in turn is often predicated upon disk I/O performance. Therefore, you should monitor and performance-tune disk I/O on the computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.

## Monitoring Disk I/O
 Because of the database-intensive nature of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], disk I/O can easily become a bottleneck on the MessageBox and BizTalk Tracking databases; this is true even if disk I/O has not previously been a bottleneck for the database files in your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] environment. Thus, we recommend that you proactively measure disk I/O performance for the disks that house the data and transaction log files. For more information about monitoring disk I/O performance using System Monitor, see the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] article "Predeployment I/O Best Practices". If you are using a SAN, you may also need specific tools from the SAN hardware manufacturer to measure disk I/O performance.

## Separating the MessageBox and BizTalk Tracking (DTA) Databases and Log Files
 Since the MessageBox and BizTalk Tracking databases are the most active, we recommend that you place the data files and transaction log files for each of these on dedicated drives to reduce the likelihood of problems with disk I/O contention. For example, you would need four drives for the MessageBox and BizTalk Tracking database files; one drive for each of the following:

- MessageBox data files

- MessageBox transaction log files

- BizTalk Tracking data files

- BizTalk Tracking transaction log files

  Separating the MessageBox and BizTalk Tracking databases and separating the database files and transaction log files on different physical disks are considered best practices for reducing disk I/O contention. Try to spread the disk I/O across as many physical spindles as possible. For more information about avoiding disk contention, see [How to Avoid Disk Contention](https://go.microsoft.com/fwlink/?LinkId=158809) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Performance Optimization Guide.

  You should separate the files manually after configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 

## See Also
 [Using the Performance Analysis of Logs (PAL) Tool](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)
