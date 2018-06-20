---
title: "How to Deploy or Undeploy a Policy | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "managing [policies], undeploying"
  - "deploying, policies"
  - "policies, deploying"
  - "managing [policies], deploying"
  - "policies, undeploying"
  - "undeploying, policies"
ms.assetid: 9d26d4fe-9673-4baa-9927-02efda56b7a4
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Deploy or Undeploy a Policy
This topic describes how to use the BizTalk Server Administration console to deploy or undeploy a policy manually. In addition, starting an application automatically deploys any policies it contains, and stopping an application automatically undeploys its policies. Deploying a policy puts it into effect in the application that uses it. Undeploying a policy makes it inactive so that it no longer functions in any application that uses it in the BizTalk group.  
  
 When deploying or undeploying a policy, bear in mind the following important points:  
  
-   Before you can deploy a policy, it must exist in the Rule Engine database for the BizTalk group. If you import an application that contains a policy, the policy is automatically imported into the Rule Engine database, or you can explicitly import a policy into the Rule Engine database by using the administration console or BTSTask, as described in [How to Import a Policy](../core/how-to-import-a-policy.md). Alternatively, you can add a policy to the Rule Engine database by using the Rule Engine Deployment Wizard, as described in [How to Deploy and Undeploy Policies and Vocabularies](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md).  
  
-   Before you can deploy a policy, it must be published, as described in [How to Publish a Policy](../core/how-to-publish-a-policy.md).  
  
-   A deployed policy cannot be modified. If you want to modify a deployed policy, you must first undeploy it.  
  
## Prerequisites  
 To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group. For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
### To deploy or undeploy a policy  
  
1. Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  
  
2. In the console tree, expand **BizTalk Server Administration**, expand the BizTalk group containing the policy that you want to deploy or undeploy, and then expand **\<All Artifacts\>**.  
  
3. Click **Policies**, right-click the policy, and then click **Deploy** or **Undeploy**.  
  
## See Also  
 [Managing Policies](../core/managing-policies.md)   
 [How to Start and Stop a BizTalk Application](../core/how-to-start-and-stop-a-biztalk-application.md)