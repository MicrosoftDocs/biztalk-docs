---
description: "Learn more about: PIP Implementation"
title: "PIP Implementation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords:
  - "PIPs"
  - "PIPs, element-level constraints"
  - "Document Type Definitions (DTDs)"
  - "PIPs, schemas"
  - "examples, schemas"
  - "schemas, examples"
  - "PIPs, about PIPs"
  - "element-level constraints"
  - "PIPs, DTDs"
  - "schemas, PIPs"
  - "XML Schema Definition files (XSDs)"
  - "Partner Interface Processes (PIPs)"
  - "DTDs, XSDs"
  - "schemas, XSDs"
ms.assetid: 0d964223-e0b6-4377-b26a-5fdc89ec81f4
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# PIP Implementation
RosettaNet Partner Interface Processes (PIPs) define business processes between trading partners in a supply chain. Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] provides a set of PIPs out-of-the-box and you can create additional PIPs. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] supports all PIPs defined by the RosettaNet organization.

 For more information, see [RosettaNet PIPs](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md).

## Schemas in BTARN
 RosettaNet specifies all PIP message schemas in the form of Document Type Definitions (DTDs). Trading partners who participate in the business-document exchange must comply with these DTDs. However, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implements these DTDs as XML Schema Definition files (XSDs), because Microsoft  BizTalk Server represents documents by using XSDs, not DTDs. XSDs supersede DTDs in terms of functionality, and can represent most of the information provided in the message guidelines natively.

> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] also supports next-generation PIPs, recently published by the RosettaNet organization, that use XSD specifications.

 To implement a new PIP, you must convert the PIP's DTD into an XSD. You download the DTD associated with the PIP from the RosettaNet Web site at [http://go.microsoft.com/fwlink/?linkid=33859](https://go.microsoft.com/fwlink/?linkid=33859). You then create a [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] process configuration profile based on the PIP. For more information, see [Incorporating a New Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md).

 You can create a new process configuration profile based on an existing profile. For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md). You can create multiple agreements based on the same process configuration profile between the same partners. However, you can only activate one of them at a time. To create and activate an agreement, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).

 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implements XSDs with the RosettaNet message-guideline constraints for the following RosettaNet headers:

-   Preamble for RNIF 1.1 and RNIF 2.01

-   Service header for RNIF 1.1 and RNIF 2.0

-   Delivery header for RNIF 2.0

-   Service content for all signal messages of RNIF 1.1 and RNIF 2.01.

## Sample Schemas
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] setup installs a set of PIPs in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas. These are for sample purposes only. Before using them in production, it is highly recommended that you compare these schemas against the latest published RosettaNet PIP specifications and message guidelines. BTARN supports implementation of all RosettaNet PIPs.

## Element-Level Constraints in BTARN
 In BTARN, you implement the element-level constraints specified in the PIP message-guideline documents as process configuration settings. Runtime components use the process configuration to determine how to process a specific PIP.

 To implement a new PIP, you must apply the message guideline constraints for the PIP by creating a new process configuration profile. You do this in the BTARN Management Console. For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).

 The process configuration profile maps to the RosettaNet PIP specification as shown in [Using the PIP Specification to Create a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md).

## See Also
 [What BizTalk Accelerator for RosettaNet Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)
 [Trading Partner Agreements](../../adapters-and-accelerators/accelerator-rosettanet/trading-partner-agreements.md)
 [RosettaNet PIPs](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)
