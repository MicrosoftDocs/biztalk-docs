---
title: "Batch-Related Promoted Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "promoted properties, batch related properties"
  - "batching, promoted properties"
ms.assetid: 00df1d8f-2f3f-4e3f-9983-37dcf3514fd8
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Batch-Related Promoted Properties
When the SWIFT disassembler publishes a message that originated from an inbound batch to the MessageBox database, the disassembler marks the message with special [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] promoted properties that are specific to batch messages. These properties provide context information, such as which batch a message originated from, what ordinal position it was in within the batch, which parts A4SWIFT has preserved, and so forth.  
  
 A4SWIFT sets the following promoted properties for batch messages:  
  
- **A4SWIFT_BatchId**  
  
- **A4SWIFT_IsMessageHeaderValued**  
  
- **A4SWIFT_IsMessageTrailerValued**  
  
- **A4SWIFT_NumberOfParts**  
  
- **A4SWIFT_PosInBatch**  
  
  For information about these and other promoted properties, see [A4SWIFT_* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).  
  
## Failures During Batch Processing  
 When the SWIFT disassembler encounters message failures (parsing or validation) during batch processing (**Inbound Debatching** set to **True**), its behavior depends upon the batching configuration, as follows:  
  
- For batch processing (**Inbound Debatching** set to **True**) with fragmentation enabled (**Fragmentation** set to **True**), the disassembler publishes failed messages to the MessageBox database individually, with corresponding error information appended in promoted properties and serialized **ErrorCollection** XML. If the disassembler finds unexpected data at the end of the batch (that is, data that the disassembler cannot parse using any of the specified schemas), the disassembler includes this unexpected data in the last message in the batch and marks it as having failed parsing. If the disassembler encounters a fatal error during processing, then the disassembler publishes the message that caused the fatal error, plus all data to the end of the interchange, as a single message. The disassembler does not fragment messages after the fatal error.  
  
- For batch processing (**Inbound Debatching** set to **True**) with fragmentation disabled (**Fragmentation** set to **False**), the disassembler publishes failed messages to the MessageBox database individually, with corresponding error information appended in promoted properties and serialized **ErrorCollection** XML. In addition, the disassembler publishes the entire batch (containing one or more failed messages) to the MessageBox database as a single message, in native form (exact copy of input). The disassembler marks it with the **A4SWIFT_Failed** promoted property set **True** to indicate that the batch contains one or more failed messages. The disassembler also attaches serialized **ErrorCollection** XML to the un-fragmented batch that represents the concatenation of all errors encountered in the individual messages within the batch. To discover the per-message error details from failed messages in the batch, you must retrieve the individual failed messages from the MessageBox database (by correlating on A4SWIFT_BatchId), and extract the **ErrorCollection** XML for each failed message. If the disassembler finds unexpected data at the end of the batch (that is, data that the disassembler cannot parse using any of the specified schemas), the disassembler includes the unexpected data with the entire failed batch (since the disassembler publishes it to the MessageBox database verbatim), and marks it as having failed parsing due to unexpected data.  
  
- For non-batch scenarios (**Inbound Debatching** set to **False**), the disassembler always publishes failed messages to the MessageBox database individually, as expected.  
  
  For more information about A4SWIFT failure/error promoted properties and the **ErrorCollection** object, see [Working with Failed Message Subscriptions](../../adapters-and-accelerators/accelerator-swift/working-with-failed-message-subscriptions.md).  
  
## See Also  
 [Disassembling Inbound Batches](../../adapters-and-accelerators/accelerator-swift/disassembling-inbound-batches.md)   
 [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)