---
title: "Deploying BRE Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, BRE policies"
  - "BRE policies, deploying"
ms.assetid: 3a66aa57-e7f9-400f-963c-eda12fb1e659
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploying BRE Rules
You must deploy the BRE rules used by [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] orchestrations to process SWIFT messages.  

 **Summary**  

 Publish the following vocabularies:  

- A4SWIFT_CodeLists.xml and A4SWIFT_Functions.xml vocabularies. These are located in *\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies\Vocabulary. Publish and deploy these using the BRE Deployment Utility.  

  Publish and deploy the following policies:  

- SWIFT base policies for message schema, including SWIFT_Reference_Policy.xml, SWIFT_PartyIdentifier_Policy.xml, and network rule policies (SWIFT_NetworkRulexxx_Policy.xml) for deployed schemas. These are located in \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies. Publish and deploy these using the BRE Deployment Utility.  

- Master and validation policies associated with deployed message schemas (MTxxx_Master_Policy.xml and MTxxx_Validation_Policy.xml). These are located in \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MTxxx. Publish and deploy these using the BRE Deployment Utility.  

- Master and validation policies associated with BIC validation (BIC_Master_Policy.xml and BIC_Validation_Policy.xml), if BIC validation is required. These are located in \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies. Before publishing and deploying these policies, you must customize BIC_Master_Policy.xml with the names of the SQL Server, the BIC database name, and integrated security value. For more information, see [Enabling Validation of Bank Identifier Codes](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md). Publish and deploy these using the Rules Engine Deployment Wizard.  

### To deploy BRE rules  

1.  Run the BRE Deployment Utility. For more information, see "Deploying BRE Rules All at Once" below. This utility will publish and deploy the following:  

    -   A4SWIFT_CodeLists.xml and A4SWIFT_Functions.xml vocabularies  

    -   SWIFT base policies for message schema, including SWIFT_Reference_Policy.xml, SWIFT_PartyIdentifier_Policy.xml, and network rule policies (SWIFT_NetworkRulexxx_Policy.xml)  

    -   Master and validation policies associated with deployed message schemas (MTxxx_Master_Policy.xml and MTxxx_Validation_Policy.xml)  

2.  Customize BIC_Master_Policy.xml with the names of the SQL server, the BIC database name, and integrated security value. For more information, see [Enabling Validation of Bank Identifier Codes](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md).  

3.  Run the Rules Engine Deployment Wizard to publish and deploy BIC_Master_Policy.xml and   BIC_Validation_Policy.xml (in \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies). For more information, see "Deploying BRE Rules One at a Time" below.  

## Tools for Deploying the Policies  
 The easiest way to publish the vocabularies and deploy the policies is by using the Business Rule Engine (BRE) Deployment Utility in the A4SWIFT Software Development Kit (SDK). You can also do so by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Rule Engine Deployment Wizard, which performs the same task one vocabulary or policy at a time.  

> [!NOTE]
>  The BRE Deployment Utility does not deploy the BIC Master Policy and BIC Validation Policy. You must deploy these using the Rule Engine Deployment wizard.  

### Deploying BRE Rules All at Once  
 The Business Rule Engine (BRE) Deployment Utility performs a series of publishing and deployment tasks in one step. You must rerun the deployment utility any time that you add a schema to your project.  

##### To deploy BRE rules using the BRE Deployment Utility  

1. Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Accelerator for SWIFT**, and then click **BRE Deployment Utility**.  

2. In the BRE Deployment Utility dialog box, click **Browse**.  

3. In the .NET Global Assembly Cache dialog box, select the project assembly that you deployed in [Deploying A4SWIFT Schemas](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md), and then click **OK**.  

4. In the BRE Deployment Utility dialog box, click **Deploy**.  

   > [!NOTE]
   >  Based on the schemas you deployed with that assembly, the deployment utility identifies the related rules and publishes them for use with the BRE. When complete, the BRE Deployment Utility displays the following message:  

   > [!NOTE]
   >  "Deployment has completed. View the log file or Business Rule Composer for details."  

5. Close the BRE Deployment Utility dialog box.  

6. Open [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer. Browse to \<*drive*\>:\Documents and Settings\All Users\Application Data, and confirm that the log file BREDeploymentLog.txt appears in that drive.  

7. Restart the Rule Engine Update Service. Do so by clicking **Start**, clicking **Run**, entering **services.msc**, and clicking **OK**. In the **Services (Local)** window, right-click **Rule Engine Update Service**, and then click **Restart**.  

### Deploying BRE Rules One at a Time  
 You can use the Rules Engine Deployment Wizard to publish vocabularies and deploy policies one at a time. For a vocabulary, this process involves importing and publishing the vocabulary to the database from a file in one step. For a policy, the process involves importing and publishing the policy in one step, and then deploying it in another step.  

##### To deploy BRE rules Using the Rules Engine Deployment Wizard  

1. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rules Engine Deployment Wizard**.  

2. On the Welcome to the Rules Engine Deployment Wizard page, click **Next**.  

3. On the Deployment Task page, click **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.  

4. On the Policy Store page, in the **SQL Server Name list**, select your server, and in the **Configuration Database on selected server** list, select **BizTalkRuleEngineDb**. Click **Next**.  

5. On the Import Rules Engine Policy/Vocabulary file page, click **Browse**.  

6. On the Import Policy from file page, in the **Look in** drop-down list, move to one of the following folders, depending upon the vocabulary or policy:  

   -   \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies\Vocabulary for A4SWIFT_CodeLists.xml and A4SWIFT_Functions.xml  

   -   \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Policies for SWIFT_Reference_Policy.xml, SWIFT_PartyIdentifier_Policy.xml, network rule policies, BIC_Master_Policy.xml, and BIC_Validation_Policy.xml  

   -   \<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MTxxx for the master and validation policies associated with deployed message schemas  

7. Select the policy that you want to deploy, and then click **Open**.  

8. On the Import Rules Engine Policy/Vocabulary file page, click **Next**.  

9. On the Ready page, click **Next**.  

10. On the Importing Policy/Vocabulary page, verify that the command succeeded, and then click **Next**.  

11. If you want to deploy a policy, on the Completing the Rules Engine Deployment Wizard page, click **Run this Wizard again**, and then click **Finish**.  

12. On the Welcome to the Rules Engine Deployment Wizard page, click **Next**.  

13. On the Deployment Task page, click **Deploy Policy**, and then click **Next**.  

14. On the Policy Store page, in the **SQL Server Name list**, select your server, and in the **Configuration Database on selected server** list, select **BizTalkRuleEngineDb**. Click **Next**.  

15. On the Deploy Policy page, click the down arrow next to the **Rules Engine Policy** text box, select the policy you just published, and then click **Next**.  

16. On the Ready page, click **Next**.  

17. On the **Importing Policy/Vocabulary** page, verify that the command succeeded, and then click **Next**.  

18. Click **Finish**.  

19. Restart the **Rule Engine Update Service**. Do so by clicking **Start**, clicking **Run**, entering **services.msc**, and clicking **OK**. In the **Services (Local)** window, right-click **Rule Engine Update Service**, and then click **Restart**.
