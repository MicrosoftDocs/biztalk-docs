---
description: "Learn more about: Static Acknowledgments"
title: "Static Acknowledgments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "static acknowledgements"
  - "acknowledgements, static acknowledgements"
ms.assetid: 1cdd01fc-1dae-4851-917f-4f13a0f9595a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Static Acknowledgments
BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) supports original, enhanced, deferred, and static acknowledgment (ACK) modes. If you select static ACK mode for a party in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will generate static ACKs that contain only an indication of success or failure. The static ACK indicates whether the receiving system received and processed the message, in success and failure values configured in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.  
  
 In original, enhanced, and deferred modes, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates dynamic ACKs. They are HL7-encoded, and contain fields such as the MSA.1 Acknowledgment Code field and the ERR segment. The MSA.1 field of a dynamic ACK will indicate whether a failure condition is a Reject or an Error, which result in different processing (see [Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)). The ERR segment provides detailed information about the error. Static ACKs provide no such information.  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] processes a static ACK differently from a dynamic ACK. If a two-way send port (which will only send the next message after receiving the ACK) receives the static ACK, and the ACK indicates failure (or is not a valid ACK), [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will move to the secondary transport or suspend the message. It will not retry the message, as it would if it received a dynamic ACK, depending upon the failure condition.  
  
 When the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parser processes a static ACK, it writes the **IsStaticAck** Boolean property to the message context. The serializer uses this value to determine whether it should process the message as a static ACK.  
  
## See Also  
 [Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)
