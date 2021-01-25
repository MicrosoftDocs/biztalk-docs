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

|Steps|Reference|
|-----------|---------------|
|Ensure that each host has an instance running on at least two physical BizTalk servers (reliability check).|[High Availability for BizTalk Hosts](../technical-guides/high-availability-for-biztalk-hosts.md)|
|Ensure that each receive location is redundant (reliability check).|[Scaling Out Receiving Hosts](../technical-guides/scaling-out-receiving-hosts.md)|
|Ensure that the SQL Server Agent service is running on the SQL server (administration check).|-   [How to: Start SQL Server Agent](https://go.microsoft.com/fwlink/p/?LinkId=154672) (https://go.microsoft.com/fwlink/p/?LinkId=154672).<br />-   [SQL Server Agent](https://go.microsoft.com/fwlink/p/?LinkId=106728) (https://go.microsoft.com/fwlink/p/?LinkId=106728).|
|Ensure that all SQL Server jobs related to BizTalk Server are working properly (administration check).|[Monitoring SQL Server Agent Jobs](../technical-guides/monitoring-sql-server-agent-jobs.md)<br /><br /> If the SQL Server Agent jobs are not running, system performance will degrade over time. For more information about the SQL Server Agent jobs that BizTalk Server provides to help manage the BizTalk Server databases, see [Database Structure and Jobs](https://go.microsoft.com/fwlink/p/?LinkID=153451) (https://go.microsoft.com/fwlink/p/?LinkID=153451).|
|Ensure that the SQL Server jobs responsible for backing up BizTalk Server databases are running normally (administration check).|-   [How to Configure the Backup BizTalk Server Job](https://go.microsoft.com/fwlink/p/?LinkID=153813) (https://go.microsoft.com/fwlink/p/?LinkID=153813)<br />-   [How to Schedule the Backup BizTalk Server Job](https://go.microsoft.com/fwlink/p/?LinkId=154674) (https://go.microsoft.com/fwlink/p/?LinkId=154674)|
|Ensure that the latest security updates are installed (security check).|Microsoft Update site at [http://update.microsoft.com/microsoftupdate/v6/default.aspx](https://update.microsoft.com/microsoftupdate/v6/default.aspx)|
|Analyze weekly performance monitoring logs against baseline and thresholds (performance check).|-   [Using the Performance Analysis of Logs (PAL) Tool](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)<br />-   [Troubleshooting Performance Issues3](../technical-guides/troubleshooting-performance-issues3.md)|
|Ensure that the system is not experiencing frequent auto-growth of BizTalk Server databases (performance check).|-   [Defining Auto-Growth Settings for Databases](../technical-guides/defining-auto-growth-settings-for-databases.md)<br />-   [Tracking Database Sizing Guidelines](https://go.microsoft.com/fwlink/p/?LinkId=154677) (https://go.microsoft.com/fwlink/p/?LinkId=154677).<br />-   [Identifying Bottlenecks in the Database Tier](https://go.microsoft.com/fwlink/p/?LinkId=154678) (https://go.microsoft.com/fwlink/p/?LinkId=154678).<br />-   [Database File Initialization](https://go.microsoft.com/fwlink/p/?LinkID=101579) (https://go.microsoft.com/fwlink/p/?LinkID=101579).<br />-   [Performing SQL Server Maintenance Procedures](~/technical-guides/checklist-configuring-sql-server.md)|
|Run SQL Server Profiler during high load to check for long response times and high resource usage (performance check).|[Using SQL Server Profiler](https://go.microsoft.com/fwlink/p/?LinkID=106720) (https://go.microsoft.com/fwlink/p/?LinkID=106720).|
|Ensure that message batching for all adapters is appropriate for resource consumption or latency (performance check).|-   [Configuring Batching to Improve Adapter Performance](../technical-guides/configuring-batching-to-improve-adapter-performance.md)<br />-   [How to Design a Performant Adapter](https://go.microsoft.com/fwlink/p/?LinkId=154679) (https://go.microsoft.com/fwlink/p/?LinkId=154679).|
|Ensure that the large message threshold is appropriate for resource consumption (performance check).|[How BizTalk Server Processes Large Messages](https://go.microsoft.com/fwlink/p/p/?LinkId=154680) (https://go.microsoft.com/fwlink/p/p/?LinkId=154680).|
|Archive backup files and specify appropriate computers for backup|To avoid potential data loss, you should specify a computer for your backup that is different from the computer with the original data, and for \<destination path\> you should specify a computer to store the database logs that is different from the computer with the original database logs.<br /><br /> For more information about best practices for backup, see [Best Practices for Backing Up and Restoring Databases](https://go.microsoft.com/fwlink/p/p/?LinkID=151391) (https://go.microsoft.com/fwlink/p/p/?LinkID=151391).|

## See Also
 [Routine Monitoring Tasks](../technical-guides/routine-monitoring-tasks.md)
