---
title: "Message Repair Process | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "repairing messages"
  - "errors, messages"
  - "messages, errors"
  - "validating, messages"
  - "messages, validating"
ms.assetid: 87b97cec-5796-4684-bcf0-53285aca7ee2
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Repair Process
By default, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] suspends failed messages in the suspended queue of the MessageBox database. This process handles failed messages separately from successful messages. Using this default mechanism, however, you have a limited ability to retrieve failed messages and repair them. The Message Repair and New Submission feature of [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] enables an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user to repair a message and resubmit it. Another [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user can then verify the repairs, and a third can approve the repairs.  
  
> [!NOTE]
>  In this context, an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user is a user that performs a role in a departmental repair workflow. This A4SWIFT user is defined, and associated with a certificate, in the Users link of the Profile Web Client. This [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user is not the same as a [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] user account, as defined in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Users group in the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Computer Management utility. The person functioning as an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user must have a [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] user account so that they can use that account's certificates when submitting a message. However, that person can also serve as other [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] users: repairer, verifier, approver, or creator. For more information, see [Creating Departments and Roles for Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md).  
  
 With this repair workflow, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] does not suspend a failed message. It performs additional processing on the failed message, and then drops the message into the MessageBox, just as it would a successful message. The repair orchestration drops the message into the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] MRSR site, where users can perform their functions in [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms.  
  
## Message Validation  
 Message Repair and New Submission sends any message failing the following validation to MRSR site for repair:  
  
- Structural validation performed by the flat file parser (unparsed messages)  
  
- Data validation performed by the XML validating reader  
  
- SWIFT network and usage rule validation performed by the Business Rule Engine (BRE)  
  
  [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] collects any errors encountered during validation in an error collection object that travels with the SWIFT message. The repair process includes serializing error information into XML and attaching it to the message as an error part. This processing also includes marking the message with a promoted property that indicates that the message has failed validation ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed==True), and another promoted property that reports the error counts for each validation stage. The resulting multipart message consists of the following:  
  
- A body part containing the failed message  
  
- An error part containing the error-collection XML  
  
- Promoted properties indicating the failure state  
  
## Message Repair  
 The MRSRDepartmentRule business rule within the MRSRDepartmentPolicy determines which department will handle the failed message. The message repair orchestration starts the repair workflow by routing the message to an inbox associated with the repair role in the department. The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user performing the repair role opens the message in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, repairs the message, and then signs and submits it. The orchestration routes the repaired message to each of the repair, rekey verification, or approval roles, and after the workflow has successfully completed, routes the message to the send port.  
  
 In addition to validation, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] checks the signatures on the message to determine the following:  
  
- The users in the repair workflow belong to the same department  
  
- Each user has signed just once  
  
- The sequence of roles corresponding to the users matches the sequence in the workflow defined for that department  
  
  For more information about departments, see [Creating Departments and Roles for Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md).  
  
  [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] also enables you to repair unparsed messages. However, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] performs different processing on a repaired unparsed message. For more information, see [Repairing Unparsed Messages](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md).