---
description: "Learn more about: Position Counting in Bytes"
title: "Position Counting in Bytes | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cf666ec-d15e-4d2d-9df9-49189f352c65
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Position Counting in Bytes

## Overview

You can use the **Count Positions In Bytes** property of the **Schema** node to: 

* Specify how the values you enter for the **Positional Length** and **Positional Offset** properties of the various fields within positional records are interpreted
* Specify how the values you enter for the **Tag Offset** property of the positional records themselves are interpreted

By default, these values are interpreted as a number of characters. But when the **Count Positions In Bytes** property is set to **True**, these values are interpreted as a number of bytes.  
  
 Setting the **Count Positions In Bytes** property to **True** might be necessary when dealing with multibyte character set (MBCS or DBCS) data, or when your flat file messages originate in SAP, mainframes, or other systems that may count positions in bytes.  
  
 Counting field lengths in bytes can be complicated when the number of bytes used to encode characters is variable, and can result in some issues with respect to determining field boundaries. When the flat file disassembler parses a flat file in such situations, it attempts to make appropriate parsing decisions based on its knowledge of the character encoding in use.  
  
 An example of this type of parsing decision concerns lead bytes in MBCS character encodings. Lead bytes are well-known byte values that are used to begin multibyte character encodings, and which should never occur on their own. When specifying the length of the fields using bytes rather than character, situations may arise in which the last byte in a field is found to be a lead byte, which cannot constitute an entire character on its own. In such cases, the flat file disassembler will treat the character occurring just prior to the lead byte as the last character in the previous field, and begin parsing the next field starting with the lead byte.  

More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
## See Also  
 [Positional Record Considerations](../core/positional-record-considerations.md)   
