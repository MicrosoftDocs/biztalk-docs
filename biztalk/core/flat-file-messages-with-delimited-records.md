---
title: "Flat File Messages with Delimited Records | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ad7119b-4e39-43df-9dba-a04382eb6db2
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Flat File Messages with Delimited Records
Delimited records within a flat file instance message contain nested records and/or individual fields (items of data) that are separated by a predefined character or set of characters. The fields are parsed according to these separating delimiters. For example, consider the following delimited records from a flat file instance message, which contain two line items from a hypothetical purchase order:  
  
```  
  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Electric-120vac,ITEM926-AA|Baby Monitor|1|39.98|Electric-4AA|2004-01-21  
  
```  
  
 A reasonable definition for this record in a flat file schema can be described as follows:  
  
- A delimited record named items with child delimiter (,), child order prefix, and the tag ITEMS.  
  
  -   A delimited, repeating record named item with child delimiter &#124;, child order infix, and the tag ITEM.  
  
  -   An attribute named "partNum".  
  
  -   An element named "productName".  
  
  -   An element named "quantity".  
  
  -   An element named "USPrice".  
  
  -   An element named "powerSource".  
  
- An optional element named "shipDate".  
  
  Given these record and field definitions, the flat file disassembler produces the following XML equivalent of these records.  
  
```  
  
<items>  
    <item partNum="872-AA">  
        <productName>Lawnmower</productName>  
        <quantity>1</quantity>  
        <USPrice>148.95</USPrice>  
        <powerSource>Electric-120vac</powerSource>  
    </item>  
    <item partNum="926-AA">  
        <productName>Baby Monitor</productName>  
        <quantity>1</quantity>  
        <USPrice>39.98</USPrice>  
        <powerSource>Electric-4AA</powerSource>  
        <shipDate>2004-01-21</shipDate>  
    </item>  
</items>  
  
```  
  
 There are a number of considerations related to delimited records that will affect how the record is parsed when received and constructed when sent, including:  
  
- The character or characters used to override the interpretation of delimiters so that they are treated as part of the data. For more information, see [Ways to Interpret Special Characters as Part of a Field Value](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md).  
  
- An optional tag at the beginning of the record, used to distinguish the record from other similar records. For more information, see [Tag Handling in Delimited Records](../core/tag-handling-in-delimited-records.md).  
  
- How data is justified within fields with minimum lengths, relative to the accompanying pad characters. For more information, see [Field Padding](../core/field-padding.md), [Field Justification](../core/field-justification.md), and [Minimum Field Lengths Within Delimited Records](../core/minimum-field-lengths-within-delimited-records.md).  
  
- Positional records nested within other delimited records. For more information, see [Nested Positional and Delimited Records](../core/nested-positional-and-delimited-records.md).  
  
- How data is justified within a fixed length field, relative to its accompanying pad characters. For more information, see [Field Justification](../core/field-justification.md).  
  
- Considerations concerning the positioning of delimiters relate to the data that they delimit. For more information, see [Child Order Considerations](../core/child-order-considerations.md).  
  
- Preservation and suppression of delimiters when flat file messages are received and sent. For more information, see [Delimiter Preservation and Suppression](../core/delimiter-preservation-and-suppression.md).  
  
  To help you better understand how to work with delimited flat files, see the samples in the FlatFileReceive and FlatFileSend folders located at [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Pipelines\AssemblerDisassembler\\.  
  
> [!NOTE]
>  If your flat file contains both delimited and positional records, you must set the **Structure** property of the root node to **Delimited** and the **Structure** property of subordinate record nodes to either **Delimited** or **Positional** as appropriate.  
  
> [!NOTE]
>  Delimited fields in flat files have a limit of 50000000 characters.  
  
## See Also  
 [Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md)   
 [How to Create Schemas for Flat File Messages](../core/how-to-create-schemas-for-flat-file-messages.md)   
 [Migrating Flat File Records](../core/migrating-flat-file-records.md)