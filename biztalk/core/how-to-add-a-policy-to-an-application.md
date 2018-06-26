---
title: "How to Add a Policy to an Application | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [policies], adding to applications"
  - "policies, applications"
  - "applications, policies"
  - "policies, adding to applications"
ms.assetid: 93b3ce5e-8c63-4c64-9bdc-1747541ba9a8
caps.latest.revision: 18
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Policy to an Application
This topic describes how to use the BizTalk Server Administration console or the command line to add a policy to a BizTalk application. When using the administration console, you can add more than one policy at a time. Adding a policy to an application makes it available for use by that application as well as any other applications that reference it.  
  
 When adding a policy to an application, bear in mind the following important points:  
  
-   Before you can add a policy to an application, the policy must exist in the Rule Engine database for the BizTalk group, and it must be published, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).  
  
    > [!NOTE]
    >  When you remove a policy from the Rule Engine database by using the Rule Engine Deployment Wizard, it will still display in the administration console, but, you will not be able to publish it. For more information about the Rule Engine Deployment Wizard, see [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
-   The policy cannot already exist in another application in the BizTalk group.  
  
    > [!IMPORTANT]
    >  If a policy is shared across two or more applications, you should create a separate application to contain the policy and then create references from the applications that use the policy to the application containing the policy. This is because if you stop an application that contains a policy, the policy is automatically undeployed and no longer functions for any of the applications that use it. For instructions on adding a reference, see [How to Add a Reference to Another Application](../core/how-to-add-a-reference-to-another-application.md).  
  
-   For the policy to take effect and begin functioning, it must also be deployed. Policies are automatically deployed when the application starts, or you can manually deploy them as described in [How to Deploy or Undeploy a Policy](../core/how-to-deploy-or-undeploy-a-policy.md).  
  
## Prerequisites  
 To perform the procedures in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## To add a policy to an application  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and the BizTalk group.  
  
3. Expand Applications, expand the application to which you want to add a policy, and then right-click **Policies**.  
  
4. Point to **Add** and click **Policy**.  
  
5. Select the check box of each policy and version to add, and then click **OK**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask AddResource** [**/ApplicationName:**<em>value</em>] **/Type:System.BizTalk:Rules** [**Overwrite**] **/Name:**<em>value</em>**/Version:**<em>value</em> [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
   > [!NOTE]
   >  Parameter values are case sensitive. Parameter names are not case sensitive. Also, when you add a policy to an application by using this command, any vocabularies used by the policy are automatically added as well.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
    Example:  
  
    **BTSTask AddResource /ApplicationName:MyApplication /Type:System.BizTalk:Rules /Overwrite /Name:MyPolicy /Version:1.0 /Server:MyDatabaseServer /Database:BizTalkMgmtDb**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/ApplicationName**|Name of the BizTalk application to which to add the policy. If the application name is not specified, the default BizTalk application for the group is used. Names that include spaces must be enclosed in double quotation marks (").|  
   |**/Type**|**System.BizTalk:Rules**|  
   |**/Overwrite**|Option to update an existing policy. If not specified, and a policy already exists in the application that has the same name as the policy being added, the AddResource operation fails.|  
   |**/Name**|Name of the policy.|  
   |**/Version**|Version number of the policy.|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database. Required if you specify the Database parameter. If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.|  
   |**/Database**|Name of the BizTalk Management database. Required if you specify the Server parameter. If Server and Database parameters are not specified, the default BizTalk Management database for the group is used.|  
  
## See Also  
 [Managing Policies](../core/managing-policies.md)   
 [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md)   
 [AddResource Command: Policy](../core/addresource-command-policy.md)