---
title: "How to Modify the Deployment Options of a .NET Assembly, COM Component, File, or BAM Artifact | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [.NET assemblies], deploying"
  - "deploying, virtual directories"
  - "managing [applications], deploying"
  - "managing [applications], modifying"
  - "definition files [BAM], modifying"
  - "modifying, artifacts"
  - "deploying, artifacts"
  - "managing [certificates], deploying"
  - "deploying, .NET assemblies"
  - "COM components, deploying"
  - "definition files [BAM], deploying"
  - "virtual directories, deploying"
  - "deploying, certificates"
  - "modifying, deployment options"
  - "virtual directories, modifying"
  - "deploying, COM components"
ms.assetid: 4955d420-d9ff-4d5a-82f4-fb16477a828c
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Modify the Deployment Options of a .NET Assembly, COM Component, File, or BAM Artifact
This topic describes how to use the BizTalk Server Administration console to modify the deployment options of the following resource artifacts:  
  
- .NET assemblies  
  
- COM components  
  
- Ad hoc files  
  
- BAM artifacts  
  
  You might want to modify the deployment properties to change the destination location to which the artifact file will be copied when the application is installed on the local computer. If you do not provide a path, the file will not be copied to the local computer on installation.  
  
  In addition, you might want to modify the following options for a .NET assembly:  
  
- **Add to the global assembly cache on add resource (gacutil).** When you select this option, the assembly is added to the global assembly cache (GAC) on the local computer when the assembly is added to the application. In addition, if you later refresh the assembly (right-click it and click **Refresh**), the assembly is added to the GAC. Clearing the check box for this option does not remove the assembly from the GAC, if it currently exists there.  
  
- **Add to the global assembly cache on MSI file import (gacutil).** When you select this option, if the application is exported to an .msi file, and the .msi file is imported into a BizTalk group, the assembly is installed in the GAC on the local computer as part of the import process.  
  
- **Add to the global assembly cache on MSI file install (gacutil).** When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, the assembly is installed in the GAC on the local computer as part of the installation process.  
  
- **Make visible to COM components (regasm).** When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, a managed COM assembly is added to the Windows registry on the local computer as part of the installation process. If you specify this option, you must also specify a location for the file in Destination.  
  
- **Register serviced components (regsvcs).** When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, a managed COM+ assembly is added to the Windows registry on the local computer as part of the installation process. If you specify this option, you must also specify a location for the file in Destination.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. In addition, if you select an option that immediately adds the assembly to the GAC, your account must also be a member of the local Administrator's group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To modify the deployment properties of a resource artifact  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the artifact for which to modify deployment options, and then expand the application containing the artifact.  
  
3. Click the **Resources** folder, right-click the artifact, and then click **Modify**.  
  
4. On the **Options** tab, modify the deployment options as necessary, and then click **OK**.  
  
## See Also  
 [Managing .NET Assemblies, Certificates, and Other Resources](../core/managing-net-assemblies-certificates-and-other-resources.md)