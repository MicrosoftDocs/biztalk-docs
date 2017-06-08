---
title: "Special Processing in Message Repair and New Submission | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "repairing messages, rekey verification"
  - "repairing messages, process flow"
  - "rekey verification"
  - "repairing messages"
  - "messages, templates"
  - "messages, rekey verification"
  - "BIC fields"
  - "templates, messages"
  - "BIC-12 data"
  - "messages, process flow"
  - "BIC-11 data"
ms.assetid: 0ab729e3-4b67-47d3-84c9-f016318a4c41
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Special Processing in Message Repair and New Submission
The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair and New Submission functionality enables customers to develop an enterprise implementation. The functionality supports the following special processing:  
  
-   Rekeying verification  
  
-   Department-specific workflow support (For more information, see [Repairing Messages and Submitting New Messages](../../adapters-and-accelerators/accelerator-swift/repairing-messages-and-submitting-new-messages.md).)  
  
-   Entry of BIC-12 data as BIC-11  
  
-   Entry of BIC fields as one string  
  
-   Repair and resubmission of parse failures (For more information, see [Repairing Unparsed Messages](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md).)  
  
-   Saving repairs in progress by using the Save command  
  
-   Creating a new template by using the Save As command  
  
## Rekey Verification  
 For many financial institutions, the primary means of checking work is for a second person to rekey the most important fields of a transaction. This operation verifies that the second person has read, and understands, the data in those fields. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] provides this capability for messages repaired or created in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 If a rekey step is required, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] blanks out the fields to be rekeyed in the form presented to the user. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] still displays the contents of the original message in the task pane, so the verifier can use those contents when entering the data. The verifier should not change other fields in the message, because this might allow changes without verification. Instead, the verifier should reject the message repair if other changes need to be made.  
  
 After the rekey step, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] compares the results of the rekeying with the results of the repair. It performs this comparison only on the fields that have been rekeyed, on a field-by-field basis. If the two versions do not agree on a character-by-character basis, the message must be repaired again. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] indicates that there was a key verification mismatch, and adds the error to the error-collection part of the message. The data entered by the verifier is not saved.  
  
 The fields to be rekeyed are specified in the MrsrXpathConfig.xml file in the MRSR folder under the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] folder. This file contains name/value pairs consisting of the field to be rekeyed and the xpath to the field. You can customize this file to change which fields will be rekeyed for each message. The fields to be rekeyed are generally those representing the most important date associated with the message contents, the currency of the transaction, and the amount of the transaction.  
  
 All verification steps in Message Repair and New Submission involve rekey verification. Sight verification is performed by the approver.  
  
## Entry of BIC-12 Data as BIC-11  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] accommodates the need for an additional character in the Logical Terminal (LT) Address of a message. The LT Address contains only 11 characters of data, but the SWIFT Alliance Access (SAA) requires the LT field to have an "X" in position 9. This extra character indicates to SAA that it should select the correct LT.  
  
 The LT address is used for transmission of the message over the FIN network. It can be contained in two fields of a SWIFTBound message (the LT Address field of the Basic Header block or the Destination Address field in the input Application Header block) and in two fields of a message from SWIFT (the LT Address field of the Basic Header block or the LT Address in the Message Input Reference in the Output Application Header block).  
  
 Users must enter only 11 characters when they create or repair a message, or rekey the field as part of verification. Even when repairing or rekeying an LT that has 12 characters, a user must enter only 11 characters. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] inserts the twelfth character and validates the 12-character field. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] validates the 11-character LT address against the address in the BIC Plus database.  
  
## Entry of BIC Fields as One String  
 You can enter the BIC into a single field on [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms. The BIC contains four subfields, each of which has a subfield on the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms. After you enter the full BIC string into the single field, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] populates each of the four subfields.  
  
## Saving Repairs in Progress  
 If you need to interrupt a repair, you can save a message in its current state back into the repair inbox. You do so by using the Save command to check in the message. You can close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form and check the message out later, or someone else can check it out to continue the repair. The message's history indicates the save operation, and a second repairer can see the repairs that you performed.  
  
 You can execute a Save As command to store a message in its current state on the user's local machine. This leaves the message checked out to the user who performed the Save As. The user can close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form and return later to complete the repair, but another user cannot check out the message and repair it.  
  
## Creating a New Template  
 When creating a new message, you can create a new template by executing a Save As command. This enables you to open an existing template, add data to fields, and then create a new template based on the existing template that includes the additional data. You save the template with a new name, and anyone with access to the new message folder in MRSR site can create a new message based on the template. You must save the template to the MRSR site to submit a message based on the template to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. Otherwise, errors will occur or you will not be able to open the form.