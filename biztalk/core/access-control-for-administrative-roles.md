---
title: "Access Control for Administrative Roles | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "roles, administrative"
  - "administrator accounts, administrative roles"
  - "administrative roles"
  - "access control, administrative roles"
ms.assetid: 328e049b-921d-4057-85f0-7d008ec308bb
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Access Control for Administrative Roles
When a user opens any of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tools that require access to the databases or to Windows resources, the interactive user of the tool must have the proper SQL Server and Windows user rights in order to perform the various tasks that the tools support.  
  
 One or more of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tools access the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases. Therefore, BizTalk Server must grant some level of access in each database to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators. Furthermore, for security reasons, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators should not have more user rights than necessary to perform their jobs. Using SQL Server database roles, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can fulfill both requirements. Anytime you create a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database through installation or the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically creates SQL Server database roles for both these administrative roles in that database. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] grants each role, and any SQL Server login assigned to the role, the minimum user rights needed by administrators on the SQL Server objects (tables, views, stored procedures, etc) to perform administrative tasks on that database.  
  
> [!NOTE]
>  There are some administrative tasks that require BizTalk Administrators to have more permission that those given to them through the SQL Server roles such as creating host instances. For more information about these additional permissions, see [Minimum Security User Rights](../core/minimum-security-user-rights.md).  
  
 In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], there are two Administrative Roles: the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrator, and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operator. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrator is a high privilege role with access to configuration and tracking data. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operator is a low privilege role with access only to monitoring and troubleshooting actions. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators group:  
  
- Is a lower privilege administrative role without access to message data.  
  
- Enables members to monitor [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for errors, query for suspended messages\instances, view configuration.  
  
- Prevents members from changing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration. For example [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Operators cannot change send ports, receive locations, filters on ports, deploy new artifacts.  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] creates the default [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrator Role when you install the product for the first time. By default, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] calls this [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators, although you can choose a different name.  
  
  Similarly, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] creates in each database a SQL Server Database role for the user group for each host, and grants this role the minimum user rights it needs for the user group to perform tasks for that host. You must add the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators to the Single Sign-On Affiliate Administrators Group. For more information about Enterprise Single Sign-On, see [Using SSO](../core/using-sso.md).  
  
> [!CAUTION]
>  BizTalk administrators must ensure they trust the source of the assembly they will deploy in the system. If they deploy assemblies with code you do not trust, they may expose the BizTalk environment to potential attacks. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not enforce any restrictions on the actions that custom code components can perform when the BizTalk engine invokes them.  
  
## See Also  
 [Access Control and Data Security](../core/access-control-and-data-security.md)   
 [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)