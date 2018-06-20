---
title: "How to View the Dependencies for a BizTalk Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "viewing, dependencies"
  - "assemblies, dependencies"
  - "managing [assemblies], dependencies"
  - "assemblies, viewing"
  - "viewing, assemblies"
  - "managing [assemblies], viewing"
ms.assetid: 872abc99-8248-4397-9fcb-24a0ba6f4757
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to View the Dependencies for a BizTalk Assembly
This topic describes how to use the BizTalk Server Administration console to view the list of artifacts that have dependencies on a BizTalk assembly. For background information about dependencies and how they affect application deployment, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group or BizTalk Operators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To view the dependencies of a BizTalk assembly  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the BizTalk assembly for which you want to view dependencies, and then expand the application containing the BizTalk assembly.  
  
3. Click the **Resources** folder, right-click the BizTalk assembly, and then click **Modify**.  
  
4. Click the **Dependencies** tab.  
  
    The name and status of the artifacts that have dependencies on this BizTalk assembly are displayed in the list.  
  
## See Also  
 [Managing BizTalk Assemblies](../core/managing-biztalk-assemblies.md)