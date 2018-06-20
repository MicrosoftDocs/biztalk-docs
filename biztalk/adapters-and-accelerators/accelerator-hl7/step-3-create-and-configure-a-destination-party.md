---
title: "Step 3: Create and Configure a Destination Party | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8746f115-9f69-4593-9943-9ccda45cd900
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3: Create and Configure a Destination Party
In this step, you create and configure a destination party for the Create-Batch scenario. You also select the messages that [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] batches and the batch schedules, as defined for that party. You schedule the batch send time as one hour after copying the files into the folder. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] batches any messages received thereafter with a frequency of one hour.  
  
### To create and configure a destination party  
  
1. In the BizTalk Server Administration Console, right-click **Parties**, point to **New**, and then click **Party**.  
  
2. In the Party Properties dialog box, in the **Name** box, type **Tutorial_BatchDest**, and then click **OK**.  
  
3. Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.  
  
4. In BTAHL7 Configuration Explorer, on the **Parties** tab in the console tree, click **Tutorial_BatchDest**.  
  
5. Click the **Acknowledgment** tab in the Details pane. Verify that the **Acknowledgment type** is **None**.  
  
6. Click the **Batch Definition** tab. In the **Available Messages** pane, select **BTAHL7Schemas.ADT_A03_231_GLO_DEF**. Click the Move to the right arrow (**>>**) to add this schema to **Selected Messages**, and then click **Save**.  
  
7. Click the **Batch Schedule** tab. In the **Repeat Batch After** section, verify that **Hours** is selected, and then type **1** in the **Hours** box. In the **Hours before first batch** box, type **1**, and then click **Start Schedule**.  
  
   Proceed to [Step 4: Configure the Source Party for the Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md).