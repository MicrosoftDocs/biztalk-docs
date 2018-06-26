---
title: "Clustering the BizTalk Server Databases1 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "clustering, how to"
  - "clustering, SQL Servers"
  - "SQL Server, clustering"
  - "BizTalk Server Configuration Wizard"
  - "high availability, databases"
  - "clustering, BizTalk Server Configuration Wizard"
  - "clustering, databases"
  - "clustering, prerequisites"
ms.assetid: 9a1ed843-483b-4a56-961b-bc6801a07b64
caps.latest.revision: 32
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Clustering the BizTalk Server Databases
This section provides guidelines for deploying a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution with high availability. If the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases become unavailable, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment will not function correctly. To provide high availability, you can create a Microsoft SQL Server cluster for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, as shown in the following figure.  
  
 ![BizTalk Server Database Tier](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 To provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must have at least two computers that are running SQL Server and a shared disk array for use by a  Windows Server Failover Cluster.  
  
## Procedures for Clustering the Databases  
  
#### Before you start  
  
1. When you create the domain groups for your BizTalk Server environment, you must create Active Directory domain global groups.  
  
2. Configure the SQL Server cluster before you install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. For more information about clustering SQL Server, see [Always On Failover Cluster Instances](https://technet.microsoft.com/library/ms189134.aspx).  
  
3. If you are also clustering the master secret server, configure that server first. For more information about high availability for Enterprise Single Sign-On, see [High Availability for Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).  
  
#### To run the BizTalk Server Configuration Wizard  
  
1. Install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a runtime server.  
  
2. Launch the BizTalk Configuration Program. Click **Start**, point to **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.  
  
3. Follow the steps in [Import and Export BizTalk Server Configuration](../install-and-config-guides/import-and-export-biztalk-server-configuration.md) to apply a custom configuration. To specify the SQL Server cluster for the BizTalk databases, enter the name of the SQL Server cluster in the **Databases** dialog of the configuration program as described in the **Editing Databases** section of this topic.  
  
4. Complete the BizTalk Server configuration by following the instructions in [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).  
  
## See Also  
 [Creating a Highly Available BizTalk Server Environment](../core/creating-a-highly-available-biztalk-server-environment.md)