---
title: "Managing the BAM Dynamic Infrastructure | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "infrastructure, managing [BAM]"
  - "managing [BAM], infrastructure"
ms.assetid: af8a76b5-407a-484d-aff4-0d911f88313e
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Managing the BAM Dynamic Infrastructure
Business Activity Monitoring (BAM) features use a dynamically generated SQL and online analytical processing (OLAP) infrastructure. Administrators use the BAM Management utility to deploy the BAM definition workbook or XML file, which the business analyst develops.  
  
 The BAM dynamic infrastructure consists of the BAM workbook views, BAM deployments, the BAM Data Transformation Services (DTS) packages, and the BAM databases. For more information about the BAM dynamic infrastructure, see [BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md).  
  
 BizTalk Server creates the following BAM databases when you configure BizTalk Server:  
  
- BAM Primary Import (BAMPrimaryImport) database  
  
- BAM Star Schema (BAMStarSchema) database (optional)  
  
- BAM Analysis (BAMAnalysis) database (optional)  
  
- BAM Archive (BAMArchive) database  
  
  For information about the BAM databases, see [Managing BAM Databases](../core/managing-bam-databases.md).  
  
  Administrators perform the following management tasks for the BAM infrastructure, which are described in this section:  
  
- Deploy and undeploy BAM definitions and views  
  
- Manage user access to BAM views  
  
- Run the BAM DTS packages  
  
- Back up the BAM databases  
  
## In This Section  
  
-   [Managing BAM Definitions](../core/managing-bam-definitions.md)
  
-   [Managing BAM Security](../core/managing-bam-security.md)  
  
-   [Managing Aggregations](../core/managing-aggregations.md) 
  
-   [Managing BAM Databases](../core/managing-bam-databases.md)
  
## See Also  
 [Managing BAM](../core/managing-bam.md)