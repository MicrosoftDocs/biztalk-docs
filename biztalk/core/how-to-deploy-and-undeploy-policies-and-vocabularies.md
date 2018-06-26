---
title: "How to Deploy and Undeploy Policies and Vocabularies | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, policies"
  - "policies, deploying"
  - "deploying, vocabularies"
  - "policies, undeploying"
  - "vocabularies, deploying"
ms.assetid: 9a7e3310-54b7-482c-8210-b4b11fde4c49
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Deploy and Undeploy Policies and Vocabularies
You can use the Rule Engine Deployment Wizard to deploy or undeploy a policy.  
  
 In the Rule Engine Deployment Wizard, when you try to deploy, only published policy versions are shown in the drop-down list. When you try to undeploy, only deployed policy versions are shown in the drop-down list.  
  
### To deploy or undeploy a policy  
  
1. Click **Start**, point to **Program Files**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **Business Rules Engine Deployment Wizard**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2. On the **Rules Engine Deployment Wizard** welcome page, click **Next**.  
  
3. Select either **Deploy Policy** or **Undeploy Policy**, and then click **Next**.  
  
4. From the drop-down lists, select an available SQL Server computer and database, and then click **Next**.  
  
   > [!NOTE]
   >  You can only deploy to the rule store database that you are configured against. An attempt to deploy to a different DB will give an error.  
  
5. From the drop-down list, select a policy, and then click **Next**.  
  
   > [!NOTE]
   >  When you try to deploy, only published policy versions are shown in the drop-down list. When you try to undeploy, only deployed policy versions are shown in the drop-down list.  
  
6. Review the server, database, and policy information, and then click **Next**.  
  
7. Watch the progress of the deployment or undeployment. When it is finished, click **Next**.  
  
8. Review the completion status of the deployment or undeployment, and then click **Finish**.  
  
> [!NOTE]
>  You can also deploy or undeploy a policy version from within the Business Rule Composer by right-clicking the policy version and then clicking **Deploy** or **Undeploy**.