---
title: "Schema Determination in the HL7 2.X Assembler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, assembler"
  - "MSH5"
  - "assembler, schemas"
ms.assetid: 464c006e-4fae-4e2a-99ea-157301c0179e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Determination in the HL7 2.X Assembler
When a message flows to the serializer, the serializer in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses MSH5 (destination party) of the message to determine the operations to be performed on the message. Such operations include:  
  
- Whether to perform XML validation for body segments  
  
- Whether to validate custom data types for body segments  
  
- Whether to allow trailing delimiters in the body  
  
- Which schema target namespace the serializer will use  
  
- Whether the serializer needs to map the header  
  
  To determine the schema, the serializer does the following:  
  
- Sets the target namespace (**TargetNS**) to the same value as the namespace configured for the destination party  
  
- Extracts **Rootnode** from the **BTS.MessageType** promoted property  
  
  The **doctype** becomes **TargetNS + "#" + Rootnode**.  
  
## See Also  
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [BTAHL72X Flat File Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)