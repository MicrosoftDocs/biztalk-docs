---
description: "Learn more about: Batch Message Processing"
title: "Batch Message Processing"
ms.date: "06/08/2017"
ms.prod: biztalk-server
ms.topic: article
---
# Batch Message Processing
Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) handles three types of HL7 2.X batch scenarios:  
  
- Fragmented inbound batch scenario. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parses these batches into separate output messages. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends acknowledgments (ACKs) for each message in a fragmented batch.  
  
- Batch in/batch out scenario. These are in-bound batches that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not fragment, but passes through and sends as an intact batch. If [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK for the batch, the ACK includes a version ID.  
  
- Create-batch scenario. In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] combines separate input messages into an output batch.  
  
  You can format batches in either of two ways:  
  
- With a file header and trailer (FHS/FTS) and a batch header and trailer (BHS/BTS).  
  
- With no file or batch headers/trailers.  
  
## See Also  
 [Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)   
 [Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)   
 [Part 1: Fragmented Inbound Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [Part 2: Batch In/Batch Out Scenario](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)   
 [Part 3: Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)   
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)
