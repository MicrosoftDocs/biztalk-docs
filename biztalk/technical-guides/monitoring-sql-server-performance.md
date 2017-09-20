---
title: "Monitoring SQL Server Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
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
# Monitoring SQL Server Performance
[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provides several tools for monitoring events in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and for tuning the physical database design. These tools are described in the topic [Tools for Performance Monitoring and Tuning](http://go.microsoft.com/fwlink/?LinkId=146357) (http://go.microsoft.com/fwlink/?LinkId=146357) in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] books online. Information about specific tools used for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performance monitoring and tuning is provided below.  
  
## SQL Server Performance Monitoring Tools  
 Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is such a database-intensive process, it is often helpful to take a peek at what is going on in SQL Server when troubleshooting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance issues. The remainder of this topic describes performance monitoring tools available for reviewing both real-time and archived data on [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] and [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)].  
  
### SQL Server 2008 R2 Activity Monitor  
 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Activity Monitor provides information about [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] processes and how these processes affect the current instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. For more information about [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Activity Monitor, see [Activity Monitor](http://go.microsoft.com/fwlink/?LinkId=146355) (http://go.microsoft.com/fwlink/?LinkId=146355) in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] books online. For information about how to open Activity Monitor from [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio, see [How to: Open Activity Monitor (SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=135094) (http://go.microsoft.com/fwlink/?LinkId=135094) in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] books online.  
  
### SQL Server 2008 R2 Data Collection  
 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] provides a data collector that you can use to obtain and save data that is gathered from several sources. The data collector enables you to use data collection containers, which enable you to determine the scope and frequency of data collection on a computer that is running [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]. For more information about implementing [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] data collection, see [Data Collection](http://go.microsoft.com/fwlink/?LinkId=146356) (http://go.microsoft.com/fwlink/?LinkId=146356) in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] books online.  
  
## See Also  
 [Optimizing Database Performance](../technical-guides/optimizing-database-performance.md)