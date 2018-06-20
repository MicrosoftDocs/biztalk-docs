---
title: "Server Runtime Security | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, server runtime"
  - "servers, security"
  - "servers, runtime"
ms.assetid: 40f5ca3e-d9d3-4543-bd38-82283c343b76
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Server Runtime Security
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair and New Submission governs the flow of SWIFT messages between business users, back-end systems, and SWIFT network endpoints in a secure and deterministic manner. It authenticates messages submitted by business users, validates messages for data and business-rule correctness, and routes messages to back-end systems or for final delivery to the SWIFT network. For more information about digital certificates, see "Encryption and Signing Certificates" on the MSDN Library Web site at [http://go.microsoft.com/fwlink/?linkid=50285](http://go.microsoft.com/fwlink/?linkid=50285).  
  
 Message Repair and New Submission is a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestration application, hosted and executed in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security context. It is secured as a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application by the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security features described earlier. Message Repair and New Submission also defines and enforces user-level security policies specific to SWIFT message creation, repair, approval, and submission, as follows:  
  
- All messages, new or repaired, submitted to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] through Message Repair and New Submission must originate from a trusted user.  
  
- Trusted users who create or repair messages must have the correct authorization and rights. Trusted users who approve or reject messages must have the correct authorization and rights.  
  
- All messages must be approved by a known number of trusted users. Each trusted user in the chain of message creator, repairer, and approvers must be unique—the same user cannot create or repair and approve or reject a message. The same user cannot enter multiple approve or reject decisions for a single message in a multistep approval process. You cannot approve your own created or repaired messages, nor can you approve the same message as multiple approvers.  
  
- You cannot alter a message during the approval process (that is, a message cannot be altered after original submission to Message Repair and New Submission, as a new or repaired message).  
  
- Messages altered during a rekey verification stage must exactly match the original message (either created or repaired).  
  
  To enforce these security semantics, Message Repair and New Submission validates the digital signature embedded in every XML message that it receives, at each stage of the creation or repair approval-submission process. The Message Repair and New Submission digital signature validation performs the following checks. If one or more of these checks fail, Message Repair and New Submission stops and is persisted through the message box, and a security fault is logged in the Event Log:  
  
- The XML message must be digitally signed and therefore must contain a corresponding digital signature.  
  
- Each digital signature used in the workflow must be made by using a trusted digital certificate. This ensures that the message creator, repairer, verifier and approvers are trusted.  
  
- Each trusted digital certificate must belong to a [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] domain user who has membership in the domain group having logical authority or rights to perform actions within [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. This ensures that each participant in the create or repair-approval-submission process has the correct authority or rights to perform the specific action that they performed.  
  
   The preceding rules are enforced through ACLs on the SharePoint site through site user groups and through the form submit code. If the user acting upon the message is not in the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Users group (domain or local), Message Repair and New Submission rejects the message.  
  
   For example, an organization that enforces a three-stage approval process might define these three logical roles: Repairers, Verifiers (Rekey stage), and Approvers. Correspondingly, the users participating in the roles need to belong to the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Users domain group. To further lock down the SharePoint site the users should be organized into logical domain groups (such as repairers, verifiers, approvers).  
  
   For more information about site user groups see [Windows SharePoint Services Security](../../adapters-and-accelerators/accelerator-swift/windows-sharepoint-services-security.md).  
  
- Each digital signature in the stack must be unique. That is, each digital signature must be made by using a unique digital certificate (relative to the other signatures in the same stack). This ensures that the message was not approved by the person who created/repaired the message, and that no person approved the same message as multiple approvers.  
  
  Message Repair and New Submission imposes strict security policies by having checkpoints at each entry point into the message creation, repair, approval, and submission infrastructure. These checkpoints are tightly coupled with core functionality of Message Repair and New Submission and cannot be circumvented. While Message Repair and New Submission is designed to integrate seamlessly with the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form-signing functionality, it is also designed to be secure and robust enough to enforce authenticity and protection of SWIFT messages even if [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] is not used and messages are submitted directly by end users to Message Repair and New Submission receive endpoints (SharePoint Web folders).