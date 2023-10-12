---
description: "Learn more about: Maintaining Performance"
title: "Maintaining Performance"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Maintaining Performance
This section provides information that is intended to help you resolve performance issues discovered during your routine maintenance checks. You can also use the tools and techniques described here proactively, to identify potential problems before they become critical issues.

 You will generally need to establish a performance baseline as a standard against which to assess current system performance.

 In addition to the topics in this section, other topics in this document address performance issues. These topics are listed in Related Sections below.

## In This Section

-   [Best Practices for Maintaining Performance](../technical-guides/best-practices-for-maintaining-performance.md)

-   [Configuring Batching to Improve Adapter Performance](../technical-guides/configuring-batching-to-improve-adapter-performance.md)

-   [How to Adjust the Configuration Cache Refresh Interval](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md)

-   [How to Disable Tracking](../technical-guides/how-to-disable-tracking.md)

-   [Troubleshooting Performance Issues3](../technical-guides/troubleshooting-performance-issues3.md)

## Related Sections

- For more information about performance issues in general, see [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Performance Optimization Guide at [https://go.microsoft.com/fwlink/?LinkID=150492](https://go.microsoft.com/fwlink/?LinkID=150492).

- For information about analyzing weekly performance monitor logs against baseline and thresholds, see [Using the Performance Analysis of Logs (PAL) Tool](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md), "Finding and Eliminating Bottlenecks" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Performance Optimization Guide at [https://go.microsoft.com/fwlink/?LinkId=154675](https://go.microsoft.com/fwlink/?LinkId=154675), and [Troubleshooting Performance Issues3](../technical-guides/troubleshooting-performance-issues3.md).

- For information about ensuring that the system is not experiencing frequent auto-growth of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, see [Defining Auto-Growth Settings for Databases](../technical-guides/defining-auto-growth-settings-for-databases.md), "Tracking Database Sizing Guidelines" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [https://go.microsoft.com/fwlink/?LinkId=154677](../core/tracking-database-sizing-guidelines.md), and "Identifying Bottlenecks in the Database Tier" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [https://go.microsoft.com/fwlink/?LinkId=154678](/previous-versions/).

- For information about maintaining SQL Server, [Performing SQL Server Maintenance Procedures](~/technical-guides/checklist-configuring-sql-server.md).

- For information about running SQL Server Profiler during high load to check for long response times and high resource usage, see "Using SQL Server Profiler" in SQL Server Help at [https://go.microsoft.com/fwlink/?LinkID=106720](/sql/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions).

- For information about ensuring that message batching for all adapters is appropriate for resource consumption or latency, see [Configuring Batching to Improve Adapter Performance](../technical-guides/configuring-batching-to-improve-adapter-performance.md).

- For information about increasing the BizTalk Server cache refresh interval, see [How to Adjust the Configuration Cache Refresh Interval](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md).

- For information about inbound and outbound host throttling, see "What is Host Throttling?" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [https://go.microsoft.com/fwlink/?LinkId=154694](../core/what-is-host-throttling.md). For information about triggers, actions, and mitigation strategies for inbound and outbound throttling, see "Throttling condition triggers, actions, and mitigation strategies" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [https://go.microsoft.com/fwlink/?LinkId=154695](../core/how-biztalk-server-implements-host-throttling.md).

- To use a PassThrough send pipeline instead of the default XML send pipeline, see "Managing Send Ports Using BizTalk Explorer" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [https://go.microsoft.com/fwlink/?LinkID=154696](https://go.microsoft.com/fwlink/?LinkID=154696).

- For information about sizing the tracking database, see "Tracking Database Sizing Guidelines" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [https://go.microsoft.com/fwlink/?LinkId=154677](../core/tracking-database-sizing-guidelines.md).

- For information about sizing the MessageBox, BizTalkDTADb, and BAMPrimaryImport databases, see "Identifying Bottlenecks in the Database Tier" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help at [https://go.microsoft.com/fwlink/?LinkId=154678](/previous-versions/).

- For information about avoiding contention in the MessageBox database, see [How to Avoid Disk Contention](https://go.microsoft.com/fwlink/?LinkId=158809) ([https://go.microsoft.com/fwlink/?LinkId=158809](https://go.microsoft.com/fwlink/?LinkId=158809)) in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Performance Optimization Guide.