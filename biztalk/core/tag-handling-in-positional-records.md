---
title: "Tag Handling in Positional Records | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c85d695-6dc9-4200-a453-dc576832adca
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Tag Handling in Positional Records
Positional records can include a well-known sequence of characters, known as a tag, which can be used to disambiguate one type of record from another. This allows the flat file disassembler to properly identify the appropriate **Record** node in the schema that contains the information required to correctly parse the flat file record.  
  
 You can use the [Tag Identifier](../core/tag-identifier-node-property-of-flat-file-schemas.md) and [Tag Offset](../core/tag-offset-node-property-of-flat-file-schemas.md) properties together to specify the tag and its position within a positional record. Note that this allows the tag to occur anywhere within the positional record and that depending on your settings for the [Positional Length](../core/positional-length-node-property-of-flat-file-schemas.md) and [Positional Offset](../core/positional-offset-node-property-of-flat-file-schemas.md) properties of the various fields within the record, the tag can be interpreted as part of data associated with one or more of these fields.  
  
 The **Positional Offset** property also allows you to treat the tag separately from the data in the record. For example, if the tag occurs at the beginning of the record and is four characters in length, you could set the value of the **Positional Offset** property of the first field in the record to four, thereby effectively skipping over the positional record tag when the value of the first field is translated in the equivalent XML format of the record.  
  
## See Also  
 [Positional Record Considerations](../core/positional-record-considerations.md)   
 [Tag Identifier (Node Property of Flat File Schemas)](../core/tag-identifier-node-property-of-flat-file-schemas.md)   
 [Tag Offset (Node Property of Flat File Schemas)](../core/tag-offset-node-property-of-flat-file-schemas.md)   
 [Positional Length (Node Property of Flat File Schemas)](../core/positional-length-node-property-of-flat-file-schemas.md)   
 [Positional Offset (Node Property of Flat File Schemas)](../core/positional-offset-node-property-of-flat-file-schemas.md)