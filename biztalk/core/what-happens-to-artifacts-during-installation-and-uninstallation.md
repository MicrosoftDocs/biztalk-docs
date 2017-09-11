---
title: "What Happens to Artifacts During Installation and Uninstallation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "uninstalling, artifacts"
  - "artifacts, uninstalling"
  - "installing, artifacts"
  - "artifacts, installing"
  - "uninstalling"
ms.assetid: f7b5bd8b-bfdf-4536-ae64-fa98c4885be6
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Happens to Artifacts During Installation and Uninstallation
This topic describes how BizTalk Server handles file-based artifacts included in a BizTalk application when you install and uninstall the application.  
  
> [!NOTE]
>  Send ports, send port groups, receive locations, and receive ports are not file-based artifacts and are not affected by installation and uninstallation. Orchestrations, schemas, maps, and pipelines are all deployed and managed as part of the BizTalk assemblies that contain them.  
  
-   **BizTalk assembly.** During installation, the BizTalk assembly file is copied to the destination path, if one was specified when the assembly was added to the application. It also installs the assembly to the global assembly cache (GAC) if this option was specified when the assembly was added. When the application is uninstalled, the assembly file is deleted from the file system if it exists there, but is not uninstalled from the GAC, unless the developer included a post-processing script in the application to perform this operation. If necessary, you can uninstall BizTalk assemblies from the GAC manually. For more information, see [How to Uninstall an Assembly from the GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4).  
  
-   **.NET assembly.** During installation, the .NET assembly file is copied to the destination path, if one was specified when the assembly was added to the application. It also installs the assembly to the GAC and the Windows Registry if these options were specified when the assembly was added. When the application is uninstalled, the assembly file is deleted from the file system if it exists there and is not in the Windows Registry. The assembly is not removed from the GAC or the Windows Registry, unless the developer included a post-processing script in the application to perform this operation. If necessary, you can remove BizTalk assemblies from the GAC or the Windows Registry manually. For more information, see [How to Uninstall an Assembly from the GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4) and [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
-   **File.** During installation, the file is copied to the local file system, if a destination path was specified when the file was added to the application. When the application is uninstalled, the file is deleted from the file system.  
  
-   **Certificate.** During installation, the certificate is added to the Other People certificate store on the local computer. When the application is uninstalled, the certificate is not removed, unless the developer included a post-processing script in the application to perform this operation. If necessary, you can remove certificates manually. For more information, see [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
-   **Virtual directory.** If Internet Information Services (IIS) exists on the computer where the application is installed, the virtual directory is created. If a virtual directory having the same name already exists that uses the specified port, the virtual directory resources in the application .msi file are written to the existing virtual directory, and security settings for the existing virtual directory are left unchanged. You should verify that these security settings are sufficient. If the application pool to which the virtual directory is bound does not exist on the local computer when you install the application, the virtual directory is bound to the default application pool.  
  
     When the application is uninstalled, the virtual directory and its files are deleted, unless the virtual directory existed before installation, or files were added to the virtual directory following installation. In this case, only the files that were installed from the application .msi file are deleted. The virtual directory and files added to it after application installation are not deleted. The virtual directory is deleted only if it is empty.  
  
-   **COM component.** During installation, the COM component is added to the Windows Registry if this option was specified when the component was added to the application. In addition, the file is copied to the local file system, if a destination location was specified when the component was added to the application. When the application is uninstalled, the COM component is not removed from the Windows Registry or the file system unless the developer included a post-processing script in the application to perform this function. If necessary, you can remove COM components from the Windows Registry and file system manually. For more information, see [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
-   **Pre-processing and post-processing scripts.** During installation, script files are copied to the local file system, if a destination path was specified when the file was added to the application. Pre-processing scripts run before application import or removal and after uninstallation. Post-processing scripts run after application import or removal and before installation. Script files are deleted from the file system when the application is uninstalled. However, if a pre- or post-processing script added files to the file system they are not deleted. If necessary, you can delete files manually. For more information, see [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
-   **BAM artifacts.** During installation, BAM artifact files are copied to the destination path that was specified when the artifact was added to the application. BAM artifacts are not deployed when the application is installed. When the application is uninstalled, BAM artifact files are deleted.  
  
## See Also  
 [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md)   
 [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md)   
 [What Happens to Artifacts During Application Deployment](../core/what-happens-to-artifacts-during-application-deployment.md)