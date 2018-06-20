---
title: "Step 1: Configure and Enable the BatchControlPort Receive Port | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: be248a05-e740-497a-b112-8ba3a57b020b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 1: Configure and Enable the BatchControlPort Receive Port
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) setup creates a receive port, the batch control port, to handle the messages that the batch orchestration uses to start, stop, and time batches. These messages include the batch activation, batch termination, and batch timer messages. In this step, you configure the receive pipeline for the batch control port, and enable the port.  
  
### To configure and enable BatchControlPort  
  
1. Start **BizTalk Server Administration**.  
  
2. In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1**. Click **Receive Locations**.  
  
3. Right-click **BatchControlLocation**, and then click **Disable**.  
  
4. Right-click **BatchControlLocation**, and then click **Properties**.  
  
5. In the Receive Location Properties dialog box, for **Receive Pipeline**, select **BTAHL72XPipelines.BTAHL72XReceivePipeline**.Click **OK**.  
  
6. In the BizTalk Administration Console, right-click **BatchControlLocation**, and then click **Enable**.  
  
   Proceed to [Step 2: Enable the Batch Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md).