---
title: "Using an InfoPath Form to Repair a Message or Submit a New Message | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creating, messages"
  - "InfoPath forms, verifying messages"
  - "submitting, messages"
  - "InfoPath forms, repairing messages"
  - "Bank Identifier Code (BIC)"
  - "messages, submitting"
  - "messages, repairing"
  - "unparsed messages"
  - "repairing messages, unparsed messages"
  - "messages, unparsed messages"
  - "messages, modifying"
  - "messages, InfoPath forms"
  - "modifying, messages"
  - "messages, approving"
  - "repairing messages, InfoPath forms"
  - "messages, creating"
  - "approving messages"
  - "messages, verifying"
  - "verifying, messages"
ms.assetid: fb1a885f-fb01-42be-88bc-f68715f689f7
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using an InfoPath Form to Repair a Message or Submit a New Message
To repair, verify, approve, or create a message, you work in an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form that you open from within the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] MRSR Web site. The MRSR site contains an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for each message type and an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for unparsed messages. Message Repair and New Submission sends messages in need of repair, verification, or approval to the appropriate MRSR document library, where you can open it.  
  
 When you open a message in a MRSR document library, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] displays an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form populated with the message data. You perform the operation inside the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, which enables you to manipulate the data within labeled fields, to select values from drop-down lists (if applicable), and to see whether a field is required or optional. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] ensures that the Message Repair and New Submission process is secure by requiring a domain account and signature with a certificate for submission.  
  
 To perform an operation on a message in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] MRSR site, you must deploy the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for that message type. This loads the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form required for the message into the Templates document library.  
  
## Repairing a Message  
 To repair, verify, approve, or create a message, you work in an InfoPath form that you open from within the MRSR SharePoint site. The message to be repaired is published in the MRSR site. Message Repair and New Submission sends messages in need of repair, verification, or approval to the appropriate MRSR site document library, where you can open it.  
  
 When you open a message in a MRSR site document library, A4SWIFT displays an InfoPath form populated with the message data. You perform the operation inside the InfoPath form, which enables you to manipulate the data within labeled fields, to select values from drop-down lists (if applicable), and to see whether a field is required or optional. A4SWIFT ensures that the Message Repair and New Submission process is secure by requiring a domain account and signature with a certificate for submission.  
  
 To perform an operation on a message in the MRSR site, you must deploy the InfoPath form for that message type. This loads the InfoPath form required for the message into the Templates document library.  
  
## Verifying a Message  
 A repair workflow can include a verification stage. In this stage, after a repairer has repaired a message, a verifier verifies that the repairs in the message are correct. To do this, you open the message in an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form from the \<department name>_RekeyVerify document library in your MRSR site, and verify that the repairs made to the message are correct. You must also rekey data into certain fields that require rekeying. All verification stages require rekeying, although you can customize which fields (if any) need to be rekeyed. For more information about rekey verification, see [Special Processing in Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md).  
  
 A workflow consisting of all possible stages includes one or more verification stages. However, a workflow does not need to include a verification stage.  
  
## Approving a Message  
 A repair workflow can include an approval stage. In this stage, after a verifier has verified the repairs to a message, or the data in a new message, an approver visually verifies that the repairs in the message are correct. Note that a verification stage consists of a rekey verification, while an approval stage consists of a visual verification.  
  
## Accepting or Rejecting the Changes to a Message  
 After completing a stage, a creator, repairer, verifier, or approver can either accept the changes, cancel the changes, or reject the changes. If the submission is successful, acceptance moves the message to the next stage. Rejection submits the message with the changes rejected. Cancellation cancels the submission process, and the message remains in its current stage.  
  
 If you reject a message in the verify or approve stage, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] returns the message to the first stage defined for that workflow (create or repair). The workflow is reset, so any repairer can repair the message. If the first stage of the workflow rejects the message, the repair orchestration publishes the message to the MessageBox with the appropriate promoted properties. You can write a custom handler to process these messages. For more information, see [Creating a Custom Handler for Rejected Messages](../../adapters-and-accelerators/accelerator-swift/creating-a-custom-handler-for-rejected-messages.md).  
  
 If you reject a message in the create or repair stage, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] suspends the message, and you receive the error message: "Could not reset to the first stage in the workflow."  
  
## Repairing an Unparsed Message  
 If a message fails because of a parsing error, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] routes the message to the Unparsed document library in MRSR site. As with messages that fail validation, when you double-click the message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] displays an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form populated with the message data. You repair the message from within the form. When you submit the message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] sends the message directly to the outbox without verification or approval. For more information, see [Repairing Unparsed Messages](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md).  
  
## Creating and Submitting a New Message  
 You can create a new message in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] MRSR site by displaying a new message form, entering data, and submitting it. For more information, see [Creating and Submitting a New Message](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md).  
  
 To create a new message, you must deploy a new message form for that message type. This loads the XML form required for the message into a document library that you create to contain new-message forms.  
  
 When you create a message from the default new message form, none of the fields are populated, requiring you to enter data in the all the fields. You can prepopulate fields in a form by opening a message, entering data, and then running the Save-As command from the File menu in MRSR site. You can give the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form a different name and save it to a different document library.  
  
## Looking Up a BIC  
 When you work in an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] MRSR site, you may need to enter a Bank Identifier Code (BIC). [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] provides a utility that you can use to look up a BIC. In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, click BIC Lookup in the right pane of the form. This displays a form for searching for the BIC based upon the bank name, or vice versa. This searches the Bicplus table of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] database. For more information on the Bicplus table, see [Enabling Validation of Bank Identifier Codes](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md) and [Managing the Bicplus Table in the A4SWIFT Database](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md).