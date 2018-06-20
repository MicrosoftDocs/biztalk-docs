---
title: "Design Time Tools | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BizTalk Adapter Framework"
  - "BTAHL7, tools"
  - "Starter Project"
  - "Pipeline Designer"
  - "BizTalk Editor"
  - "Visual Studio Starter Project"
  - "BizTalk Mapper"
  - "design-time tools"
  - "Orchestration Designer"
ms.assetid: 709bd782-d2ad-49be-ba33-e957eba2a0cc
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Design Time Tools
Developers working on [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) have the use of a set of design time tools built into BizTalk Server. These tools are integrated into [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. For more information about [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools, see [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server Help.  
  
## BizTalk Editor  
 You use BizTalk Editor to manage HL7 XSD schemas. You can use the following supported schema templates (as XSD files) for your solution development:  
  
-   HL7: 2.1 (includes 37 events)  
  
-   HL7: 2.2 (includes 56 events)  
  
-   HL7: 2.3 (includes 182 events)  
  
-   HL7: 2.3.1 (includes 189 events)  
  
-   HL7: 2.4 (includes 288 events)  
  
-   HL7: 2.5 (includes approximately 390 schemas)  
  
-   HL7: 2.XML (includes approximately 450 schemas for V2.3.1 and 2.4)  
  
## BizTalk Mapper  
 You use BizTalk Mapper to create and customize maps that define data transformations. You use BizTalk Mapper to map transformations for both inbound and outbound [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] message types.  
  
## BizTalk Orchestration Designer  
 You use BizTalk Orchestration Designer to design and implement business processes.  
  
## BizTalk Pipeline Designer  
 You use BizTalk Pipeline Designer to create and configure the pipelines that define and link processing steps. Pipelines divide processing into stages, and determine the sequence in which you perform each category of work.  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provides both receive and transmit pipelines for all supported HL7 versions. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provides a pipeline template that has a custom HL7 parser and disassembler/assembler component.  
  
## BizTalk Adapter Framework  
 You use the BizTalk Adapter Framework with end-point adapters to integrate with partners and applications.  
  
## Visual Studio Starter Project  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] includes the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Starter Project, which you can use to quick-start your HL7 solution implementation. The Starter Project includes the following projects:  
  
- **Empty**  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]  **Project**. Does not include any schemas.  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V2XCommon Project**. Includes header and acknowledgment schemas.  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V21Common Project**. Includes common schemas for HL7 version 2.1.  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V22Common Project**. Includes common schemas for HL7 version 2.2.  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V23Common Project**. Includes common schemas for HL7 version 2.3.  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V231Common Project**. Includes common schemas for HL7 version 2.3.1.  
  
- [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] **V24Common Project**. Includes common schemas for HL7 version 2.4.  
  
- BTAHL7**V25Common Project**. Includes common schemas for HL7 version 2.5.  
  
## See Also  
 [Tools and Features](../../adapters-and-accelerators/accelerator-hl7/tools-and-features.md)   
 [Analysis Tools](../../adapters-and-accelerators/accelerator-hl7/analysis-tools2.md)