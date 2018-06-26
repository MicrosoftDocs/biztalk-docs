---
title: "How to Delete a BizTalk Application from the BizTalk Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "undeploying, applications"
  - "applications, deleting"
  - "applications, groups"
  - "undeploying, deleting"
  - "managing [applications], deleting"
  - "deleting, applications"
  - "applications, undeploying"
  - "managing [applications], groups"
  - "groups, applications"
ms.assetid: 968a6436-ae1a-4f85-bb44-e704826a0197
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Delete a BizTalk Application from the BizTalk Group
You can delete an application from the BizTalk group. This removes all of its data from the BizTalk databases for the group, and the application no longer displays in the BizTalk Server Administration console. It does not uninstall the application.  
  
 Before you delete an application, bear in mind the following points:  
  
-   The application must be stopped before you can delete it. You should use the Full Stop option for stopping the application, as described in [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
-   You can delete an application only if no other applications contain references to it. If other applications contain references to the application you want to remove, you must first remove the references from the other applications. For instructions, see [How to Remove a Reference to Another Application](../core/how-to-remove-a-reference-to-another-application.md).  
  
-   You cannot delete an application if it contains a send port group of which a send port in another application is a member. You must unenlist the member send port before you can delete the application. For instructions, see [How to Unenlist a Send Port or Send Port Group](../core/how-to-unenlist-a-send-port-or-send-port-group.md).  
  
-   You cannot delete an application if it contains a send port that is referenced by a party. You can delete the reference from the party, delete the send port, or move the send port to a different application. For instructions on performing these tasks, see [How to View or Edit a Party](http://msdn.microsoft.com/library/42e6f3a0-8f7d-4f6c-ab05-a1fab7bf46ca), [How to Delete a Send Port](../core/how-to-delete-a-send-port.md), or [How to Move an Artifact to a Different Application](../core/how-to-move-an-artifact-to-a-different-application.md).  
  
-   You cannot delete the default application. If you want to delete it, you must first make another application the default. For instructions, see [How to Change the Default Application](../core/how-to-change-the-default-application.md).  
  
-   You cannot delete an application if an orchestration in the application has a suspended instance.  
  
-   To completely undeploy a BizTalk application, you must also take the steps described in [How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md), and you may also need to remove other files and settings, as described in [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To delete a BizTalk application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand  **BizTalk Server Administration**, expand the BizTalk group, and expand **Applications**.  
  
3. Right-click the application folder, and then click **Delete**.  
  
4. Click **Yes** to confirm the deletion.  
  
    BizTalk Server deletes all of the application data from the BizTalk databases and removes the application from the administration console.  
  
    If BizTalk Server cannot delete any of the application artifacts, the delete operation fails. In this case, BizTalk Server attempts to roll back the delete operation.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask RemoveApp /ApplicationName:** *value* [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask RemoveApp /ApplicationName:MyApplication**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to delete. If the name includes spaces, you must enclose it in double quotation marks (").|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database. Required if you specify the Database parameter. If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.|  
   |**/Database**|Name of the BizTalk Management database. Required if you specify the Server parameter. If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.|  
  
## See Also  
 [Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md)   
 [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md)