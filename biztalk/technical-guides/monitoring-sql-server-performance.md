---
title: "Monitor SQL Server Performance | Microsoft Docs"
description: Monitor BizTalk Server databases using performance tools, Activity Monitor, and Data collection
ms.custom: ""
ms.date: "11/29/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 020fa764-968e-467c-b146-d069f5606a0f
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Monitor SQL Server Performance
SQL Server provides several tools for monitoring events in SQL Server and for tuning the physical database design. [Tools for Performance Monitoring and Tuning](https://docs.microsoft.com/en-us/sql/relational-databases/performance/performance-monitoring-and-tuning-tools) describes these tools. 
  
BizTalk Server is a database-intensive process. when troubleshooting BizTalk Server performance issues, it can be beneficial to also check the SQL Server performance. The following tools can help.  
  
## SQL Server Activity Monitor  
SQL Server Activity Monitor provides information about SQL Server processes and how these processes affect the current instance of SQL Server. For more information, see [Activity Monitor](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor), and [How to: Open Activity Monitor (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio). 
  
## SQL ServerData Collection  
SQL Server provides a data collector that you can use to obtain and save data that is gathered from several sources. The data collector enables you to use data collection containers, which enable you to determine the scope and frequency of data collection on a computer that is running SQL Server. See [Data Collection](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection).
  
## See Also  
 [Optimizing Database Performance](../technical-guides/optimizing-database-performance.md)