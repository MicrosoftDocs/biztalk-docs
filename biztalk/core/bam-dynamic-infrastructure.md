---
description: "Learn more about: BAM Dynamic Infrastructure"
title: "BAM Dynamic Infrastructure | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "infrastructure, BAM"
  - "BAM, infrastructure"
ms.assetid: 88f39438-3213-4f0d-8b8d-e6426c266138
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM Dynamic Infrastructure
The BAM infrastructure consists of SQL Server tables, BAM views, stored procedures, and Data Transformation Services (DTS) packages in the BAM databases (Primary Import, Archive, Star Schema, and Analysis) as configured and managed through incremental deployments of BAM definitions. The infrastructure is where, at run time, events are correlated, aggregated, and then made available for querying by users.  
  
 This section describes some of these infrastructure processes. For example, once you extract the data of interest from your applications (the BAM definition), you can store it so that it is available for queries. Additionally, you can maintain certain pre-created aggregations of the data for faster aggregated queries.  
  
 Typically, you achieve such functionality by an extensive development effort to implement a data warehouse. BAM in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] greatly simplifies this process, however, by automatically generating the SQL and OLAP infrastructure based on your activity and view definitions.  
  
## In This Section  
  
-   [What Is a BAM Definition?](../core/what-is-a-bam-definition.md)  
  
-   [What Is a BAM Definition Schema?](../core/what-is-a-bam-definition-schema.md)  
  
-   [Activity Data Storage](../core/activity-data-storage.md)  
  
-   [What Is an Aggregation?](../core/what-is-an-aggregation.md)  
  
-   [Querying BAM Data](../core/querying-bam-data.md)  
  
-   [BAM Infrastructure Limitations](../core/bam-infrastructure-limitations.md)  
  
-   [How to Define Out-of-Range Numeric Dimension Alerts In Non-English Installations](../core/define-out-of-range-numeric-dimension-alerts-in-non-english-installations--bam.md)
