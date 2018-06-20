---
title: "Components | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "architecture, components"
ms.assetid: 8793534f-5bd7-4cd3-9a42-8f0895f91007
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Components
You use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] components to implement SWIFT-centric middleware solutions that facilitate trading partner relationships, enterprise application integration (EAI), and application and business workflow automation. These components include:  
  
- **SWIFT Message Schemas.** You use XML schema definition language (XSD)-compliant schemas to facilitate the parsing of native SWIFT flat file messages into XML using the SWIFT pipeline components and [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] runtime. After you convert SWIFT data into XML, you use a map to transform it into another format, such as delimited flat files or positional flat files. This transformation enables you to use these files in your existing applications. You can also use the XML data without any mapping, such as for validation-only scenarios. SWIFT schemas also enforce SWIFT-defined data and format rules. For a complete list of schemas provided in this release, see [Supported Messages](../../adapters-and-accelerators/accelerator-swift/supported-messages.md).  
  
- **SWIFT Validation Policies and Framework.** You use [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] Business Rule Engine (BRE) policies to validate and enforce SWIFT-defined data, format, network, and usage rules. The SWIFT disassembler and [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] validation component invoke the BRE. Validation errors are collected into error-collection objects and erroneous messages are marked with special promoted properties before being published to the MessageBox database.  
  
- **SWIFT Pipeline Components.** You use the BizTalk pipeline disassembler and assembler components to process SWIFT messages. The SWIFT disassembler dynamically resolves SWIFT message types, disassembles SWIFT message batches, parses messages into XML, and validates messages against SWIFT data formats and network and usage rules. The SWIFT assembler serializes XML data back into SWIFT flat file format.  
  
- [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]  **Validation Component.** The [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] assembly provides class application programming interfaces (APIs) that can be used in BizTalk orchestration expression shapes. These classes provide the same SWIFT message validation functionality performed by the SWIFT disassembler. This functionality allows message validation to take place in orchestrations (for example, after transforming or modifying a SWIFT message).  
  
- **Message Repair and New Submission.** You use the Message Repair and New Submission feature to repair messages that fail validation or that the SWIFT disassembler cannot parse, or to create and submit new messages. This feature is implemented through the MrsrRepair orchestration, MRSR SharePoint site, and [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms.  
  
- **FRR Response Reconciliation.** FRR Response Reconciliation reconciles a FIN response with the message originally sent by A4SWIFT, enabling custom processing of the resulting message-response correlation set. FRR is implemented through the FrrMain orchestration, the FRR receive location and send ports, and the BizTalk Adapter for MQSeries.  
  
- **Software Development Kit (SDK).** The SDK provides tools, tutorials, and samples to aid development and deployment of SWIFT-based BizTalk solutions. These solutions include:  
  
  -   [End-to-End Tutorial](../../adapters-and-accelerators/accelerator-swift/end-to-end-tutorial2.md)  
  
  -   [BRE Deployment Utility](../../adapters-and-accelerators/accelerator-swift/bre-deployment-utility.md)  
  
  -   [SWIFT Header and Trailer Schemas](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  
  
- **Documentation.** [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Help describes what you need to plan, develop, deploy, and maintain your SWIFT-based BizTalk solutions.  
  
## See Also  
[Runtime, message repair, FIN response, and messaging](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md)