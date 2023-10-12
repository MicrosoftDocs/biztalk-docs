---
description: "Learn more about: How to Remove Other Files and Settings for a BizTalk Application"
title: "How to Remove Other Files and Settings for a BizTalk Application"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Remove Other Files and Settings for a BizTalk Application
This topic describes how to remove files and settings for a BizTalk application that may not be removed when you uninstall the application (which is described in [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md)). For example, certificates, COM and COM+ registry entries, and COM files are not removed unless the application included a post-processing script that removed them on uninstallation.

> [!CAUTION]
>  Before removing any shared items, make certain that no other applications are using them, or the applications will not function correctly.

> [!NOTE]
>  We recommend that you automate this removal by using a post-processing script. For more information, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).

- **Delete Certificates.** There are two ways to delete certificates from the certificate store: by using the Certificate Manager (certmgr.exe) command-line tool or the Certificates snap-in. Certmgr.exe is installed with the .NET SDK, which is one of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation prerequisites. You can run certmgr.exe manually, or you can run it from a post-processing script. For more information about using certmgr.exe, see [Certificate Manager Tool (certmgr.exe)](/previous-versions/dotnet/netframework-1.1/e78byta0(v=vs.71)) at the Microsoft Web site.

   The Certificates snap-in is included in both Windows Server 2008 and Windows Vista. To delete a certificate, open the snap-in, as described in "Starting the Certificates snap-in" in Help for your operating system, and then delete the certificate as described in "Delete a certificate" in Certificates Help.

- **Remove assemblies from the Windows Registry.** To remove .NET and BizTalk assemblies from the Windows registry, use regsvcs or regasm, which are included with the .NET SDK, which is one of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation prerequisites. For reference information, see [.NET Services Installation Tool (Regsvcs.exe)](/previous-versions/dotnet/netframework-1.1/04za0hca(v=vs.71)) and [Assembly Registration Tool (Regasm.exe)](/previous-versions/dotnet/netframework-1.1/tzat5yw6(v=vs.71)) at the Microsoft Web site.

- **Remove COM components from the Windows Registry.** To remove COM components from the Windows Registry, use regsvr32. For reference information, see "Regsvr32" in Help for your operating system. This tool is included in both Windows Server 2008 and Windows Vista Professional.

- **Uninstall assemblies from the global assembly cache (GAC).** Assemblies are not automatically uninstalled from the GAC. You can uninstall an assembly from the GAC manually or by using a script. For more information, see [How to Uninstall an Assembly from the GAC](/dotnet/framework/app-domains/how-to-remove-an-assembly-from-the-gac).

## Prerequisites
 To remove the files and settings described in this topic, you must be logged on with Write permissions on the Windows Registry, the GAC, or the certificate store, depending on what you want to remove. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).

## See Also
 [Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md)
 [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md)
