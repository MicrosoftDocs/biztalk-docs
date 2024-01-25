---
description: "Learn more about: Field Padding"
title: "Field Padding"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Field Padding

## Overview

Pad characters are used in fields within both delimited and positional records when the data contained within the field smaller than the number of characters or bytes reserved for the field. These characters occupy the portion of the field not required by the data, if any. Pad characters are specified on a field-by-field basis using the  **Pad Character** and **Pad Character Type** properties of the corresponding **Field Element** and **Field Attribute** nodes. If no pad character is specified for a particular field, the default pad character, space (" "), is used for that field.  
  
## Inbound instances

For inbound instance messages, regardless of whether a particular record is positional or delimited, the flat file disassembler discards leading or trailing instances for the specified or default pad character for a particular field as the instance message is translated into its equivalent XML form. Whether it is leading or trailing instances of the relevant pad character that are discarded depends on whether the **Justification** property of corresponding **Field Element** and **Field Attribute** node is set to **Right** or **Left**, respectively.  

## Outbound instances
  
For outbound instance messages, the flat file assembler will insert the appropriate number of the specified or default pad character into fields so that the length of the field is correct. The pad characters will be inserted before or after the data characters based on whether the **Justification** property of the corresponding **Field Element** and **Field Attribute** node is set to **Right** or **Left**, respectively.  
  
When the field to be padded in an outbound instance message is contained within a positional record, the **Positional Offset** and **Positional Length** properties of the corresponding **Field Element** or **Field Attribute** node, combined with the number of data characters that the field must contain, determine whether any pad characters are required, and if so, how many. When the field to be padded in an outbound instance message is contained within a delimited record, pad characters are only inserted when the value of the **Minimum Length with Pad Character** property of the corresponding **Field Element** or **Field Attribute** node exceeds the number of data characters.  

For more details on the properties mentioned in this article, see the [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

## See Also
  
- [Field Considerations](../core/field-considerations.md)
- [Field Justification](../core/field-justification.md)
- [Specification of Field Positions within Positional Records](../core/specification-of-field-positions-within-positional-records.md)