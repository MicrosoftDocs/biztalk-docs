---
description: "Learn more about: Checklist: Performing Weekly Maintenance Checks"
title: "Checklist: Performing Weekly Maintenance Checks | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b13e43ba-4bac-4d4b-aaf8-46d60c0561bf
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Checklist: Performing Weekly Maintenance Checks

This topic describes the steps involved in performing weekly maintenance checks of the reliability, administration, security, and performance of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.

- Ensure that each host has an instance running on at least two physical BizTalk servers (reliability check). For more information, go to [High Availability for BizTalk Hosts](high-availability-for-biztalk-hosts.md).

- Ensure that each receive location is redundant (reliability check). For more information, go to [Scaling Out Receiving Hosts](scaling-out-receiving-hosts.md).

- Ensure that the SQL Server Agent service is running on the SQL server (administration check). For more information, go to:

  - [How to: Start SQL Server Agent](/sql/ssms/agent/start-stop-or-pause-the-sql-server-agent-service)
  - [SQL Server Agent](/sql/ssms/agent/sql-server-agent)

- Ensure that all SQL Server jobs related to BizTalk Server are working properly (administration check).  If the SQL Server Agent jobs are not running, system performance will degrade over time. For more information, go to:

  - [Monitoring SQL Server Agent Jobs](monitoring-sql-server-agent-jobs.md)
  - [Database Structure and Jobs](../core/database-structure-and-jobs.md)

- Ensure that the SQL Server jobs responsible for backing up BizTalk Server databases are running normally (administration check). For more information, go to:

  - [How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md)
  - [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md)

- Ensure that the latest security updates are installed (security check). For more information, go to the [Windows Update: FAQ](https://support.microsoft.com/windows/windows-update-faq-8a903416-6f45-0718-f5c7-375e92dddeb2).

- Analyze weekly performance monitoring logs against baseline and thresholds (performance check). For more information, go to:

  - [Using the Performance Analysis of Logs (PAL) Tool](using-the-performance-analysis-of-logs-pal-tool.md)
  - [Troubleshooting Performance Issues](troubleshooting-performance-issues3.md)

- Ensure that the system is not experiencing frequent auto-growth of BizTalk Server databases (performance check). For more information, go to:

  - [Defining Auto-Growth Settings for Databases](defining-auto-growth-settings-for-databases.md)
  - [Tracking Database Sizing Guidelines](../core/tracking-database-sizing-guidelines.md)
  - [Identifying Bottlenecks in the Database Tier](bottlenecks-in-the-database-tier.md)
  - [Database File Initialization](/sql/relational-databases/databases/database-instant-file-initialization)
  - [Performing SQL Server Maintenance Procedures](checklist-configuring-sql-server.md)

- Run SQL Server Profiler during high load to check for long response times and high resource usage (performance check). For more information, go to [Using SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions).

- Ensure that message batching for all adapters is appropriate for resource consumption or latency (performance check). For more information, go to:

  - [Configuring Batching to Improve Adapter Performance](configuring-batching-to-improve-adapter-performance.md)
  - [How to Design a Performant Adapter](../core/how-to-design-a-performant-adapter.md)

- Ensure that the large message threshold is appropriate for resource consumption (performance check). For more information, go to [How BizTalk Server Processes Large Messages](../core/how-biztalk-server-processes-large-messages.md).

- Archive backup files and specify appropriate computers for backup.

  To avoid potential data loss, you should specify a computer for your backup that is different from the computer with the original data, and for \<destination path\> you should specify a computer to store the database logs that is different from the computer with the original database logs.

  For more information about best practices for backup, see [Best Practices for Backing Up and Restoring Databases](../core/best-practices-for-backing-up-and-restoring-databases.md).

## See Also

[Routine Monitoring Tasks](../technical-guides/routine-monitoring-tasks.md)
