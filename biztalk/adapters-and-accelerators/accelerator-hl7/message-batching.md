---
description: "Learn more about: Message Batching"
title: "Message Batching"
ms.date: "06/08/2017"
ms.prod: biztalk-server
ms.topic: article
---
# Message Batching
Protocol standards, scheduling issues, or message size limitations may motivate the need to batch messages. A Health Level Seven (HL7) batch consists of messages enclosed by an HL7 batch header and batch trailer. Message separators separate the individual messages within the batch.  
  
 Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] supports the following three message batching scenarios:  
  
-   **Fragmented inbound batch**. In this scenario, BTAHL7 receives an HL7 message batch, and then routes the individual messages to the destination system.  
  
-   **Batch in/batch out**. In this scenario, BTAHL7 receives an HL7 message batch, verifies the individual messages within the batch, and then routes the message batch to the destination system.  
  
-   **Create batch or outbound batching**. In this scenario, BTAHL7 receives individual messages and batches them before routing them to the destination system.  
  
    > [!NOTE]
    >  BTAHL7 does not enable message batching for outbound batching by default. You must use BizTalk Explorer to first enlist the BTAHL7 batch orchestration, and then start the batch orchestration. For more information about enabling message batching, see [Configuring Batching](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).  
  
## In This Section  
  
-   [Fragmented Inbound Batch](../../adapters-and-accelerators/accelerator-hl7/fragmented-inbound-batch.md)  
  
-   [Configuring Batching](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)  
  
-   [Scheduling Batching](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)  
  
-   [Configuring Batching Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)
