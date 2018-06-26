---
title: "How to Modify the Deployment Options of a BizTalk Assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifying, deploying"
  - "managing [assemblies], modifying"
  - "deploying, assemblies"
  - "managing [assemblies], deploying"
  - "assemblies, deploying"
ms.assetid: d25e2f71-08bd-4786-ab6c-35ae4e88b8cc
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Modify the Deployment Options of a BizTalk Assembly
This topic describes how to use the BizTalk Server Administration console to modify the deployment options of a BizTalk assembly.  
  
 You can specify the following deployment options:  
  
-   **Add to the global assembly cache on add resource (gacutil).** When you select this option, the assembly is added to the global assembly cache (GAC) on the local computer when the assembly is added to the application. In addition, if you later refresh the assembly (right-click it and click **Refresh**), the assembly is added to the GAC. Clearing the check box for this option does not remove the assembly from the GAC, if it currently exists there.  
  
-   **Add to the global assembly cache on MSI file import (gacutil).** Install the assembly to the GAC on the local computer when the application .msi file is imported.  
  
-   **Add to the global assembly cache on MSI file install (gacutil).** Install the assembly to the GAC on the local computer when the application is installed from the .msi file.  
  
-   **Destination location:** Path to which the assembly file will be copied when the application is installed. If a path is not provided, the assembly file is not copied to the local file system on installation.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. In addition, if you select an option that immediately adds the assembly to the GAC, your account must also be a member of the local Administrator's group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To modify the deployment options of a BizTalk assembly  
  
1. Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand BizTalk Server Administration, expand the BizTalk group containing the BizTalk assembly for which to modify deployment options, and then expand the application containing the BizTalk assembly.  
  
3. Click the **Resources** folder, right-click the BizTalk assembly, and then click **Modify**.  
  
4. In **Options**, select the check boxes of the deployment options that you want.  
  
5. If necessary, in **Destination location** edit the path where the assembly will be copied when the application is installed, and then click **OK**.  
  
## See Also  
 [Managing BizTalk Assemblies](../core/managing-biztalk-assemblies.md)