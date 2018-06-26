---
title: "How to Publish a Policy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "policies, publishing"
  - "managing [policies], publishing"
  - "publishing, policies"
ms.assetid: 730c57a7-526f-40ca-8610-88216558e375
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Publish a Policy
This topic describes how to use the BizTalk Server Administration console to publish a policy in a BizTalk group. Publishing a policy makes it available to add to a BizTalk application, as described in [How to Add a Policy to an Application](../core/how-to-add-a-policy-to-an-application.md).  
  
 Before you can publish a policy, it must exist in the Rule Engine database for the BizTalk group. There are three ways to import a policy into the Rule Engine database:  
  
-   You can import an application that contains a policy. When you do this, the policy is automatically imported into the Rule Engine database.  
  
-   You can explicitly import a policy into the Rule Engine database by using the administration console or BTSTask, as described in [How to Import a Policy](../core/how-to-import-a-policy.md).  
  
-   You can add a policy to the Rule Engine database by using the Rule Engine Deployment Wizard, as described in [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
> [!NOTE]
>  While a published policy can be overwritten by another policy that you import, should you specify this option, a published vocabulary can never be overwritten. To update a published vocabulary, you must remove it from the Rule Engine database and then import the new version.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To publish a policy  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the policy to publish, expand **Applications**, and then expand **\<All Artifacts\>**.  
  
3. Click **Policies**, right-click the policy, and then click **Publish**.  
  
   > [!NOTE]
   >  In order to publish a policy, any assemblies that are referenced by the policy must be installed in the Global Assembly Cache (GAC) of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer before you open **BizTalk Server Administration**. When **BizTalk Server Administration** is opened, it maintains a cache of the assemblies that are installed into the GAC. This cache is not updated until **BizTalk Server Administration** is closed and reopened. If you attempt to publish a policy and publication fails because a referenced assembly is not installed in the GAC you must close **BizTalk Server Administration**, install the referenced assembly into the GAC, open **BizTalk Server Administration**, and then publish the policy.  
  
## See Also  
 [Managing Policies](../core/managing-policies.md)