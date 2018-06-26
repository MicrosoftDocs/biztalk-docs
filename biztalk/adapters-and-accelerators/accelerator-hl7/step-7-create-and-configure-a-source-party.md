---
title: "Step 7: Create and Configure a Source Party | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8788a9c-ae6f-461b-82e5-f4276d1d5e0c
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 7: Create and Configure a Source Party
In this step, you create and configure a source party, and assign send ports to enable message header transformations for the outgoing message.  
  
### To create and configure a source party  
  
1. In the BizTalk Administration Console, right-click **Parties**, point to **New**, and then click **Party**.  
  
2. In the **Party Properties** dialog box, in the Name field, type **Tutorial_BatchSource**.  
  
   > [!NOTE]
   >  The value that you type in this box is from FHS3.1 of the original [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] batched message, FragmentedInboundBatch.txt.  
  
3. In the console tree, click **Send Ports**.  
  
4. In the Send Ports pane, for the Name field, select **Tutorial_2wayAck**.  
  
5. Click **OK**.  
  
6. Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.  
  
7. In BTAHL7 Configuration Explorer, on the **Parties** tab, click **Tutorial_BatchSource**.  
  
8. Select the **Batch Definition** tab of BTAHL7 Configuration Explorer. Select **Yes** for **Fragmentation Required**, and then click **Save**.  
  
9. Select the **Acknowledgment** tab. For **Acknowledgment Type**, select **OriginalMode**, and then click **Save**.  
  
   Proceed to [Step 8: Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md).