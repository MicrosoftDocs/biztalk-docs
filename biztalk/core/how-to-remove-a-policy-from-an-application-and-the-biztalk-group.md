---
title: "How to Remove a Policy from an Application and the BizTalk Group | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deleting, policies"
  - "managing [policies], applications"
  - "managing [policies], deleting"
  - "groups, policies"
  - "managing [policies], groups"
  - "applications, policies"
ms.assetid: e9882cb3-8808-4258-a107-a24905290288
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Remove a Policy from an Application and the BizTalk Group
This topic describes how to use the BizTalk Server Administration console or the command-line to remove a policy from an application and the Rule Engine database for the BizTalk group.  
  
 Before removing a policy, bear in mind the following important points:  
  
-   You cannot remove a deployed policy. You must first undeploy the policy, as described in [How to Deploy or Undeploy a Policy](../core/how-to-deploy-or-undeploy-a-policy.md). Undeploying a policy makes it inactive so that it no longer functions in any application that uses it in the BizTalk group.  
  
-   Removing a policy deletes it from the Rule Engine database. If you want to use this policy again, you should export it to an .xml file before removing it. For instructions, see [How to Export a Policy](../core/how-to-export-a-policy.md).  
  
-   If the policy is used by other applications, it will no longer be in effect for the other applications. Verify that you no longer want to use the policy for any other applications that reference it before you remove it.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To remove a policy  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand  **BizTalk Server Administration**, expand the BizTalk group containing the policy to remove, and then expand the application containing the policy  
  
3. Click **Policies**, right-click the policy, and then click **Remove**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask RemoveResource** [**/ApplicationName:**<em>value</em>] **/Luid:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"Rule/Policy1/1.0"**  
  
   |Parameter|Description|  
   |---------------|-----------------|  
   |**/ApplicationName**|Name of the BizTalk application containing the policy to delete. If this parameter is not specified, the default application is used.|  
   |**/Luid**|Locally unique identifier (LUID) of the policy. You can obtain the LUID by using the **ListApp** command, as described in [ListApp Command](../core/listapp-command.md).|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database. Required if you specify the Database parameter. If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.|  
   |**/Database**|Name of the BizTalk Management database. Required if you specify the Server parameter. If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.|  
  
## See Also  
 [Managing Policies](../core/managing-policies.md)