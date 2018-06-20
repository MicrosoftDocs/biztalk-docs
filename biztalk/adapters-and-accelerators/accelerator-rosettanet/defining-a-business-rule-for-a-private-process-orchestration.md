---
title: "Defining a Business Rule for a Private Process Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, policies"
  - "vocabularies, saving"
  - "private processes, orchestrations"
  - "business rules, private processes"
  - "creating, vocabularies"
  - "vocabularies, business rules"
  - "business rules, vocabularies"
  - "policies, deploying"
  - "vocabularies, creating"
  - "orchestrations, private-process orchestrations"
  - "private processes, customizing"
  - "policies, publishing"
  - "business rules, Set elements"
  - "creating, policies"
  - "customizing private processes"
  - "Set elements"
  - "business rules, orchestrations"
  - "publishing, vocabularies"
  - "vocabularies, publishing"
  - "creating, rules"
  - "business rules, Get elements"
  - "policies, saving"
  - "publishing, policies"
  - "Get elements"
  - "orchestrations, business rules"
  - "rules"
  - "private processes, business rules"
  - "policies, creating"
ms.assetid: 5d2b0257-1b15-482b-a562-798b808e9a2d
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Defining a Business Rule for a Private Process Orchestration
You can define a business rule for use in an acknowledgement private process. This lets you to modify the business rule dynamically without stopping the private-process orchestration. This process uses the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Business Rule Engine. This process involves the following steps:  
  
1. Adding a new vocabulary. This involves defining at least one vocabulary constant value. This sets a business-rule threshold. It also involves defining XML document `Get` and `Set` elements. This establishes how [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] uses the threshold.  
  
2. Adding a new policy. This involves creating a policy, creating a set of rules, and then saving, publishing, and deploying the policy.  
  
3. Calling the business rule from the private-process orchestration. This involves adding a **Call Rules** shape to the orchestration.  
  
   The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes a sample [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] business policy, samplebtarnpolicy.xml, in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4. For more information, see [Sample BTARN Business Policy](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md).  
  
   PIP3A4PrivateResponder.odx orchestration is a sample private-process orchestration that demonstrates how to implement a Partner Interface Process (PIP)-specific responder private process incorporating a business rule. For more information about this sample, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).  
  
   For more information about vocabularies and policies, see the "Developing with Business Rules" topic in BizTalk Server.  
  
### To add a new vocabulary  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**.  
  
2. If the **Open Rule Store** dialog box opens, select the **BizTalk Rule Engine** database that you set up on the current server, and then click **OK**.  
  
