---
title: "How to Export a Policy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [policies], exporting"
  - "policies, exporting"
  - "exporting, policies"
ms.assetid: 2e46d96a-7762-479b-be20-bd590b2a4f0a
caps.latest.revision: 30
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Export a Policy
This topic describes how to use the BizTalk Server Administration console or the command line to export one or more policies and associated vocabularies.  
  
 When exporting a policy, bear in mind the following important points:  
  
-   Using the BizTalk Server Administration console, you can export policies from a BizTalk group or a BizTalk application as well as the vocabularies to export. Using BTSTask, you can export policies from an application, and all of the associated vocabularies will be exported as well. You cannot select the vocabularies to export.  
  
    > [!IMPORTANT]
    >  When using the administration console, you can select which vocabularies to export. We recommend that you select for export all of the vocabularies associated with a policy. This way, you can be sure that the required vocabularies are present in the destination environment. Even if the required vocabularies were previously deployed to the destination environment, if their associated policy was deleted, they would have been deleted as well. This is because when you delete a policy, all of its vocabularies that are not being used by another policy are deleted.  
  
-   You can then import the policy or policies into a different BizTalk group or an application in a different BizTalk group, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).  
  
-   Before you can export a policy, it must exist in the Rule Engine database for the BizTalk group. There are several ways to import a policy into the Rule Engine database, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).  
  
    > [!NOTE]
    >  When you remove a policy from the Rule Engine database by using the Rule Engine Deployment Wizard, it will still display in the administration console, but you will not be able to export it. For more information about the Rule Engine Deployment Wizard, see [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
-   When you use the administration console for exporting, the policies and vocabularies are exported into an .xml file. When you use the BTSTask command-line tool for exporting, the policies and vocabularies are exported into an application .msi file.  
  
-   BTSTask does not provide a specific command for exporting policies; however you can use the ExportApp command of BTSTask to selectively export only the policies you want, and no other artifacts. This generates an application .msi file containing the policies. You can use the ImportApp command to import the .msi file into a different BizTalk group.  
  
## Prerequisites  
 The following are prerequisites for performing the procedures in this topic:  
  
-   You must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
-   The Business Rule Engine must be installed. For more information, see [Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5).  
  
-   The policy that you want to export must exist in the Rule Engine database for the BizTalk group. If you want to export the policy from an application, it must have also been added to the application as well.  
  
## To export a policy  
  
#### Using the BizTalk Server Administration console  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration** and expand the BizTalk group.  
  
3. If you want to select the policies to export from all of the policies in a BizTalk group right-click the **Applications** folder, click **Export**, and then click **Policies**.  
  
    OR  
  
    If you want to export the policies in a particular application, expand the Applications folder, right-click the application, click **Export**, and then click **Policies**.  
  
    OR  
  
    If you want to export only a particular policy, click the Policies folder that contains the policy, right-click the policy, and then click **Export**.  
  
4. On the Export Policies page, in **Policies to export**, select the policies to export.  
  
5. In **Vocabularies to export**, select the check boxes of the vocabularies to export, and clear the checkboxes of any vocabularies you do not want to export. The vocabularies used by this policy are automatically selected.  
  
6. In **File to export** into, type the path of the XML file to which to export the policy or policies, and then click **OK**.  
  
#### Using the command line  
  
1.  Use the BTSTask ListApp command with the /ResourceSpec option to generate an XML file that lists the artifacts in the BizTalk application from which you want to export a policy, as described in [ListApp Command](../core/listapp-command.md).  
  
2.  Edit the XML file generated in the previous step, deleting all of the artifacts except for the policy or policies that you want to export.  
  
3.  Use the BTSTask ExportApp command, and specify the modified XML file for the /ResourceSpec parameter. For more information, see [ExportApp Command](../core/exportapp-command.md).  
  
     BTSTask exports the specified policies and all of their associated vocabularies into an application .msi file.  
  
## See Also  
 [Exporting BizTalk Applications, Bindings, and Policies](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [Managing Policies](../core/managing-policies.md)