---
title: "InfoPath Security | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "security, InfoPath forms"
  - "InfoPath forms, security"
ms.assetid: 6ed7b5cc-9801-45a5-8fdb-e5d56dd36435
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# InfoPath Security
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 uses XML Signatures to let you digitally sign a form using a digital certificate. XML Signatures defines a standard for XML-based digital signatures that you use to help secure the data contained in XML documents. XML Signatures is a standard governed by the World Wide Web Consortium (W3C).  
  
 A digital signature is an electronic, encryption-based, secure stamp of authentication on a macro or document. When digitally signing an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, the XML instance entered through the form is "stamped" with a digital signature (the signature public key and signed data digest is written to a dedicated node in the XML). This signature confirms that the XML document originated from the signer and has not been altered. [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] provides verifiable, non-repudiable signing, partial signing, cosigning and countersigning through enhanced digital signature support.  
  
 The SWIFT [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms generated with the FormGenerator utility provided by A4SWIFT use the countersigning method of digital signing to let signatures of countersigners to be stacked on top of each other. This countersigning signature stack models the human-oriented process of creating or editing a SWIFT message, having the message reviewed and approved by one or more reviewers and approvers, and finally submitting that message only after all stages in a workflow have signed off.  
  
 Repairers, reviewers, or approvers sign the message regardless of whether they approve or reject it. The signature signifies authenticity of the response and does not necessarily signify an "accepted" decision.  
  
 When the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form is submitted, it checks messages for validity and that the user signing the form is in the correct role.  
  
 If the message is rejected at any stage in a workflow (besides repair), the message is sent back to the repair stage. If the message is rejected at the repairer or creator stage, Message Repair and New Submission sends the message back to the Message Repair and New Submission orchestration instance with specific properties marking the message as rejected.  
  
 This section describes how Message Repair and New Submission handles the digital signatures based on the capabilities defined for a role. The role and capability combination is called a "stage" in the workflow.  
  
> [!NOTE]
>  The "create" role is limited to a single creator across all departments.  
  
 This section contains:  
  
-   [Create and Repair Stages](../../adapters-and-accelerators/accelerator-swift/creating-and-repairing-stages.md)  
  
-   [Rekey Verification Stage](../../adapters-and-accelerators/accelerator-swift/rekey-verification-stage.md)  
  
-   [Approval Stage](../../adapters-and-accelerators/accelerator-swift/approval-stage.md)  
  
-   [Distributing Digital Certificates](../../adapters-and-accelerators/accelerator-swift/distributing-digital-certificates.md)