3. In [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Business Rule Composer, in the Facts Explorer pane, right-click **Vocabularies**, and then click **Add New Vocabulary**.  
  
4. In the Property pane (lower left), set the **Name** property to the name of the appropriate vocabulary, and then press **Enter**.  
  
5. Expand the vocabulary folder you just created, right-click **Version 1.0 (not saved)**, and then click **Add New Definition**.  
  
6. On the **Vocabulary Definition Wizard** page, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.  
  
7. On the **Constant Value, Range of Values, or Set of Values** page, in the **Definition Name** box, type the name of the appropriate vocabulary constant value, such as **Maximum Quantity Allowed**, and then click **Next**.  
  
8. On the **Define a Constant Value** page, in the **Value Field** box, type the threshold, and then click **Finish**.  
  
### To define Get and Set elements  
  
1.  In Business Rule Composer, in the Facts Explorer pane, under the vocabulary folder created in the "To add a new vocabulary procedure", right-click **Version 1.0 (not saved)**, and then click **Add New Definition**.  
  
2.  On the **Vocabulary Definition Wizard** page, select **XML Document Element or Attribute**, and then click **Next**.  
  
3.  On the **XML Document Element or Attribute** page, in the Definition Name text box, type a name for a **Get** element.  
  
4.  Click **Browse**, move to the location of the schema that you want to use, select the schema file, and then click **Open**.  
  
5.  If the **Select Root Node** page opens, select the root node to browse.  
  
6.  On the **Select Binding** page, move to the field for which you want to define the threshold, and then click **OK**.  
  
7.  In the **Document Type** box, type the name of the document.  
  
8.  In the **Operation Type** section, select **Perform “Get” operation**.  
  
9. Click **Finish**.  
  
10. Repeat these steps to define one or more `Set` operations, select **Perform “Set” operation** for the **Operation Type**.  
  
### To save and publish the vocabulary  
  
1.  In Business Rule Composer, in the Facts Explorer pane, under the vocabulary folder that you created, right-click **Version 1.0 (not saved)**, and then click **Save**.  
  
2.  In the Facts Explorer pane, under the 3A4PurchaseOrderVocabulary folder, right-click **Version 1.0**, and then select **Publish**.  
  
### To add a new policy and rules  
  
1.  In Business Rule Composer, in the Policy Explorer pane, right-click **Policies**, and then click **Add New Policy**.  
  
2.  Click **Policy1**.  
  
3.  In the Property pane, set the **Name** property to the appropriate policy name.  
  
4.  In the Policy Explorer pane, under the folder for the new policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.  
  
5.  Click **Rule1**.  
  
6.  In the Property pane, set the **Name** property to the rule name you want, and then press **Enter**.  
  
7.  In the Rule Composer, under the **IF** pane, right-click **Conditions**, and then select a logical condition, if appropriate.  
  
8.  In the Facts Explorer pane, under **Vocabularies**, expand **Predicates**, expand **Version 1.0 - Published**, select the predicate you want, drag it to the composer surface, and then drop it on **Conditions** or the logical operator.  
  
9. In the Facts Explorer pane, under the Vocabularies folder, expand the vocabulary that you created, expand **Version 1.0 - Published**, select a `Get` or `Set` element, drag it to the composer surface, and drop it on **argument1**.  
  
10. Under the vocabulary folder, select a `Get` or `Set` element, drag it to the composer surface and drop it on **argument2**.  
  
11. Under the vocabulary folder, select a `Set` element, drag it to the composer surface, and drop it in the **Actions** box in the THEN pane.  
  
12. If a variable is associated with the `Set` element, click the variable, make changes as appropriate, and then press **Enter**. If appropriate, repeat with other `Set` elements.  
  
### To save, publish, and deploy the policy  
  
1.  When you have finished defining the rules, in Business Rule Composer, in the Policy Explorer pane, under the policy folder that you created, right-click **Version 1.0 (not saved)**, and then click **Save**.  
  
2.  In the Policy Explorer pane, under the policy folder that you created, right-click **Version 1.0**, and then click **Publish**.  
  
3.  In the Policy Explorer pane, under the policy folder that you created, right-click **Version 1.0**, and then click **Deploy**.  
  
### To call the business rule from the orchestration  
  
1.  Start **Microsoft Visual Studio 2012**.  
  
2.  On the **File** menu, point to Open, and then click **Project/Solution**.  
  
3.  Locate the solution that contains the orchestration that you must call the business rule from, and then click **Open**.  
  
4.  Click **View**, point to **Other Windows**, and then click **Orchestration View**.  
  
5.  Expand **Variables**. Make sure that the orchestration variable list contains a variable that corresponds to each parameter in the business policy that you call from the orchestration. Make sure that the variable has the same type as the policy parameter. If the list does not contain an orchestration variable for each policy parameter, right-click **Variables**, and then click **New Variable**. In Orchestration View, type a variable name, and then in the Properties window, enter the type of the parameter.  
  
6.  From the **Toolbox**, drag a **Call Rules** shape to the orchestration design surface, and then drop it under the **Receive** shape.  
  
7.  Double-click the **Call Rules** shape.  
  
8.  In the **Select the business policy you wish to call** box, select the business policy from the drop-down list.  
  
9. For the first parameter shown, for **Parameter Name**, select a name from the drop-down list.  
  
    > [!NOTE]
    >  BTARN populates the **Policy Parameter** list with all the parameters in the business policy. For each parameter in the list, BTARN enters a value in **Parameter Type** from the business policy. In the drop-down list associated with **Parameter Name**, BTARN enters the names of all variables from the orchestration's variable list that has the same type as the policy parameters. By selecting an orchestration variable, you are associating that variable with the policy parameter. You can view the orchestration variables in Orchestration View.  
  
10. Repeat step 9 for all other parameters.  
  
11. In the Orchestration Design window, enter all the additional shapes required for the processing associated with the business policy, including adding a **Decision** shape under the **Call Rules** shape.  
  
    > [!NOTE]
    >  For an example of how to use a **Call Rules** shape in an orchestration, see the PIP3A4PrivateResponder.odx orchestration included in the BTARN SDK. It is located at \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR. For more information, see [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).  
  
12. Click **OK**.  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)   
 [Sample BTARN Business Policy](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md)   
 [3A4 Private Responder Orchestration Using a Business Rule](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)