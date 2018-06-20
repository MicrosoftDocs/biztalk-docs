---
title: "ACK Message Modes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message modes, ACK messages"
  - "messages, acknowledgements"
  - "acknowledgements, message modes"
  - "ACK message modes"
ms.assetid: ab4a9470-dab2-46d4-8d0a-54dc12f2fa90
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# ACK Message Modes
For acknowledgment (ACK) messages, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) determines the acknowledgment mode and values to use for populating MSH15 and MSH16 fields of the ACK you want to generate. These values are present in the Trading Partner Management (TPM) configuration. The following values are possible for ACK mode:  
  
> [!NOTE]
>  In the following list, the HL7 specification mandates items 1 through 3 and that they contain MSH15 and MSH16 values. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] defines item 4 to signify that an acknowledgment should not be generated.  
  
1. Original - One ACK sent after validating the header and body. This mode involves schema validation.  
  
2. Enhanced - Two ACK messages sent:  
  
   -   Accept ACK – The receiving system sends this type of ACK after validation of the header. This ACK signals to the initiating application that the message is committed to the database.  
  
   -   Application ACK- The receiving system sends this type of ACK after complete message validation, including the header and the body.  
  
3. Deferred - Two ACK messages sent.  
  
   - Original Mode: The receiving system sends this type of ACK after validation of the header and body. This mode involves schema validation.  
  
   - Deferred Mode: The line-of-business application acknowledges the message after processing it. The application delivers the deferred message to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], which process it as a stand-alone message and delivers it to the destination.  
  
4. Static - An on success or on failure ACK sent.  
  
## See Also  
 [Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [ACK Process Model](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md)   
 [Static Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/static-acknowledgments.md)