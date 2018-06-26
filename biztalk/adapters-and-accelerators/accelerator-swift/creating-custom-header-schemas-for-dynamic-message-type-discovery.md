---
title: "Creating Custom Header Schemas for Dynamic Message Type Discovery | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schemas, dynamic resolution"
  - "schemas, message types"
  - "schemas, custom headers"
  - "header schemas"
ms.assetid: 0c936c57-b533-47ca-9258-576b021fd016
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Custom Header Schemas for Dynamic Message Type Discovery
In most scenarios, you should specify the default SWIFT header schema (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) for the SWIFT Header Schema configuration property of the SWIFT disassembler. The SWIFT disassembler uses the default SWIFT header schema to parse message headers that conform to the SWIFT standard specification, and has the necessary promoted properties to facilitate dynamic schema resolution (and sub-type resolution for "dual type" SWIFT messages like MT574_IRSLST and MT574_W8BENO). For more information about the default SWIFT header schema and to understand how the SWIFT disassembler performs schema resolution, see [Dynamic Message Type Discovery and Schema Resolution](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md).  
  
 For other scenarios where messages contain non-SWIFT standard header data, you can use a custom header schema for header parsing and dynamic message type discovery. To create and use a custom header schema for dynamic schema resolution, do the following:  
  
1. Create a custom schema that the SWIFT disassembler can use to structurally parse the expected header data format.  
  
2. Identify which fields in the schema will hold the value(s) indicating message type.  
  
3. Add the A4SWIFT Property Schema (Microsoft.Solutions.A4SWIFT.Property.PropertySchema) to the "Property schemas list" of the custom header schema and promote the appropriate fields that indicate message type using the following [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] properties:  
  
   -   **A4SWIFT_MessageType**  
  
   -   **A4SWIFT_MessageType2** (optional if **A4SWIFT_MessageTypes** is used)  
  
   -   **A4SWIFT_SecondaryMessageType** (optional)  
  
4. Build and deploy the custom header schema.  
  
5. Set the SWIFT Header Schema configuration property of the SWIFT disassembler (in your receive pipeline project) to the custom header schema.  
  
   For more information about these and other promoted properties, see [A4SWIFT_* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md). For more information about using BizTalk Editor to create and edit schemas, promote properties using a property schema, and build and deploy schema projects, see BizTalk Server Help.  
  
## See Also  
 [Working with the SWIFT Disassembler and Assembler](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)