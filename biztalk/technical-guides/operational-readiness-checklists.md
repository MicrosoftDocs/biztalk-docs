---
title: "Operational Readiness Checklists | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c308a876-9872-43b3-a1fb-76e81396612f
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operational Readiness Checklists
The Operational Readiness checklists contain recommendations that you should consider and tasks that you should perform before deploying a BizTalk solution into production. These checklists include information for configuring prerequisite software, increasing availability, monitoring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, and procedures for testing.  
  
 Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] maintains dependencies on so many other Microsoft technologies, you should complete the tasks for each dependent technology to help ensure that your production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment runs smoothly.  
  
## Typical Prerequisite Software  
 Prerequisite software for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application platform typically includes the following products:  
  
-   The Windows operating system  
  
-   [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] SP1 or [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)] (for development purposes, not at run time)  
  
## Additional Components  
 The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application platform may also require several of the following software components:  
  
-   Internet Information Services (IIS)  
  
-   Windows SharePoint® Services 2010  
  
-   SharePoint Foundation 2010  
  
-   Microsoft Office SharePoint Server 2007 Service Pack 1 (SP1) (MOSS)  
  
-   Windows SharePoint Services 3.0 with SP1 or SP2  
  
-   Microsoft Office Excel 2010 or 2007  
  
    > [!NOTE]  
    >  [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] supports only the 32-bit version of Microsoft Office 2010.  
  
-   SQL Server 2005 Notification Services  
  
-   SQLXML 4.0 with Service Pack 1  
  
-   .NET Framework 1.0  
  
-   .NET Framework 2.0  
  
-   .NET Framework 3.0  
  
-   Microsoft .NET Framework 4 and .Net Framework 3.5 with Service Pack 1 (SP1)  
  
-   Non-Microsoft components to enable functionality for certain [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapters.  
  
 For more information about the dependency software that is required for specific features of the BizTalk application platform for various Windows operating system versions, see the "Feature Dependency Matrix" section in the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installation and upgrade guide for the specific Windows operating system version. The [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installation and upgrade guides are available at [http://go.microsoft.com/fwlink/?LinkID=152913](http://go.microsoft.com/fwlink/?LinkID=152913).  
  
## In This Section  
  
-   [Checklist: Getting Started with BizTalk Server](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)  
  
-   [Checklist: Configuring Windows Server](../technical-guides/checklist-configuring-windows-server.md)  
  
-   [Checklist: Configuring Internet Information Services](../technical-guides/checklist-configuring-internet-information-services.md)  
  
-   [Checklist: Configuring SQL Server](~/technical-guides/checklist-configuring-sql-server.md)  
  
-   [Checklist: Configuring BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)  
  
-   [Checklist: Providing High Availability with Fault Tolerance or Load Balancing](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)  
  
-   [Checklist: Increasing Availability with Disaster Recovery](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)  
  
-   [Checklist: Monitoring Operational Readiness](../technical-guides/checklist-monitoring-operational-readiness.md)  
  
-   [Checklist: Maintaining and Troubleshooting BizTalk Server Databases](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)  
  
-   [Checklist: Testing Operational Readiness](../technical-guides/checklist-testing-operational-readiness.md)