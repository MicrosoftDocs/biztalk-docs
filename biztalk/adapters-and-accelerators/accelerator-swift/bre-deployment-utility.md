---
title: "BRE Deployment Utility | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BRE Deployment utility"
  - "deploying, BRE Deployment utility"
ms.assetid: 5b04592c-ea1e-4ded-8ca4-dcd051d6375e
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BRE Deployment Utility
You can use the BRE Deployment Utility to publish and deploy the Business Rule Engine (BRE) vocabularies and policies required for a SWIFT schema. Publishing and deploying these vocabularies and policies is required to enable BRE validation for the message type.  
  
 You can also deploy business rules by using the SWIFT Standards Release Guides (SRGs) to identify the required rules, and then using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Business Rule Composer tool to deploy the vocabularies and policies. However, using the BRE Deployment Utility is much easier.  
  
 The BRE Deployment Utility accomplishes the following:  
  
- Examines the deployed assembly that you specify and determines the message schemas that you deployed for the assembly.  
  
- Publishes the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_CodeLists.xml and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Functions.xml vocabularies required for [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] business rules processing.  
  
- Publishes and deploys the SWIFT base policies (reference policy, party identifier policy, and network rule policies) associated with the message schemas.  
  
- Publishes and deploys the master policy and validation policy associated with each message schema.  
  
- Generates a log file that indicates all the steps that it takes. This file is BREDeploymentLog.txt in the \<*drive*\>:\Documents and Settings\All Users\Application Data folder.  
  
  > [!NOTE]
  >  The BRE Deployment Utility does not deploy the BIC Master Policy and BIC Validation Policy. You must deploy these using the Rule Engine Deployment wizard.  
  > 
  > [!NOTE]
  >  If you have installed [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] in a non-default directory (other than C:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]), or you are working on a 64-bit computer, the BRE Deployment Utility will not work correctly until you change the paths in the BREDeployment.exe.config file. This configuration file is located in the \<*drive*\>:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\SDK\Tools folder. To update the utility's configuration, open BREDeployment.exe.config in Notepad, and change the folders for the base policies, schemas, and vocabulary directories.  
  
  You can also use the deployment utility to reverse this process, undeploying and unpublishing the policies and vocabularies. The utility has both deploy and undeploy functionality.  
  
### To use the BRE Deployment Utility  
  
1.  Click **Start**, point to **Programs**, point to **Microsoft BizTalk Accelerator for SWIFT**, and then click **BRE Deployment Utility**.  
  
2.  In the BRE Deployment Utility, click **Browse**.  
  
3.  Select the deployed assembly or assemblies for which you want to publish and deploy vocabularies and policies, and then click **OK**.  
  
4.  Click **Deploy**.  
  
    > [!NOTE]
    >  Based on the schemas that you deployed with that assembly, the BRE Deployment Utility goes through the process of identifying the related rules and publishing them for use with the BRE. When complete, the BRE Deployment Utility displays the following message: **Deployment has completed**. Use the Business Rule Composer to verify successful deployment.  
  
    > [!NOTE]
    >  To undeploy the policies and vocabularies, click **Undeploy**. The undeploy process does not undeploy the A4SWIFT_CodeLists.xml and A4SWIFT_Functions.xml vocabularies, which might be used by other deployed policies.  
  
5.  Locate \<*drive*\>:\Documents and Settings\All Users\Application Data to confirm that the utility created the log file BREDeploymentLog.txt.  
  
    > [!NOTE]
    >  You can open the log file by using a text editor to confirm each deployment step.  
  
## See Also  
 [Tools](../../adapters-and-accelerators/accelerator-swift/tools.md)