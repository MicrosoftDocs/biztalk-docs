---
title: "How to Remove a Pre- or Post-processing Script from an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [scripts], deleting"
  - "deleting, scripts"
  - "managing [applications], scripts"
  - "scripts, deleting"
  - "applications, scripts"
ms.assetid: 7911f098-97f2-4a5d-87fe-20b55231113e
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove a Pre- or Post-processing Script from an Application
This topic describes how to use the BizTalk Server Administration console or the command line to remove a pre- or post-processing script from an application. This removes the script from the BizTalk Management database, so that it will not be exported in the application .msi file. This does not remove the script from the local file system, if it exists there.  
  
 If the application containing the script has been installed on the local file system, and the script is designed to run during uninstallation, you must remove the script from the file system to prevent it from running when the application is uninstalled.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To remove a script from an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the script to remove, and then expand the application containing the script.  
  
3. Click the **Resources** folder, right-click the script, and then click **Remove**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask RemoveResource** [**/ApplicationName:**<em>value</em>] **/Luid:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApplication:MyScript.vbs"**  
  
   |Parameter|Description|  
   |---------------|-----------------|  
   |**/ApplicationName**|Name of the BizTalk application containing the BizTalk script to delete. If the name includes spaces, it must be enclosed in double quotation marks ("). If this parameter is not specified, the default application is used.|  
   |**/Luid**|Locally unique identifier (LUID) of the script. You can obtain the LUID by using the [ListApp Command](../core/listapp-command.md).|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Managing Pre- and Post-processing Scripts](../core/managing-pre-and-post-processing-scripts.md)   
 [RemoveResource Command](../core/removeresource-command.md)