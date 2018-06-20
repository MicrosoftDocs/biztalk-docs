---
title: "Acknowledgment Error Conditions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "acknowledgements, errors"
  - "errors, acknowledgements"
ms.assetid: 605c7fa0-2365-4cb6-92fb-6df570905ca8
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Acknowledgment Error Conditions
The following conditions will result in a fatal error condition when [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) is processing acknowledgment (ACK) messages:  
  
- Missing required fields in MSH9  
  
- Missing required fields in MSH12  
  
  The following conditions result in a non-fatal error condition. In this situation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates the ACK, but also suspends the ACK:  
  
- Missing a required field in MSH11  
  
- Missing a MSH10 value  
  
- Enumeration type errors for optional fields in the header.  
  
> [!NOTE]
>  For enumeration type errors found in the header when MSH 15 is set to AL or ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates a commit ACK with the status **MSA_1=CR**.  
  
## See Also  
 [Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [ACK Message Schema Types](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md)   
 [Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [Setting Up a Send Port for Receiving ACKs](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)