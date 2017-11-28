---
title: "Table Values Common Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "2.X schemas, common schemas"
  - "2.X schemas, table values"
  - "common schemas"
ms.assetid: 2421e150-1bae-43bd-aba3-6322c679b22b
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Table Values Common Schemas
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) generates the **tablevalues_*\<version\>*.xsd** file for each HL7 version, and locates the file at the root of the HL7 version-specific folder. The data type common schema file references the table values common schema file.  
  
 Values in these tables are in the form of enumerations. Each enumeration defines the values that are acceptable within one or more fields of the message schemas. You can see which table applies to a node of a message schema by opening the schema in BizTalk Editor, clicking a node, and looking at the **Base Data Type** property in the Properties pane.  
  
 You will not be able to see what the acceptable values for this node are, however, by viewing the enumeration in the Properties pane for the message-schema node. This is because the table values common schema file defines the enumeration. To view the enumerations, click **tablevalues_*\<version\>*.xsd** in the Schema tree in BizTalk Editor, and then click the ellipsis (**...**) button on the Enumeration row in the Properties pane.  
  
## See Also  
 [HL7 2.X Common Schema Files](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)   
 [Data Types Common Schemas](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md)   
 [Segments Common Schemas](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md)