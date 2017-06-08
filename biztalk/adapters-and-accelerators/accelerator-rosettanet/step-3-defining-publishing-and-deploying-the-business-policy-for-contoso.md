---
title: "Step 3: Defining, Publishing, and Deploying the Business Policy for Contoso | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "policies, deploying"
  - "policies, publishing"
  - "private process tutorial, creating policies"
  - "policies, creating"
ms.assetid: 529b16d8-226b-4046-a95d-64162ebd59a3
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Defining, Publishing, and Deploying the Business Policy for Contoso
In this step, you create a business policy that reserves a set quantity of units for each product that Contoso manufactures to be used in case of an emergency.  
  
### To add a new policy  
  
1.  In the Business Rule Composer, in the Policy Explorer pane, right-click **Policies**, and then click **Add New Policy**.  
  
2.  Name the new policy **3A2PriceAvailabilityPolicy**, and then press **Enter**.  
  
### To add a policy rule to enforce the emergency quantity needs  
  
1.  Right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityPolicy**, and then click **Add New Rule**.  
  
2.  Name the rule **Emergency Supply Rule - Quantity Exhausted**, and then press **Enter**.  
  
3.  In the Business Rule Composer, in the right pane, right-click **Conditions** under the IF pane, point to **Predicates**, and then click the **Less than equal** predicate.  
  
4.  In the Facts Explorer pane, expand **Vocabularies**, expand **3A2PriceAvailabilityVocabulary**, expand **Version 1.0 - Published**, select **Quantity Available**, and drag it onto the `argument1` placeholder on the composer surface.  
  
5.  Repeat step 4 by dragging **Emergency Quantity Needed** onto the `argument2` placeholder.  
  
6.  Select **Final Quantity Available**, and then drag it onto **Actions** in the THEN pane.  
  
### To add a policy to revise the Number Available field in the response  
  
1.  Right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityPolicy**, and then click **Add New Rule**.  
  
2.  Name the new rule **Emergency Supply Rule - Quantity Available**, and then press **Enter**.  
  
3.  In the Business Rule Composer, in the right pane, right click **Conditions** under the IF pane, point to **Predicates**, and then click the **Greater than** predicate.  
  
4.  In the Facts Explorer pane, expand **Vocabularies**, expand **3A2PriceAvailabilityVocabulary**, expand **Version 1.0 - Published**, select **Quantity Available**, and then drag it onto the `argument1` placeholder on the composer surface.  
  
5.  Repeat that same step by dragging **Emergency Quantity Needed** onto the `argument2` placeholder.  
  
6.  Select **Final Quantity Available**, and then drag it onto **Actions** in the THEN pane.  
  
7.  In the Facts Explorer pane, expand **Version 1.0 - Published** under **Functions**, and drag the `Subtract` function onto the **0** argument next to **Final Quantity Available** in the THEN pane.  
  
8.  Drag **Quantity Available** (under **3A2PriceAvailabilityVocabulary**) and drop it on the `value1` placeholder in the THEN pane.  
  
9. Drag **Emergency Quantity Needed**, and drop it on the `value2` placeholder in the THEN pane.  
  
### To save, publish, and deploy the business policy  
  
1.  In the Policy Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityPolicy**, and then click **Save**.  
  
2.  Right-click that same node, and then click **Publish**.  
  
3.  Right-click that same node, and then click **Deploy**.  
  
## See Also  
 [Step 4: Creating the HeaderHelper Project](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-headerhelper-project.md)