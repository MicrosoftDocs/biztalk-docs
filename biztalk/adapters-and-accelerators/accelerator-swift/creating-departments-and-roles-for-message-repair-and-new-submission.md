---
title: "Creating Departments and Roles for Message Repair and New Submission | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "departments, creating"
  - "creating, roles"
  - "roles, requirements"
  - "roles, creating"
  - "creating, departments"
  - "certificates, messages"
  - "messages, certificates"
ms.assetid: 6337bd57-63c5-4d97-b558-ac27d5eb60d7
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Departments and Roles for Message Repair and New Submission
Message Repair and New Submission involves the following four different operations:  
  
- Repair of a message that has failed validation  
  
- Verification of the repair (including rekeying)  
  
- Approval of the repair  
  
- Creation of a new message  
  
  To perform one of these operations, a user must assume the role associated with the operation. The role must also be a part of the processing department (described below). To submit the message after performing a stage in the workflow, the user must sign the message with a valid certificate associated with the user.  
  
## Creating Departments and Roles  
 Refer Profile Web client documentation.  
  
## Rules of Role Use  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] users, roles, and departments must conform to the following rules:  
  
- The full workflow for a repaired message is to repair, verify, and then approve the message. The full workflow for a created message is to create, repair, verify, and then approve the message. The verification and approval steps are optional.  
  
- A department's workflow must begin with a create role or repair role. If a workflow includes both create and repair steps (a workflow for a created message), the create step must come immediately before the repair step.  
  
- A workflow for a created message must contain one and only one role that has a capability of create.  
  
- Each workflow must contain one and only one role that has a capability of repair.  
  
- An [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user can be associated with more than one role, but no single user can execute more than one step in a single workflow. For example, if user A repairs a message and user B verifies the message, then neither user A nor user B can approve the message.  
  
- There is no check on the order of roles with the capability of RekeyVerify or Approve relative to other roles with the capability of RekeyVerify or Approve.  
  
- If a message that you have already repaired fails validation again, it goes back into the repair inbox in the MRSR site document library. When this happens, the previous limitations on the verification and approver roles (based on who has already performed a role in the workflow) no longer apply. For example, if user A repairs a message, user B rejects the message in verification, and user A repairs the message a second time, then a user other than user B could verify the message. If that is the case, then user B could approve the message. Another example is that if user A creates a message, user B rejects the message in verification, and user C repairs the message, then user A could verify the message.  
  
- An [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user who creates a message can also repair that message if it fails validation.  
  
- Only [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] users in the department associated with a workflow can perform a step in the workflow. When an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user submits a message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] verifies that the user has a role in the department associated with the message (through the User profiles (in case the department is not default) in Profile web client).  
  
- An administrator can give a single [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user multiple roles within a department. A single user can perform repair, verification, approval, or creation, or any subset of those roles, subject to the limitations on any one workflow described above.  
  
## Certificates  
 To submit a message on your local computer after repair, verification, approval, or creation, the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] user must sign the message with his or her certificate. For more information about creating certificates, see [Installing Certificates](../../adapters-and-accelerators/accelerator-swift/installing-certificates.md).  
  
 To be able to repair, verify, approve, or create a message by accessing the MRSR site from a remote client computer, the user must add his or her certificate in the Certificates - Current User/Personal/Certificates store of their client computer (the user does not have to be an administrator to do so). In addition, an administrator on the server must add the user's certificate (and those of any other users who access the server from their client computer) to the Certificates (Local Computer)/Other People/Certificates store on the server.  
  
 A single user might have several allotted roles, and should use the same certificate when performing any of those roles.