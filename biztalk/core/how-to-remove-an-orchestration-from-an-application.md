---
title: "How to Remove an Orchestration from an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications, orchestrations"
  - "deleting, orchestrations"
  - "managing [orchestrations], deleting"
  - "orchestrations, applications"
  - "orchestrations, deleting"
ms.assetid: e6d635ea-3513-42de-a667-b56c536e5328
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove an Orchestration from an Application
This topic describes how to use the BizTalk Server Administration console or the command line to remove an orchestration from a BizTalk application. Removing an orchestration from an application also deletes it from the BizTalk Management database for the BizTalk group.  
  
 When you remove an orchestration, the following occurs:  
  
- The orchestration is deleted from the BizTalk Management database.  
  
- The BizTalk assembly that contains the orchestration is deleted from the BizTalk Management database, but is not removed from the local file system or the global assembly cache (GAC), if it exists in these locations.  
  
- As a consequence of the BizTalk assembly being deleted, all artifacts contained in the assembly are deleted from the BizTalk Management database as well.  
  
  Before removing an orchestration from an application, bear in mind the following important points:  
  
- If other artifacts have dependencies on this orchestration or the artifacts contained in the assembly that will also be removed, they will no longer function correctly when you remove the orchestration. For background information about dependencies, see [Dependencies and Application Deployment](../core/dependencies-and-application-deployment.md).  
  
- You cannot remove an orchestration that has running instances. You must terminate any running instances.  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To remove an orchestration from an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group, expand **Applications**, and then expand the application containing the orchestration that you want to remove.  
  
3. Click **Orchestrations**, right-click the orchestration, and then click **Unenlist**.  
  
4. Select the orchestration, point to **View**, and then click **Instance Information**.  
  
5. In the query results pane, right-click the orchestration instances, and then click **Terminate**.  
  
   > [!NOTE]
   >  You can unenlist, terminate running instances, and stop all of the orchestrations in an application at once by using the Full Stop option for the application, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
6. Click **Orchestrations**, right-click the orchestration, and then click **Remove**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask RemoveResource** [**/ApplicationName:**<em>value</em>] **/Luid:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"**  
  
   |Parameter|Description|  
   |---------------|-----------------|  
   |**/ApplicationName**|Name of the BizTalk application containing the orchestration to delete. If the name includes spaces, you must enclose it in double quotation marks ("). If this parameter is not specified, the default application is used.|  
   |**/Luid**|Locally unique identifier (LUID) of the orchestration. You can obtain the LUID by using the [ListApp Command](../core/listapp-command.md).|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database. Required if you specify the Database parameter. If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.|  
   |**/Database**|Name of the BizTalk Management database. Required if you specify the Server parameter. If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.|  
  
## See Also  
 [Managing Orchestrations](../core/managing-orchestrations.md)   
 [RemoveResource Command](../core/removeresource-command.md)