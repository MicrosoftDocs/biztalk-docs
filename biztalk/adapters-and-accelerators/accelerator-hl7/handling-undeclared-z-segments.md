---
title: "Handling Undeclared Z Segments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Z segments, 2.X schemas"
  - "2.X schemas, undeclared Z segments"
  - "segments, undeclared [Z objects]"
  - "Z objects, undeclared segments"
ms.assetid: 8878bc93-1833-4bfc-b80e-305e4144739e
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Handling Undeclared Z Segments
There are two types of Z segments: declared Z segments and undeclared Z segments. While they are similar in that you use them for local purposes, they are very different in how you use them.  
  
 You include the definition of a declared Z segment in a message schema, and [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses it to process a message, just like a schema defined by the HL7 standard. No schema defines an undeclared Z segment. You include an undeclared Z segment at the end of a message, and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] passes through without processing it against a schema. The parser and serializer do not validate it. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] treats it as a binary large object (BLOB). The only check that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does on an undeclared Z segment is verifying that the BLOB does not include any existing three-character schema tag.  
  
 You include the undeclared Z segment as the third part, or Z part, of a multi-part message. The message includes the header, the body, and the Z part. The Z part has a segment ID starting with the letter "Z".  
  
> [!NOTE]
>  The Zpart must always contain data. Specifying null for the stream results in an error condition. If no data is included in the Zpart, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] inserts the word "Empty" in the Zpart. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] uses the context property **ZPartPresent** to determine whether to serialize the Z part.  
> 
> [!CAUTION]
>  [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] has tested Zsegments with ANSI character sets, with the result that Zsegment behavior with ANSI characters is predictable. However, using other character sets in Zsegments may result in unpredictable behavior.  
  
## See Also  
 [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)