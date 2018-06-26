---
title: "How to Remove a BizTalk Assembly from an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [applications], assemblies"
  - "assemblies, deleting"
  - "deleting, assemblies"
  - "applications, assemblies"
  - "managing [assemblies], deleting"
ms.assetid: 0691c3b6-476d-4e01-b50b-47d7c0b299bf
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove a BizTalk Assembly from an Application
This topic describes how use the BizTalk Server Administration console or the command line to remove a BizTalk assembly from a BizTalk application. When you do this, the assembly and the artifacts that it includes, such as orchestrations, schemas, and pipelines, are removed from the application and the BizTalk Management database.  
  
 Before removing a BizTalk assembly, bear in mind the following important points:  
  
-   When you remove a BizTalk assembly, the assembly file is not automatically removed from the global assembly cache (GAC) or the local file system, if it exists there. You must manually remove it. For instructions, see [How to Uninstall an Assembly from the GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4) and [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
-   If you remove a BizTalk assembly that includes a pipeline, any send ports in the same application that use the pipeline will be reset to use the default, PassThruTransmit pipeline.  
  
-   You cannot remove a BizTalk assembly on which other artifacts depend. You must first remove the dependent artifacts. Then you can remove the BizTalk assembly.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To remove a BizTalk assembly from an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand BizTalk Server Administration, expand the BizTalk group containing the BizTalk assembly to remove, and then expand the application containing the BizTalk assembly.  
  
3. Click the **Resources** folder, right-click the BizTalk assembly, and then click **Remove**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask RemoveResource** [**/ApplicationName:**<em>value</em>] **/Luid:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**  
  
   |Parameter|Description|  
   |---------------|-----------------|  
   |**/ApplicationName**|Name of the BizTalk application containing the BizTalk assembly to delete. If this parameter is not specified, the default application is used. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Luid**|Locally unique identifier (LUID) of the BizTalk assembly. You can obtain the LUID by using the **ListApp** command, as described in [ListApp Command](../core/listapp-command.md).|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
## See Also  
 [Managing BizTalk Assemblies](../core/managing-biztalk-assemblies.md)   
 [RemoveResource Command](../core/removeresource-command.md)