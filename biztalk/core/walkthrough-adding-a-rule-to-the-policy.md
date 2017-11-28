---
title: "Walkthrough: Adding a Rule to the Policy | Microsoft Docs"
ms.custom: ""
ms.date: "2016-04-05"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b2a682c0-a5d7-4550-924d-be9fa29b84d2
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Adding a Rule to the Policy
This walkthrough provides step-by-step procedures for adding a rule named **DeniedRule** to the **ProcessPurchaseOrder** policy.  
  
## Prerequisites  
 You must complete the [Walkthrough: Creating and Using a Vocabulary in the Policy](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md) walkthrough before performing this walkthrough.  
  
## Overview of This Walkthrough  
 This walkthrough contains three procedures, as described in the following table.  
  
|Procedure title|Procedure description|  
|---------------------|---------------------------|  
|To add DeniedRule to the ProcessPurchaseOrder policy|Provides step-by-step instructions for adding a new rule named **DeniedRule** to the **ProcessPurchaseOrder** policy. The **DeniedRule** rule sets the value of the **Status** field to **Denied** if the value of the **Quantity** is greater than 500.|  
|To test with Business Rule Composer|Provides step-by-step instructions for testing the **ProcessPurchaseOrder** policy by using Business Rule Composer.|  
|To test the solution|Provides step-by-step instructions for testing the solution.|  
  
### To add DeniedRule to the ProcessPurchaseOrder policy  
  
1.  On the **Start** menu, open **Business Rule Composer**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges. To do this, right-click the application, and then select **Run as administrator**.  
  
2.  In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.1**, and then click **Copy**.  
  
3.  Right-click **ProcessPurchaseOrder**, and then click **Paste Policy Version**.  
  
4.  Right-click **Version 1.2(not saved)**, click **Add New Rule**, and then change the name of the rule to **DeniedRule**.  
  
5.  If you forgot to change the name of the rule to **DeniedRule** in step 4, click **Rule1**, and change the name to **DeniedRule** in the Properties window.  
  
6.  In the IF pane, right-click **Conditions**, point to **Predicates**, and then click **Greater Than**.  
  
7.  In the Facts Explorer window, click the **Vocabularies** tab.  
  
8.  Expand **Vocabularies**, expand **POVocabulary**, expand **Version 1.0 - Published**, and then drag **Request Quantity** to **argument1** in the IF pane.  
  
9. Drag **Maximum number of items allowed** to **argument2** in the IF pane.  
  
10. Drag **Request Status** to the THEN pane.  
  
11. Click **\<empty string\>** and then type **Denied**.  
  
12. Right-click **Version 1.2 (not saved)**, and then click **Save**.  
  
13. Right-click **Version 1.2**, and then click **Publish**.  
  
14. Right-click **Version 1.2**, and then click **Deploy**.  
  
### To test with Business Rule Composer  
  
1.  Open the SamplePO.xml and SamplePO2.xml files in Notepad and change the value of the **Status** field to **XYZ**.  
  
2.  In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.2**, and then click **Test Policy**.  
  
3.  Under the **XMLDocuments** node, select **RuleTest.PO**, and then click **Add Instance**.  
  
4.  Select **SamplePO.xml**, and then click **Open**.  
  
5.  Click **Test**.  
  
6.  Look at the **Agenda Update** section in the output, and notice that only **ApprovalRule** is added to the agenda. Therefore it is the only rule that fires (actions associated with the rule are executed).  
  
7.  Open **SamplePO.xml** in Notepad and notice that the value of the **Status** field is set to **Approved**.  
  
8.  In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.2**, and then click **Test Policy.**  
  
9. Select **SamplePO.xml**, click **Remove instance**, and then click **Add Instance**.  
  
10. Select **SamplePO2.xml**, and then click **Open**.  
  
11. Click **Test**.  
  
12. Look at the **Agenda Update** section in the output, and notice that only **DeniedRule** is added to the agenda. Therefore it is the only rule that fires.  
  
13. Open **SamplePO2.xml** in Notepad and notice that the value of the **Status** field is **Denied**.  
  
### To test the solution  
  
1.  Open **SamplePO.xml** and **SamplePO2.xml** in Notepad and change the value of the **Status** field to **XYZ**.  
  
2.  Copy the **SamplePO.xml** file from the C:\BRE-Walkthroughs directory to the C:\BRE-Walkthroughs\RuleTestSol\Input directory for the orchestration.  
  
3.  You should see an output file in the C:\BRE-Walkthroughs\RuleTestSol\Output directory for the orchestration. Open the output XML file and notice that the value of the **Status** field is set to **Approved**.  
  
4.  Repeat steps 2 and 3 with **SamplePO2.xml**, and notice that the value of the **Status** field is set to **Denied** in the output document. This proves that the orchestration is using version 1.2 of the **ProcessPurchaseOrder** policy. The orchestration uses the latest deployed version of the **ProcessPurchaseOrder** policy, which is **1.2**. You do not need to undeploy version 1.1 of the policy to use version 1.2 of the policy. However, you need to wait for approximately 60 seconds before testing the solution. For more information, see the Comments section.  
  
## Comments  
  
-   A policy can have one or more rules. There is no logical limit on the number of rules in a policy.  
  
-   The rule engine uses a Condition Evaluation - Conflict Resolution - Action Execution algorithm. In the **Condition Evaluation** stage, the rule engine evaluates conditions in all the rules. The rules whose conditions evaluate to true become candidate rules for execution. In the **Conflict Resolution** stage, the candidate rules are added to the agenda in the order of the priority of the rule. In the **Action Execution** stage, the actions in the candidate rules are executed. If candidate rules have the same priority, there is no deterministic order in which the actions for those rules are executed. You should assume that they are executed in parallel.  
  
-   In this scenario, for any given sample file, only one of the rules is fired. Make sure that you change the value of the **Status** field before running a test.  
  
-   When a new version of the policy is deployed, you should wait approximately 60 seconds before testing. The rule engine update service polls the rule engine database on a periodic basis (every 60 seconds by default) to look for newly deployed policies. The rule engine update service updates the policy object in memory with the information about the latest deployed version of the policy from the rule engine database.  
  
## Next Steps  
 Now that you have completed this walkthrough, perform the [Walkthrough: Modifying the Policy](../core/walkthrough-modifying-the-policy.md) walkthrough, which gives you step-by-step instructions for modifying the policy to approve purchase orders with the value of **quantity** less than or equal to 1000 (instead of 500).  
  
## See Also  
 [Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md)   
 [Agenda and Priority](../core/agenda-and-priority.md)