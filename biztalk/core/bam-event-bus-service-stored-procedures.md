---
title: "BAM Event Bus Service Stored Procedures | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "stored procedures, Even Bus Service [BAM]"
  - "Event Bus Service [BAM], stored procedures"
ms.assetid: 18a7bd40-50ce-44f2-88ae-45a2e3c8d3f4
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM Event Bus Service Stored Procedures
You use the following stored procedures to manage the BAM Event Bus service:  
  
-   To pause the BAM Event Bus service, execute the TDDS_BlockTDDS stored procedure within a transaction (without committing the transaction) on the BAM database. To resume the BAM Event Bus service, commit the TDDS_BlockTDDS transaction.  
  
-   To enable the BAM Event Bus service on multiple computers, identify which host(s) to use for tracking, and then join those computers to the tracking host.  
  
-   To set up a session time-out and heartbeat interval, use the TDDS_UpdateSettings stored procedure. Only members of the BTS_ADMIN_USERS group have permission to execute this stored procedure.  
  
     The TDDS_UpdateSettings stored procedure has the following parameters:  
  
    -   @RefreshInterval int. Set to greater than 60 seconds.  
  
    -   @SqlCommandTimeout int. Set to less than RefreshInterval.  
  
    -   @SessionTimeout int. Set to greater than two times the RefreshInterval.  
  
    -   @EventLoggingInterval nvarchar(16). Set to greater than 60 seconds.  
  
    -   @RetryCount int. Set to greater than 60 seconds  
  
    -   @ThreadPerSession int. This parameter is obsolete.  
  
## See Also  
 [Managing BAM](../core/managing-bam.md)