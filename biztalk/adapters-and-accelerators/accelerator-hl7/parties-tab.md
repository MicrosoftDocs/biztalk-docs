---
title: "Parties tab in the HL7 accelerator in BizTalk Server| Microsoft Docs"
description: Use the BTAHL7 Configuration Explorer to view existing parties, and configure acknowledgments in BizTalk Server
ms.custom: ""
ms.date: "08/14/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e01052c8-25c5-4736-8403-33f16fbd3fb7
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Parties in BTAHL7 Configuration Explorer
You use the **Parties** tab to view the available parties and specify [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] configuration for a particular party that you choose, and to configure properties for acknowledgments. 

## Parties UI explained
The **Parties** tab contains both a left and right pane. The available parties appear in the left pane. The right pane contains the following tabs for the selected party:  
  
- **Party Aliases**. Use this tab to view information about the party you have selected from the left pane.  
  
  > [!NOTE]
  >  You use BizTalk Explorer to create parties.  
  
- **Batch Definition**. Use this tab to configure [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] batching.  
  
- **Batch Schedule**. Use this tab to activate outbound batches.  
  
- **Acknowledgment**. Use this tab to specify the properties for inbound and generated acknowledgments.  
  
- **Validation**. Use this tab to select the message validation options for inbound and generated messages.  
  
- **MSH Map**. Use this tab to enable message header transformations for inbound messages.  
  
  > [!NOTE]
  >  You must configure party aliases, batch definitions, batch schedules, and acknowledgment information for all trading parties.  
  > 
  >  You can refresh the parties list by pressing F5, or by right-clicking the parties list, and select **Refresh**.  
  
## Next steps  
  
-   [Party Aliases Tab](../../adapters-and-accelerators/accelerator-hl7/party-aliases-tab.md)  
  
-   [Batch Definition Tab](../../adapters-and-accelerators/accelerator-hl7/batch-definition-tab.md)  
  
-   [Batch Schedule Tab](../../adapters-and-accelerators/accelerator-hl7/batch-schedule-tab.md)  
  
-   [Acknowledgment Tab](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-tab.md)  
  
-   [Validation Tab](../../adapters-and-accelerators/accelerator-hl7/validation-tab.md)  
  
-   [MSH Map Tab](../../adapters-and-accelerators/accelerator-hl7/msh-map-tab.md)