---
title: "Step 4: Configure the Source Party for the Create-Batch Scenario | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b06b6545-4c2e-4a56-9feb-bd3f9574d4d1
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4: Configure the Source Party for the Create-Batch Scenario
In this step, you configure the source party for the Create-Batch scenario. You also select the acknowledgments that BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) will batch, as defined for this party. You set the scheduling for the acknowledgment batch such that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will create the batch after the message count reaches 2.  
  
> [!NOTE]
>  In this scenario, you use the same source party that you created in [Step 7: Create and Configure a Source Party](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md) of Part 1 of this tutorial (the Fragmented Inbound Batch Scenario).  
  
### To configure the source party for the Create-Batch scenario  
  
1. In BTAHL7 Configuration Explorer, on the **Parties** tab in the console tree, click **Tutorial_BatchSource**.  
  
2. Click the **Acknowledgment** tab in the Details pane. Verify that the **Acknowledgment type** is **OriginalMode**.  
  
3. Click the **Batch Definition** tab. Under **Available Message Acks**, click **BTAHL7Schemas.ADT_A03_231_GLO_DEF**, click the Move to the right arrow (**>>**) to add this schema to **Selected Message Acks**, and then click **Save**.  
  
4. Click the **Batch Schedule** tab. In the **Repeat Batch After** section, select **Messages**, and then type **2** in the **Messages** box.  
  
5. Click **Start Schedule**.  
  
   Proceed to [Step 5: Create the Send Port for the Message Batch](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md).