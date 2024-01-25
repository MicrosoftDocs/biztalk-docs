---
title: "Monitor SQL Server Performance"
description: Monitor BizTalk Server databases using performance tools, Activity Monitor, and Data collection
ms.custom: ""
ms.date: "11/29/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Monitor SQL Server Performance
SQL Server provides several tools for monitoring events in SQL Server and for tuning the physical database design. [Tools for Performance Monitoring and Tuning](/sql/relational-databases/performance/performance-monitoring-and-tuning-tools) describes these tools. 
  
BizTalk Server is a database-intensive process. when troubleshooting BizTalk Server performance issues, it can be beneficial to also check the SQL Server performance. The following tools can help.  
  
## SQL Server Activity Monitor  
SQL Server Activity Monitor provides information about SQL Server processes and how these processes affect the current instance of SQL Server. For more information, see [Activity Monitor](/sql/relational-databases/performance-monitor/activity-monitor), and [How to: Open Activity Monitor (SQL Server Management Studio](/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio). 
  
## SQL ServerData Collection  
SQL Server provides a data collector that you can use to obtain and save data that is gathered from several sources. The data collector enables you to use data collection containers, which enable you to determine the scope and frequency of data collection on a computer that is running SQL Server. See [Data Collection](/sql/relational-databases/data-collection/data-collection).
  
## See Also  
 [Optimizing Database Performance](../technical-guides/optimizing-database-performance.md)