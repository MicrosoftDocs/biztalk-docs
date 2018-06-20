---
title: "How to Uninstall a BizTalk Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [applications], uninstalling"
  - "applications, uninstalling"
  - "uninstalling, applications"
  - "undeploying, uninstalling"
ms.assetid: ab721c6e-194e-4b8a-bfd1-d0139d284373
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Uninstall a BizTalk Application
This topic describes how to use the Add or Remove Programs control panel or the BTSTask command-line tool to uninstall a BizTalk application. These are the only supported methods for uninstalling an application. If you installed multiple .msi files for this application, for example to update the application, double-clicking the .msi file or using msiexec may not completely uninstall the application and are therefore not supported uninstallation methods.  
  
> [!CAUTION]
>  Uninstalling a BizTalk application while it is running can cause errors in the application. In order to avoid this problem, as a best practice we recommend that you verify there are no running service instances for the application, as described in [How to Search for All Service Instances](../core/how-to-search-for-all-service-instances.md). If necessary, you can stop the application by using the Full Stop option to completely stop all running instances, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md). Be aware that when you do this, in-process messages will not complete.  
  
 A pre- or post-processing script should be included in the application .msi file to remove all of the files and settings associated with the application when it is uninstalled. If a pre- or post-processing script has not been included, the procedures in this topic will remove the application's files and settings from the local file system, with the following exceptions.  
  
- If the application includes a virtual directory, the virtual directory and its files are deleted, unless files were added to the virtual directory after the application was installed. In this case, the virtual directory and the added files are not deleted. If you want to delete the virtual directory and the added files, you must do so explicitly.  
  
- Pre- and post-processing scripts are deleted, but any files added by the scripts during installation or uninstallation are not deleted, nor are any actions taken by the scripts undone. If you want to delete files added by scripts or undo their actions, you must do so explicitly.  
  
  > [!NOTE]
  >  Only pre-or post-processing scripts that have a destination location specified in its deployment properties when the application is imported will run during uninstallation. For more information, see [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).  
  
- Certificates are never deleted when you uninstall a BizTalk application. If you want to delete a certificate, you must do so explicitly. In addition, components are not removed from the Windows Registry and BizTalk assemblies are not removed from the global assembly cache (GAC). If you want to remove them, you must do so explicitly. For more information, see [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
  If you cancel the uninstallation operation before it completes, BizTalk Server will roll back the uninstallation, except for any actions that were taken by pre- or post-processing scripts before the operation was canceled. To restore the application to its state before you started the uninstallation, double-click the .msi file and reinstall the application. If multiple .msi files have been installed for this application, you should double-click each .msi file to reinstall the application in the order in which the .msi files were originally installed.  
  
  For more information about post-processing scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
> [!NOTE]
>  To completely undeploy a BizTalk application, you must also delete it from the BizTalk group, as described in [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with appropriate permissions. For more information, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To uninstall a BizTalk application  
  
#### Using Uninstall or change a program  
  
1.  On the computer running the application, click **Start**, click **Control Panel**, and then double-click  **Programs and Features**.  
  
2.  On **Uninstall or change a program** page, right-click the BizTalk application to remove, and then click **Uninstall**.  
  
     Windows Installer removes the specified application.  
  
3.  If the application is running on multiple computers, repeat these steps on each computer.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate value, as described in the following table:  
  
    **BTSTask UninstallApp** [**/ApplicationName:**<em>value</em>]  
  
    Example:  
  
    **BTSTask UninstallApp /ApplicationName:MyApplication**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to uninstall. If the name includes spaces, you must enclose it in double quotation marks (").|  
  
## See Also  
 [Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md)   
 [UninstallApp Command](../core/uninstallapp-command.md)