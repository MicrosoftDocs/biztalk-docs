---
title: "Step 2: Enable the Batch Orchestration | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4badf807-f461-4d0a-a3b6-9f671e580d91
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Enable the Batch Orchestration
The batch orchestration controls the create batch process. It maintains references for all messages to be included in the batch, controls the outbound batch transaction, generates the batch message, routes the outgoing batch, and processes incoming acknowledgment batches. You need to enlist the batch orchestration for the create batch process to work.  
  
### To enable the batch orchestration  
  
1. In the BizTalk Administration Console, click **Orchestrations**, right-click **BatchOrchestration.Orchestration_1**, and then click **Properties**.  
  
2. In the Orchestration Properties dialog box, in the console tree, click **Bindings**.  
  
3. In the **Bindings** pane, for **Host**, select **BizTalkServerApplication**. Click **OK**.  
  
4. In the BizTalk Administration Console, right-click **BatchOrchestration.Orchestration_1**, and then click **Enlist**.  
  
   Proceed to [Step 3: Create and Configure a Destination Party](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md).