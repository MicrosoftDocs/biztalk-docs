---
title: "Flat File Messages with Positional Records | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72c17c25-3847-458e-a43e-0dbdc42db749
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Flat File Messages with Positional Records
Positional records within a flat file instance message contain individual fields (items of data) that are each of a predefined length. The fields are parsed according to these lengths. For example, consider the following positional record from a flat file instance message, which contains a ship to address (the first line shows the number of characters reserved for each field).  
  
```  
123456789012345678901234567890123456789012345678901234567890123456789012345  
US        Alice Smith         123 Maple Street    Mill Valley    CA 90952  
```  
  
 A reasonable definition for this record in a flat file schema can be described as a positional record named shipTo that contains the following fields:  
  
- An attribute named country/region that is left-aligned, 10 characters in length, with a zero character offset.  
  
- An element named name that is left-aligned, 20 characters in length, with a zero character offset.  
  
- An element named street that is left-aligned, 20 characters in length, with a zero character offset.  
  
- An element named city that is left-aligned, 15 characters in length, with a zero character offset.  
  
- An element named state that is left-aligned, 2 characters in length, with a zero character offset.  
  
- An element named zip that is left-aligned, 5 characters in length, with a one character offset.  
  
  Given these record and field definitions, the flat file disassembler will produce the following XML equivalent of this record.  
  
```  
<shipTo country/region="US">  
    <name>Alice Smith</name>  
    <street>123 Maple Street</street>  
    <city>Mill Valley</city>  
    <state>CA</state>  
    <zip>90952</zip>  
</shipTo>  
  
```  
  
 There are a number of considerations related to positional records that will affect how the record is parsed when received and constructed when sent, including:  
  
- The character used to fill the unused portion of each field, known as the pad character. For more information, see [Field Padding](../core/field-padding.md).  
  
- An optional tag within the record, used to distinguish the record from other similar records. Tags usually occur at the beginning of the record but allowable anywhere within it. For more information, see [Tag Handling in Positional Records](../core/tag-handling-in-positional-records.md). Positional records can be defined to have a tag or not have a tag, but once defined, the tag must be present or not, based on the definition.  
  
- How data is justified within a fixed length field, relative to the accompanying pad characters. For more information, see [Field Justification](../core/field-justification.md).  
  
- Positional records nested within other positional or delimited records. For more information, see [Nested Positional Records](../core/nested-positional-records.md).  
  
- Positional records with field lengths specified as a specific number of bytes rather than a specific number of characters. For more information, see [Position Counting in Bytes](../core/position-counting-in-bytes.md).  
  
  To help you better understand how to work with positional flat files, see the samples in the FlatFileReceive and FlatFileSend folders located at \Program Files\Microsoft BizTalk Server\SDK\Samples\Pipelines\AssemblerDisassembler\\.  
  
> [!NOTE]
>  If your flat file contains both delimited and positional records, you must set the **Structure** property of the root node to **Delimited** and the **Structure** property of subordinate record nodes to either **Delimited** or **Positional** as appropriate.  
  
> [!NOTE]
>  Fields in positional records have a limit of 50000000 characters.  
  
## See Also  
 [Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md)   
 [How to Create Schemas for Flat File Messages](../core/how-to-create-schemas-for-flat-file-messages.md)