---
title: "Field Justification | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 04380208-9bfd-43cf-a279-104daea2b978
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Field Justification
Field justification concerns whether the data characters in a field occur before (left-aligned) or after (right-aligned) any accompanying pad characters.  
  
 Sometimes the data characters contained within a field do not require all of the space dedicated to that field. This is true most frequently in positional records, where the number of bytes or characters dedicated to a field is fixed, as determined by the [Positional Length](../core/positional-length-node-property-of-flat-file-schemas.md) and [Positional Offset](../core/positional-offset-node-property-of-flat-file-schemas.md) properties. It is common in such scenarios that the item of data is smaller than the field length, with the unused portion of the field being filled with pad characters.  
  
 Such padding can also occur in delimited records when the value of the [Minimum Length with Pad Character](../core/minimum-length-with-pad-character-node-property-of-flat-file-schemas.md) property exceeds the space required to store the relevant item of data.  
  
 In both such cases, the value of the [Justification](../core/justification-node-property-of-flat-file-schemas.md) property (**Left** or **Right**) of the relevant **Field Element** or **Field Attribute** node determines whether the pad characters will follow the data characters (left-aligned) or whether the pad characters will precede the data characters (right-aligned).  
  
 When the flat file disassembler is converting a flat file instance message into an equivalent XML instance message, the **Justification** property is used when parsing the corresponding field. When the flat file assembler is converting an XML instance message into an equivalent flat file instance message, the **Justification** property is used to determine when the pad characters associated with a particular field, if any, should be added to the data stream: either before or after the corresponding data characters.  
  
## See Also  
 [Field Considerations](../core/field-considerations.md)   
 [Justification (Node Property of Flat File Schemas)](../core/justification-node-property-of-flat-file-schemas.md)   
 [Positional Offset (Node Property of Flat File Schemas)](../core/positional-offset-node-property-of-flat-file-schemas.md)   
 [Positional Length (Node Property of Flat File Schemas)](../core/positional-length-node-property-of-flat-file-schemas.md)