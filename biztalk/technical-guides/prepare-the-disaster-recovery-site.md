---
title: "Prepare the Disaster Recovery Site | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b66f3c8-afe0-4ac0-b925-8f780d14bd4b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Prepare the Disaster Recovery Site
BizTalk Server log shipping has two supported scenarios. One is where log shipping for all databases on all production instances of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is applied to a single disaster recovery instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. The other scenario is where log shipping for the databases for each production instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is applied to a corresponding instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] at the disaster recovery site. Note that it is fully supported to have the same number of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances in the disaster recovery site as there is in production but on fewer physical servers. This section provides guidance on these preparations.  
  
## In This Section  
  
-   [Preparing the Disaster Recovery SQL Servers](../technical-guides/preparing-the-disaster-recovery-sql-servers.md)  
  
-   [Backing Up the BAM Analysis and Tracking Analysis Server Databases](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)  
  
-   [Preparing the Disaster Recovery BizTalk Servers](../technical-guides/preparing-the-disaster-recovery-biztalk-servers.md)  
  
-   [Preparing Applications for Disaster Recovery](../technical-guides/preparing-applications-for-disaster-recovery.md)  
  
-   [How to Restore the Master Secret Server](../technical-guides/how-to-restore-the-master-secret-server.md)