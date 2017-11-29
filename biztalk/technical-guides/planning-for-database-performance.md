---
title: "Planning for Database Performance | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7212fa37-88e0-4b5f-af97-c72063357645
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for Database Performance
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is an extremely database intensive application that may require the creation of up to 13 separate databases in Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Because of the database intensive nature of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], it is of critical importance that you choose the appropriate version and edition of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that will house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. To optimize the performance of the computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, follow the recommendations in this topic and in the [BizTalk Server Database Optimization](http://go.microsoft.com/fwlink/?LinkID=101578) white paper ([http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578)).  
  
 BizTalk Server databases must be installed on either [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] or [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)].  
  
> [!NOTE]  
>  While this white paper is written for other versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], you can use the same recommendations for BizTalk Server and [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] / [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)].  
  
## Considerations for SQL Server Editions  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases should be configured to run on a dedicated SQL Server instance whenever possible. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is a database intensive application, so separation of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers and the SQL Server computers that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases will improve performance and should be considered a best practice in a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.  
  
 Various editions of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provide different features which can affect the performance of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment. For example, under high-load conditions, the number of available database locks that are available for the 32-bit version of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] may be exceeded, which is detrimental to the performance of the BizTalk solution. Consider housing your MessageBox database on a 64-bit version of SQL Server if you are experiencing "out of lock" errors in your test environment. The number of available locks is significantly higher on the 64-bit version of SQL Server.  
  
 Consider the table below when deciding on the database engine features that you will need for your BizTalk environment. For small-scale solutions, for example when running BizTalk Server Branch Edition, [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] / [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Workgroup Edition may be adequate for housing the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. For large scale, enterprise-level solutions that require clustering support, BizTalk log shipping support, or Analysis Services support, then you will need [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] / [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Enterprise Edition to house the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases.  
  
|Version and Edition of SQL Server|64-bit support|Multi-Instance Support|Clustering support|Analysis Services|  
|---------------------------------------|---------------------|-----------------------------|------------------------|-----------------------|  
|SQL Server 2008 SP1 / SQL Server 2008 R2 Enterprise Edition|Yes|Yes|Yes|Yes|  
|[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] / [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Standard Edition|Yes|Yes|Yes (2 node)|Yes|  
|[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] / [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Workgroup Edition|Yes|Yes|No|No|  
  
> [!NOTE]  
>  BAM RTA requires [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] / [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Enterprise Edition.  
  
 For a complete list of the features supported by the editions of [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)], see [Features Supported by the Editions of SQL Server 2008 R2](http://go.microsoft.com/fwlink/?LinkId=151940) ([http://go.microsoft.com/fwlink/?LinkId=151940](http://go.microsoft.com/fwlink/?LinkId=151940)) in the [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] documentation.