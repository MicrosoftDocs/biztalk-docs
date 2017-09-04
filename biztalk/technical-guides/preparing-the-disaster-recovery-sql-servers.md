---
title: "Preparing the Disaster Recovery SQL Servers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44b77fe8-393d-4781-b0b0-5b7f6e50a67b
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Preparing the Disaster Recovery SQL Servers
Createa set of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances in the disaster recovery site. To ensure that the disaster recovery [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances can provide the same level of performance as the production [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances, the disaster recovery [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances should be configured with similar hardware and number of physical computers running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. In this scenario, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] log shipping will be configured for each production [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instance to apply to a corresponding [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instance at the disaster recovery site.  
  
 A key [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] log shipping requirement is that the drive letter(s) on the production site where the database files are stored match the drive letter(s) at the disaster recovery site where the database files are restored. So if the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database file group is located on G:\data in production, there must be a G:\data directory on the destination (DR) server, or the restore will fail.  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] log shipping does not support the **RESTORE WITH MOVE** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] command. Because of this, we recommend that database instance names at the disaster recovery site match the database instance names in production (by default, the instance name is part of the file path). Another option is to simply create a directory on the corresponding drive letter in the disaster recovery computer running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] so that the **RESTORE** operation can create the file in the same directory structure as is used in production.  
  
 Create [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] security logins for the disaster recovery site that correspond to the production site so that in the event that a failover to the disaster recovery site is required, all required security logins are present on the destination system.  
  
 Once installation of the disaster recovery [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances is completed, perform a full backup of master and msdb databases so that a clean system can be restored in the event that a switch to the disaster recovery site fails.