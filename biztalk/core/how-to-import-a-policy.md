---
title: "How to Import a Policy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "policies, requirements"
  - "importing, policies"
  - "policies, importing"
  - "managing [policies], importing"
ms.assetid: 92f6ef18-279f-416d-b13e-8b9642539d27
caps.latest.revision: 29
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Import a Policy
This topic describes how to use the BizTalk Server Administration console to import a policy into a BizTalk group or the BTSTask command-line tool to import a policy into a BizTalk application.  
  
 You can create a policy by using the Business Rule Composer, as described in [Creating Business Rules Using the Business Rule Composer](../core/creating-business-rules-using-the-business-rule-composer.md), and then import it directly, or you can export a policy from another BizTalk group, as described in [How to Export a Policy](../core/how-to-export-a-policy.md) and then import it.  
  
 Importing a policy registers it in the Rule Engine database for the BizTalk group. After you import the policy, you can view it in the BizTalk Server Administration console. If you use the BizTalk Server Administration console to import a policy, it will display in the \<All Artifacts\> node for the BizTalk group. You can then publish it to make it available to add it to a BizTalk application, as described in [How to Publish a Policy](../core/how-to-publish-a-policy.md). If you use the BTSTask command-line tool to import a policy, the policy will be automatically published and will display in the Policies folder of the application into which you imported it.  
  
 When importing a policy, bear in mind the following important points:  
  
- Even if you specify the option to overwrite an existing policy with the imported policy, you cannot import a policy that already exists in the Rule Engine database for the group and has been deployed. The import operation will fail.  
  
- Even if the policy was in a deployed state when exported from another BizTalk group, it will be in an undeployed state when imported.  
  
- BTSTask does not provide a specific command for importing policies; however you can use the ExportApp command of BTSTask to selectively export only the policies in an application that you want, including no other application artifacts. Then you can use the ImportApp command to import the .msi file into an application in a different BizTalk group. This is the approach described in this topic. When you do this, the policy is automatically imported and published in the BizTalk group and added to the specified application.  
  
  For more information about working with policies, see [Managing Policies](../core/managing-policies.md). For best practices on adding policies to applications, see [Best Practices for Deploying a BizTalk Application](../core/best-practices-for-deploying-a-biztalk-application.md).  
  
> [!NOTE]
>  The solution developer can create policies and then import them into the Rule Engine database for the group by using the Rule Engine Deployment Wizard, as described in [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
## Prerequisites  
 The following are prerequisites for performing the procedures in this topic:  
  
-   You must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
-   The Business Rule Engine must be installed. For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).  
  
-   If you want to use the BizTalk Server Administration console to import a policy, you must have available an .xml file containing the policy that you want to import. You can generate such an .xml file by exporting a policy from another BizTalk group or application, as described in [How to Export a Policy](../core/how-to-export-a-policy.md), or by using the Business Rule Composer, as described in [How to Import and Export Policies and Vocabularies](../core/how-to-import-and-export-policies-and-vocabularies.md).  
  
-   If you want to use BTSTask to import a policy, you must have an .msi file containing the policy to import. For instructions, see [How to Export a Policy](../core/how-to-export-a-policy.md).  
  
## To import a policy  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group into which you want to import the policy, expand **Applications**, and then expand **\<All Artifacts\>**.  
  
3. Right-click **Policies**, and then click **Import**.  
  
4. Browse to the .xml file containing the policy and click **Open**.  
  
    The policy is imported into the group and displays in the **Policies** folder of **\<All Artifacts\>**.  
  
#### Using the command line  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2. Type the following command, substituting the appropriate values, as described in the following table:  
  
    **BTSTask ImportApp /Package:** *value* [**/ApplicationName:**<em>value</em>] [**/Overwrite**] [**/Server:**<em>value</em>] [**/Database:**<em>value</em>]  
  
    Example:  
  
    **BTSTask ImportApp /Package:"C:\MSI Files\MyApplication.msi"  /Environment:Test /ApplicationName:MyApplication /Overwrite**  
  
   |Parameter|Value|  
   |---------------|-----------|  
   |**/Package**|Full path of the .msi file containing the policy to import. If the path includes spaces, you must enclose it in quotation marks (").|  
   |**/ApplicationName**|Name of the BizTalk application into which to import the policy. If not specified, the application name that was specified when exporting the .msi file is used. If the specified application does not exist, it will be created. Application names that include spaces must be enclosed with double quotation marks (").|  
   |**/Overwrite**|Option to overwrite policies in the application with artifacts in the .msi file that have the same name and version number. If this option is not specified, and there are one or more policies in the application that have the same name and version number as policies in the .msi file, the import fails. You can view the name and version number of the policies in an application by using the [ListApp Command](../core/listapp-command.md).|  
   |**/Server**|Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.<br /><br /> Instance name is only required when the instance name is different than the server name. Port is only required when SQL Server uses a port number other than the default (1433).<br /><br /> Examples:<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> If not provided, the name of the SQL Server instance running on the local computer is used.|  
   |**/Database**|Name of the BizTalk Management database. If not specified, the BizTalk Management database running in the local instance of SQL Server is used.|  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
## See Also  
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [Exporting BizTalk Applications, Bindings, and Policies](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [Managing Policies](../core/managing-policies.md)