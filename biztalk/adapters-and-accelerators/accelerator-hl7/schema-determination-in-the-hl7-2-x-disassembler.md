---
title: "Schema Determination in the HL7 2.X Disassembler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "header segments [2.X]"
  - "2.X messages, header segments"
  - "messages, parsing messages"
  - "MSH"
  - "disassembler, parsing messages"
  - "2.X messages, MSH"
ms.assetid: afd45c4c-2feb-44eb-b3bd-49fe114eb893
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Schema Determination in the HL7 2.X Disassembler
HL7 2.X messages contain a header segment (MSH), followed by a number of body segments and an optional number of Z segments. MSH contains 21 fields.  
  
 When a message arrives, the 2.X engine reads the header to determine the schema to use to parse the message body. The following sequence of events occurs:  
  
1. The disassembler reads the value of MSH3 (source party) to determine the following validation options:  
  
   1.  Whether to perform XML validation for the body  
  
   2.  Whether to validate custom data type fields in the body data  
  
   3.  Whether to allow trailing delimiters in the body  
  
   4.  What the target namespace of the body schema is (**TargetNS**)  
  
2. The disassembler then reads MSH9 and MSH12 to determine the root node name of the body. The algorithm is as follows:  
  
   ```  
   Body schema type = TargetNS + "#" + MSH9.1 + MSH9.2 + MSH12.1 (with dots removed) + MSH12.2 (or GLO if the value is blank) + MSH12.3 (or DEF if the value is blank)  
   ```  
  
    [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) always allows trailing delimiters in a message header. The engine examines the segment identifier that is the first three characters of each line. It keeps on generating XML for all segments that the body schema defines. When it encounters an undefined segment, it treats that segment as a Z segment. From that point on, all undefined segments constitute the Z part of the message. The next MSH marks the end of this message. For batch messages, the next MSH or BTS (the batch trailer segment tag) marks the end of a message. A Z segment can only contain segments that are undeclared in a schema. It is an error to encounter a declared segment.  
  
## See Also  
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [BTAHL72X Flat File Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)