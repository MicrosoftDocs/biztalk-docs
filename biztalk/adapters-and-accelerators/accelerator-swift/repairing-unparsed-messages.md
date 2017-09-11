---
title: "Repairing Unparsed Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "unparsed messages"
  - "repairing messages, unparsed messages"
  - "messages, unparsed messages"
ms.assetid: cc061243-3539-4407-a096-71a3feded1c5
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Repairing Unparsed Messages
If the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] disassembler cannot parse a message, you can repair that message. You do so in an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form from within the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] MRSR site. However, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] processes that message differently from a repaired message that failed XML or BRE validation.  
  
 If a message or batch fails parsing, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] marks it as [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = True, with a parse error count greater than 0. The message body remains in flat-file form, encased in an XML wrapper. If the repair rule is set to permit the processing of parse failures, the message is sent to the Unparsed inbox for processing using the Unparsed form.  
  
 There is only one Unparsed inbox for all users and all departments, because [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] may not have access to any data about the message other than the original receive location. As a result, to repair an unparsed message, a user must have the repair capability and must be associated with the repair role in all departments.  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] displays the unparsed message in the text area of the Unparsed [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form. To correct the parsing problem, you may enter or delete characters as necessary. After it is submitted, the message is extracted from the XML wrapper and resubmitted through the SWIFT receive pipeline. If parsing succeeds, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] processes the message as it would any other message.  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] does not process an unparsed message that you have fixed through a full repair workflow. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] sends it out unverified and unapproved. When you sign a repaired unparsed message and then submit it, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] does not call BRE validation or check the department, but sends the message directly to the send pipeline. If that pipeline cannot process the message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] sends it to the repair process.  
  
 This process enables you to correct badly formatted messages from another system. However, you should use caution when correcting parsing issues. When [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] handles an unparsed message, it does not validate the message. Unparsed repair is not defined as a role, so anyone can perform this process. Because unparsed message do not belong to any department, the only security provided on access to them is the ACLs on the Unparsed inbox. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] also does not retain the original receive location of an unparsed message as a context property of the message.  
  
 You can write a custom validation to be performed on the repaired unparsed message. You can also write a subscription to send a repaired unparsed message to the original file pipeline.  
  
 For the repair mechanism to work on unparsed messages, you need to add the EnvelopeUnparsedMessage.xsd schema to the assembly that contains message schemas. For more information, see [Deploying A4SWIFT Schemas](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).