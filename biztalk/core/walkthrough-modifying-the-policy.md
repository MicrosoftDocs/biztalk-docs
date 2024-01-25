---
description: "Learn more about: Walkthrough: Modifying the Policy"
title: "Walkthrough: Modifying the Policy"
ms.custom: ""
ms.date: "04/05/2016"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Walkthrough: Modifying the Policy
This walkthrough provides step-by-step instructions for creating a new version of the **POVocabulary**, creating a new version of the **ProcessPurchaseOrder** policy, and using the latest version of the **POVocabulary** in the new version of the **ProcessPurchaseOrder** policy.  
  
## Prerequisites  
 You must complete the [Walkthrough: Adding a Rule to the Policy](../core/walkthrough-adding-a-rule-to-the-policy.md) walkthrough before performing this walkthrough.  
  
## Overview of This Walkthrough  
 This walkthrough contains three procedures, as described in the following table.  
  
|Procedure title|Procedure description|  
|---------------------|---------------------------|  
|To modify the POVocabulary vocabulary|Provides step-by-step instructions for creating a new vocabulary version to modify the value of **Maximum number of items allowed** from **500** to **1000**.|  
|To modify the ProcessPurchaseOrder policy to use the updated vocabulary|Provides step-by-step instructions for creating a new version of the **ProcessPurchaseOrder** policy to use the new version of **POVocabulary**.|  
|To test the solution|Provides step-by-step instructions for testing the solution and verifying that the new policy is in effect.|  
  
### To modify the POVocabulary vocabulary  
  
1.  On the **Start** menu, open **Business Rule Composer**. If you have Business Rule Composer already open, press F5 or click **Reload** on the **File** menu to refresh it.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  In the Facts Explorer window, expand **Vocabularies**, and then expand **POVocabulary**.  
  
3.  Right-click **Version 1.0 - Published**, and then click **Copy**.  
  
4.  Right-click **POVocabulary**, and then click **Paste Vocabulary Version**.  
  
5.  Double-click **Maximum Number of Items Allowed** in **Version 1.1 (not saved)** to start the Vocabulary Definition Wizard.  
  
6.  Click **Next**.  
  
7.  Click **Next**.  
  
8.  Change the value from **500** to **1000**.  
  
9. Click **Finish**.  
  
10. Right-click **Version 1.1 (not saved)**, and then click **Save**.  
  
11. Right-click **Version 1.1**, and then click **Publish**.  
  
### To modify the ProcessPurchaseOrder policy to use the updated vocabulary  
  
1.  In Policy Explorer, expand **Policies**, and then expand **ProcessPurchaseOrder**.  
  
2.  Right-click **Version 1.2**, and then click **Copy**.  
  
3.  Right-click **ProcessPurchaseOrder**, and then click **PastePolicyVersion**.  
  
4.  Click **ApprovalRule** in **Version 1.3 (not saved)**.  
  
5.  In Facts Explorer, expand **Vocabularies**, expand **POVocabulary**, and then expand **Version 1.1 - Published**.  
  
6.  Drag **Maximum Number of Items Allowed** in **Version 1.1 - Published** to replace **Maximum Number of Items Allowed** of version 1.0 in the IF pane.  
  
7.  Repeat steps 4-6 with **DeniedRule**.  
  
8.  Right-click **Version 1.3 (not saved)**, and then click **Save**.  
  
9. Right-click **Version 1.3**, and then click **Publish**.  
  
10. Right-click **Version 1.3**, and then click **Deploy**.  
  
### To test the solution  
  
1.  Click **Start**, open **BizTalk Server Administration**. If you have the BizTalk Server Administration console already open, press F5 to refresh it.  
  
2.  Right-click **RuleTestApp**, and then click **Start**. If **Start** is disabled, the application is already running and you can ignore the next step.  
  
3.  Click **Start**.  
  
4.  Copy the **SamplePO2.xml** file from the C:\BRE-Walkthroughs directory to the C:\BRE-Walkthroughs\RuleTestSol\Input directory for the orchestration.  
  
5.  You should see an output file in the C:\BRE-Walkthroughs\RuleTestSol\Output directory. Open the output XML file and notice that the value of the **Status** field is set to **Approved**.  
  
    > [!NOTE]
    >  The value of the **Quantity** field in SamplePO2.xml is 700. Version 1.3 of the **ProcessPurchaseOrder** policy compares this value with 1000 instead of comparing it with 500 as version 1.2 did.  
  
## Comments  
  
-   A published policy cannot be modified. You must create a new version of the policy to modify it. Similarly, a published vocabulary cannot be modified. You must create a new version of the vocabulary to modify it.  
  
-   The orchestration invoking a policy by using the **Call Rules** shape uses the latest deployed version of the policy. For example, if you have versions 1.0, 1.1, 1.2, and 1.3 of the policy deployed, the orchestration uses version 1.3. If version 1.3 is not deployed and version 1.2 is deployed, the orchestration uses version 1.2. Therefore if you want to switch back to using version 1.2, you just need to undeploy version 1.3, and make sure that version 1.2 is deployed.  
  
-   To use a specific version of a policy from an orchestration, you should use an **Expression** shape and invoke the rule engine to execute the policy programmatically by using the **Policy.Execute** method.  
  
-   Note that version 1.3 of the policy uses the vocabulary definitions from both version 1.0 and version 1.1 of the POVocabulary vocabulary. If you export version 1.3 of the policy to an XML file, and import it to create the policy on a different computer, the import process looks for both versions of the vocabulary. Therefore you need to export both version 1.0 and version 1.1 of the vocabulary and import them before importing version 1.3 of the policy.  
  
-   After you deploy a newer version of the policy, you should wait approximately 60 seconds before testing the solution. The rule engine update service looks for any updates to a policy every 60 seconds (1 minute) by default. If there are updates, it refreshes the cache with the updated information.  
  
## Next Steps  
  
-   Now that you have completed this walkthrough, perform the [Walkthrough: Tracking Policy Execution](../core/walkthrough-tracking-policy-execution.md) walkthrough, which gives you step-by-step instructions for tracking policy execution details.
