---
description: "Learn more about: How to Install an Assembly in the GAC"
title: "How to Install an Assembly in the GAC"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: install-set-up-deploy
---
# How to Install an Assembly in the GAC
Manually install and uninstall a BizTalk assembly in the global assembly cache (GAC) using the Gacutil tool included with [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
 Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], you can have BizTalk assemblies automatically installed in the GAC when they are deployed from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Set this option in the Deployment Properties of the BizTalk project; see [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). You cannot, use this method to install non-BizTalk .NET assemblies in the GAC; you must install them manually, as described in this topic.  
  
> [!NOTE]
>  You can also specify deployment options for assemblies after they are deployed into a BizTalk application by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. See [How to Modify the Deployment Options of a BizTalk Assembly](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md), and [How to Modify the Deployment Options of a .NET Assembly, COM Component, File, or BAM Artifact](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md).  
  
## Prerequisites  
Sign in with an account that has Write permission to the GAC. The Administrators account on the local computer has this permission.  

  
## Install using gacutil
  
1.  Copy the BizTalk assembly to your local computer.  
  
2.  Open **Developer Command Prompt for Visual Studio** as administrator.  
  
3.  Type the following:  
  
     `gacutil /i path_to_assembly_file /f`

    For example, type:  
    `gacutil /i c:\temp\filename.dll /f`
    
The `/f` option overwrites any existing assembly that has the same assembly name. For more info on the gacutil commands and options, type `gacutil /?`. 

## Uninstall using gacutil
Uninstalling an assembly from the global assembly cache (GAC) is necessary to completely undeploy an application. You can automate this process. Before deploying the application into a production environment, write a pre-processing script that uninstalls the assembly from the GAC automatically when the application is uninstalled. See [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
 You can also use a script to remove additional files and settings. See [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
 
#### Using the Windows interface  
  
1.  Open to %systemdrive%\Windows\Assembly.  
  
2.  Right-click each assembly file included in your application, select **Uninstall**, and then select **Yes** to confirm.  
  
#### Using the command line  
  
1.  Open **Developer Command Prompt for Visual Studio** as administrator. 
  
2.  Type the following:  
  
     `gacutil /u` \<*fully qualified assembly name*\>  
  
     For example, type:  
     `gacutil /u "hello,Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"`
       
## See Also  
 [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)  
[Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md)   
 [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md)   
 [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)
 
