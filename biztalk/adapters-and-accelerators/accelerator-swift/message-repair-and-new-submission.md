---
description: "Learn more about: Message Repair and New Submission"
title: "Message Repair and New Submission"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Message Repair and New Submission
The Message Repair and New Submission feature of [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides a way for you to repair MT and MX messages that fail validation. Using the MRSR SharePoint site (deployed by user), you can see how the message failed validation. From MRSR site, you can open the message in an InfoPath form that enables you to identify the error, repair the message, and submit it for reprocessing.  
  
 Message Repair and New Submission supports role-based message repair. A full repair workflow includes repair, verification, and approval. A repair workflow is associated with a department that defines the roles (or stages) of the workflow and configures an A4SWIFT user for each role. Each repair role has a separate MRSR site view tailored to the role. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] performs validation, and each A4SWIFT user performing a role signs the message, using a certificate, to ensure a secure process.  
  
 In addition to message repair, A4SWIFT enables you to submit a new message using an enhanced [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form. A fourth A4SWIFT user, a creator, performs this function. The process also performs validation, and can involve repair, verification, and approval roles to ensure successful submission. A4SWIFT handles new message submission through an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form the same way that it handles a repaired message.  
  
 This section contains:  
  
-   [Message Repair Process](../../adapters-and-accelerators/accelerator-swift/message-repair-process.md)  
  
-   [Creating Departments and Roles for Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)  
  
-   [Using an InfoPath Form to Repair a Message or Submit a New Message](../../adapters-and-accelerators/accelerator-swift/using-an-infopath-form-to-repair-a-message-or-submit-a-new-message.md)  
  
-   [Special Processing in Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md)  
  
-   [Repairing Unparsed Messages](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)  
  
-   [Message Repair and New Submission Service Processing](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission-service-processing.md)
