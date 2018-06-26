---
title: "Step 2: Defining and Publishing the Vocabulary for Contoso | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "vocabularies, creating"
  - "vocabularies, publishing"
  - "private process tutorial, creating vocabularies"
ms.assetid: e23880c0-772c-48c6-a6b5-32eb951527c8
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Defining and Publishing the Vocabulary for Contoso
In this scenario, Contoso implements a business policy that makes sure that inventory is always on hand if an emergency occurs. You create business policies using the Business Rule Composer in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. In this step, you create the vocabulary to use when you define the business policy.  
  
### To add a new vocabulary  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**.  
  
2. In the Open Rule Store dialog box, click **OK**.  
  
3. In the Facts Explorer pane, on the **Vocabularies** tab, right-click **Vocabularies**, and then click **Add New Vocabulary**.  
  
4. Name the vocabulary **3A2PriceAvailabilityVocabulary**, and then press **Enter**.  
  
### To define a constant vocabulary value  
  
1.  In Business Rule Composer, click **3A2PriceAvailabilityVocabulary**, right-click **Version 1.0(not saved)**, and then click **Add New Definition**.  
  
2.  On the **Vocabulary Definition Wizard** page, select **Constant Value, Range of Values, or Set of Values**, and then click **Next**.  
  
3.  On the **Constant Value, Range of Values, or Set of Values** page, in the **Definition name** box, type **Emergency Quantity Needed**, and then click **Next**.  
  
4.  On the **Define a Constant Value** page, in the **Value** box, type **800**, and then click **Finish**.  
  
### To define an XML document 'Get' element  
  
1.  In Business Rule Composer, in the Facts Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityVocabulary**, and then click **Add New Definition**.  
  
2.  On the **VocabularyDefinition Wizard** page, select **XML Document Element or Attribute**, and then click **Next**.  
  
3.  On the **XML Document Element or Attribute** page, in the **Definition Name** box, type **Quantity Available**.  
  
4.  Click **Browse** (next to the **Schema** field), move to the **ContosoPriceAndAvailability** project in your solution folder, select the **ContosoPriceAndAvailability.xsd** schema, and then click **Open**.  
  
5.  In the Select Binding dialog box, expand **rootPriceResponse**, expand **Products**, select the **NumberAvailable** element, and then click **OK**.  
  
6.  On the **XML Document Element or Attribute** page, in the **Document Type** box, ensure that the value is **ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.  
  
7.  In the **Select operation** section, select **Perform "Get" Operation**, and then click **Finish**.  
  
### To define an XML document 'Set' element  
  
1.  In Business Rule Composer, in the Facts Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityVocabulary**, and then click **Add New Definition**.  
  
2.  On the **VocabularyDefinition Wizard** page, select **XML Document Element or Attribute**, and then click **Next**.  
  
3.  On the **XML Document Element or Attribute** page, in the **Definition Name** box, type **Final Quantity Available**.  
  
4.  Click **Browse** (next to the **Schema** field), move to the **ContosoPriceAndAvailability** project in your solution folder, select the **ContosoPriceAndAvailability.xsd** schema, and then click **Open**.  
  
5.  In the **Select Binding** dialog box, expand **rootPriceResponse**, expand **Products**, and then select the **NumberAvailable** element. Click **OK**.  
  
6.  On the **XML Document Element or Attribute** page, in the **Document Type** box, ensure that the value is **ContosoPriceAndAvailability.ContosoPriceSchema.rootPriceResponse**.  
  
7.  In the **Select operation** section, select **Perform "Set" Operation**, and then click **Next**.  
  
8.  In the **Specify the Display Name** page, click **Finish**.  
  
### To save and publish the vocabulary  
  
1.  In Business Rule Composer, in the Facts Explorer pane, right-click **Version 1.0 (not saved)** under **3A2PriceAvailabilityVocabulary**, and then click **Save**.  
  
2.  Right-click that same **Version 1.0** node and then click **Publish**.  
  
    > [!NOTE]
    >  Leave the Business Rule Composer open for the next step in the tutorial.  
  
## See Also  
 [Step 3: Defining, Publishing, and Deploying the Business Policy for Contoso](../../adapters-and-accelerators/accelerator-rosettanet/step-3-defining-publishing-and-deploying-the-business-policy-for-contoso.md)