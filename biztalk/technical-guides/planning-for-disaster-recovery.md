---
title: "Planning for Disaster Recovery | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a33e8875-cfde-4a60-9dab-fc6bb3ac4f1c
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Planning for Disaster Recovery
This topic provides guidance to application teams for disaster recovery requirements and procedures for BizTalk Server. Microsoft BizTalk Server stores configuration and processing information in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. BizTalk Server high availability and disaster recovery is achieved through the high availability and disaster recovery capabilities of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
 A BizTalk group is defined by a set of databases hosted in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. The set of databases hosted in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] can be made highly available through the use of a Windows Server cluster. In a BizTalk environment, the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provide the “run-time environment” and the databases on the computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provide the persistent store for the environment. Therefore, BizTalk Server backup, restore, and disaster recovery procedures are heavily focused on [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
## Purpose  
 This topic consolidates [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] disaster recovery information from the core documentation, various Microsoft Web sites, and information from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] product team to define disaster recovery procedures for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environments.  
  
 Application teams should thoroughly test backup, restore, and disaster recovery procedures. You should also ensure the procedures are tailored to meet application requirements before entering production.  
  
## Scope  
 This section focuses on disaster recovery procedures for BizTalk Server and related procedures for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. This guide builds on related documentation about how to back up and restore BizTalk Server.  
  
 For more information about backup and restore, see this documentation and see [Backing Up and Restoring BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154071) (http://go.microsoft.com/fwlink/?LinkID=154071) in BizTalk Server Help. Each application team must augment the information in this topic with additional procedures specific to their environment, such as document computer names, drive letters, and cluster configuration, as well as disaster recovery procedures for related non-BizTalk applications that are part of the solution.  
  
 This topic does not provide detailed disaster recovery procedures for the following areas:  
  
- Non-BizTalk applications  
  
- Application source code  
  
- Certificates  
  
- Application operations  
  
  There may be additional areas that require documentation in an application’s disaster recovery plan not listed above that must be addressed by each application team.  
  
## In This Section  
  
-   [Best Practices for Disaster Recovery](../technical-guides/best-practices-for-disaster-recovery.md)  
  
-   [What Is BizTalk Server Log Shipping?](../technical-guides/what-is-biztalk-server-log-shipping.md)