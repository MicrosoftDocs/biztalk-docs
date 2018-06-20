---
title: "How to Remove Other Files and Settings for a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [applications], deleting settings"
  - "managing [applications], deleting files"
  - "undeploying, settings"
  - "applications, undeploying"
  - "undeploying, files"
ms.assetid: b947831a-c988-435c-92ec-45f3fd6967de
caps.latest.revision: 17
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove Other Files and Settings for a BizTalk Application
This topic describes how to remove files and settings for a BizTalk application that may not be removed when you uninstall the application (which is described in [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md)). For example, certificates, COM and COM+ registry entries, and COM files are not removed unless the application included a post-processing script that removed them on uninstallation.  
  
> [!CAUTION]
>  Before removing any shared items, make certain that no other applications are using them, or the applications will not function correctly.  
  
> [!NOTE]
>  We recommend that you automate this removal by using a post-processing script. For more information, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
- **Delete Certificates.** There are two ways to delete certificates from the certificate store: by using the Certificate Manager (certmgr.exe) command-line tool or the Certificates snap-in. Certmgr.exe is installed with the .NET SDK, which is one of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation prerequisites. You can run certmgr.exe manually, or you can run it from a post-processing script. For more information about using certmgr.exe, see [Certificate Manager Tool (certmgr.exe)](http://go.microsoft.com/fwlink/?LinkId=56198) at the Microsoft Web site.  
  
   The Certificates snap-in is included in both Windows Server 2008 and Windows Vista. To delete a certificate, open the snap-in, as described in "Starting the Certificates snap-in" in Help for your operating system, and then delete the certificate as described in "Delete a certificate" in Certificates Help.  
  
- **Remove assemblies from the Windows Registry.** To remove .NET and BizTalk assemblies from the Windows registry, use regsvcs or regasm, which are included with the .NET SDK, which is one of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation prerequisites. For reference information, see [.NET Services Installation Tool (Regsvcs.exe)](http://go.microsoft.com/fwlink/?LinkId=56199) and [Assembly Registration Tool (Regasm.exe)](http://go.microsoft.com/fwlink/?LinkId=56200) at the Microsoft Web site.  
  
- **Remove COM components from the Windows Registry.** To remove COM components from the Windows Registry, use regsvr32. For reference information, see "Regsvr32" in Help for your operating system. This tool is included in both Windows Server 2008 and Windows Vista Professional.  
  
- **Uninstall assemblies from the global assembly cache (GAC).** Assemblies are not automatically uninstalled from the GAC. You can uninstall an assembly from the GAC manually or by using a script. For more information, see [How to Uninstall an Assembly from the GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4).  
  
## Prerequisites  
 To remove the files and settings described in this topic, you must be logged on with Write permissions on the Windows Registry, the GAC, or the certificate store, depending on what you want to remove. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## See Also  
 [Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md)   
 [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md)