---
title: "Lesson 1: Deploying the Related Business Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "business rules, deploying"
  - "deploying, business rules"
ms.assetid: f8f5b103-4b66-4836-8165-99692574961a
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Lesson 1: Deploying the Related Business Rules
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes a program in the A4SWIFT Software Development Kit (SDK) called the Business Rule Engine (BRE) Deployment Utility. In this lesson, you use this utility to inspect an assembly for deployed schemas, determine the required rules, and deploy the necessary vocabularies and policies for each schema.  
  
 You can also deploy rules by using the SWIFT Standards Release Guides (SRG) to identify the necessary rules and then use the Business Rule Composer tool to deploy the vocabularies and policies.  
  
### To deploy the related business rules  
  
1. Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for SWIFT**, and then click **BRE Deployment Utility**.  
  
2. In the BRE Deployment Utility dialog box, click **Browse**.  
  
3. In the .NET Global Assembly Cache dialog box, select **SWIFTSchemas**, and then click **OK**.  
  
   > [!NOTE]
   >  SWIFTSchemas refers to the assembly you previously deployed.  
  
4. Click **Deploy**.  
  
    Based on the schemas you deployed with that assembly, the deployment utility identifies the related rules and publishes them for use with the BRE. When complete, the BRE Deployment Utility displays the following message:  
  
    **Deployment has completed. View the log file or Business Rules Composer for details.**  
  
5. Close the SWIFT BRE Deployment Utility dialog box.  
  
6. In Windows Explorer, browse to \<*drive*\>:\Documents and Settings\All Users\Application Data to confirm that the log file **BREDeploymentLog.txt** appears in the folder.  
  
   > [!NOTE]
   >  You can open the log file using a text editor to confirm each of the deployment steps.  
  
7. Restart the Rule Engine Update Service. Do so by clicking **Start**, clicking **Run**, entering **services.msc**, and clicking **OK**. In the **Services (Local)** window, right-click **Rule Engine Update Service**, and then click **Restart**.  
  
   Proceed to [Lesson 2: Confirming the Deployment Using the Business Rule Composer Tool](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md).