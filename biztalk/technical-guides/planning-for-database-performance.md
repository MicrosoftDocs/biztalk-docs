---
description: "Learn more about: Planning for Database Performance"
title: "Plan for Database Performance"
ms.custom: ""
ms.date: "11/29/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Planning for Database Performance

## Overview
Microsoft BizTalk Server is an extremely database intensive application that may require the creation of up to 13 separate databases in Microsoft SQL Server. Because of the database intensive nature of BizTalk Server, it is of critical importance that you choose the appropriate version and edition of SQL Server that will house the BizTalk Server databases. To optimize the performance of the computers running SQL Server that house the BizTalk Server databases, follow the recommendations in this topic and in the [BizTalk Server Database Optimization](optimizing-database-performance.md).
  

> [!NOTE]  
>  While this guide is written for other versions of BizTalk Server and SQL Server, you can probably use the same recommendations for newer versions.
  
## Considerations for SQL Server Editions  
 BizTalk Server databases should be configured to run on a dedicated SQL Server instance whenever possible. BizTalk Server is a database intensive application, so separation of the BizTalk Server computers and the SQL Server computers that house the BizTalk Server databases will improve performance and should be considered a best practice in a production BizTalk Server environment.  
  
 Various editions of SQL Server provide different features which can affect the performance of your BizTalk Server environment. For example, under high-load conditions, the number of available database locks that are available for the 32-bit version of SQL Server may be exceeded, which is detrimental to the performance of the BizTalk solution. Consider housing your MessageBox database on a 64-bit version of SQL Server if you are experiencing "out of lock" errors in your test environment. The number of available locks is significantly higher on the 64-bit version of SQL Server.  
  
 Consider the table below when deciding on the database engine features that you will need for your BizTalk environment. For small-scale solutions, for example when running BizTalk Server Branch Edition, SQL Server Workgroup Edition may be adequate for housing the BizTalk Server databases. For large scale, enterprise-level solutions that require clustering support, BizTalk log shipping support, or Analysis Services support, then you need SQL Server Enterprise Edition to host the databases.  
  
|Edition of SQL Server|64-bit support|Multi-Instance Support|Clustering support|Analysis Services|  
|---|---|---|---|---|  
|SQL Server Enterprise Edition|Yes|Yes|Yes|Yes|  
|SQL Server Standard Edition|Yes|Yes|Yes (2 node)|Yes|  
|SQL Server Workgroup Edition|Yes|Yes|No|No|  
  
> [!NOTE]  
>  BAM RTA requires SQL Server Enterprise Edition.  
  
 For a complete list of the features supported by the editions, see [Features Supported by the Editions of SQL Server](/sql/sql-server/editions-and-components-of-sql-server-2016).