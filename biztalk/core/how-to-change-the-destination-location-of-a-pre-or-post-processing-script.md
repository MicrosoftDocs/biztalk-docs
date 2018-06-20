---
title: "How to Change the Destination Location of a Pre- or Post-processing Script | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "scripts, file locations"
  - "scripts, modifying"
  - "managing [scripts], modifying"
  - "managing [scripts], file locations"
ms.assetid: 4a4fdaef-099f-4c29-9815-12404c7a2212
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Change the Destination Location of a Pre- or Post-processing Script
This topic describes how to use the BizTalk Server Administration console to change the destination location of a pre- or post-processing script. This is the location to which the script is copied when the application is installed. You might want to change the destination location when deploying an application into a different environment.  
  
> [!IMPORTANT]
>  Be sure to provide a destination location for a script that will run when the application is uninstalled. If you do not, the script will not be copied to the local file system, and therefore will not run during uninstallation.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To modify the deployment properties of a pre- or post-processing script  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the script to modify, and then expand the application containing the script.  
  
3. Click the **Resources** folder, right-click the script, and then click **Modify**.  
  
4. In **Destination location**, type the full path of the destination location, including the file name, and then click **OK**. (You can use the environment variable %BTAD_InstallDir% in the path to specify the application installation folder.)  
  
## See Also  
 [Managing Pre- and Post-processing Scripts](../core/managing-pre-and-post-processing-scripts.md)