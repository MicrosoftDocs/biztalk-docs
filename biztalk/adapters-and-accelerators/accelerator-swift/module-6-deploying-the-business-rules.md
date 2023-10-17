---
description: "Learn more about: Module 6: Deploying the Business Rules"
title: "Module 6: Deploying the Business Rules | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tutorial, deploying business rules"
  - "deploying, business rules"
  - "business rules"
ms.assetid: e8fb8993-3450-4795-80fd-ff28bff8fe97
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Module 6: Deploying the Business Rules
In this module, you deploy the business rules, confirm your installation log, and confirm your deployment using the Business Rule Composer tool.  
  
 You use business rules to ensure that Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] messages adhere to format specifications, field specifications, and network validated rules as defined in the Society for Worldwide Interbank Financial Telecommunication (SWIFT) standards. Format specifications pertain to the structure of the message as a whole and field specifications detail each field in the message. Network validated rules apply to cross-field validations and are complex in nature.  
  
 A4SWIFT provides XSD schema specifications for each message. The A4SWIFT disassembler (DASM) and assembler (ASM) use the schema to parse or serialize and validate native flat-file messages. Validations are limited to format specifications and field specifications that the schema encodes. However, you cannot encode some formats and field related rules within the schema.  
  
 A4SWIFT also includes a set of business rules that follow the SWIFT Standards Release Guides (SRG). The BizTalk Server Business Rule Engine (BRE) calls the A4SWIFT policies and enforces the A4SWIFT business rules.  
  
 These business rules are included due to the complex validations relating to format and fields, and network-validated rules that are beyond the natural capability of the schema. The SWIFT DASM or ASM components within a receive or send pipeline call the BRE.  
  
 You turn the validations on or off by changing the **BREValidation** property for the DASM within your pipeline.  
  
 This section contains:  
  
-   [Lesson 1: Deploying the Related Business Rules](../../adapters-and-accelerators/accelerator-swift/lesson-1-deploying-the-related-business-rules.md)  
  
-   [Lesson 2: Confirming the Deployment Using the Business Rule Composer Tool](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md)
