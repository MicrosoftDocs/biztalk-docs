---
description: "Learn more about: Repairing Messages and Submitting New Messages"
title: "Repairing Messages and Submitting New Messages"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Repairing Messages and Submitting New Messages
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair and New Submission enables you to repair a message that has failed XML or Business Rules Engine validation. The repair process includes verification and approval steps that ensure the accuracy and appropriateness of the message repair. This process is performed using Microsoft [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)][!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms within MRSR site.  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] also enables you to submit a new message using this process. A creator submits the message, and the workflow can include a repairer, a verifier, and an approver performing the same tasks as in message repair.  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] ensures the security of this process by assigning different users to perform each task. You assign the appropriate repair, verify, or approve role to each of these users, and each user must use a specific certificate to perform the task. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] also supports the use of departments in processing repaired and submitted messages. Each department involves a specific workflow of tasks performed on a specific set of messages. In any of the create, repair, verify, or approve steps, when you submit the message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] calls BRE validation and verifies that the user is a member of the appropriate department. For more information about message repair and new submission, see [Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md).  
  
 If you receive an unparsed message, Message Repair and New Submission displays the message and a description of the failure in an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, and enables you to print the message or save it to a file. You can then repair and resubmit the message. However, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] does not call BRE validation or check membership in a department when you submit an unparsed message that you have repaired. In addition, a resubmitted unparsed message is not verified or approved. For more information about unparsed messages, see [Repairing Unparsed Messages](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md).  
  
 This section contains:  
  
-   [Repairing a Message](../../adapters-and-accelerators/accelerator-swift/repairing-a-message.md)  
  
-   [Verifying a Message](../../adapters-and-accelerators/accelerator-swift/verifying-a-message.md)  
  
-   [Approving a Message](../../adapters-and-accelerators/accelerator-swift/approving-a-message.md)  
  
-   [Handling an Unparsed Message](../../adapters-and-accelerators/accelerator-swift/handling-an-unparsed-message.md)  
  
-   [Creating and Submitting a New Message](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md)  
  
-   [Creating a New Message Template](../../adapters-and-accelerators/accelerator-swift/creating-a-new-message-template.md)
