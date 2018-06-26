---
title: "Which Node Name Characters Get Encoded | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48a581d2-48fa-4c36-b5c2-fe87c328a7f4
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Which Node Name Characters Get Encoded
XML places some restrictions on the characters that can be used in XML names, such as element names, including some special restrictions on the first character of an XML name. The conceptual goals in determining which characters to allow and which characters to exclude from legal XML names are:  
  
- Wherever applicable, be inclusive rather than exclusive, so that new writing systems can be accommodated as they are encoded in Unicode.  
  
- Exclude characters that may be or are used as delimiters, so that XML names can more easily appear in a non-XML, delimited context.  
  
  The following table shows which characters can be used in an XML name, either in any position within the name, or in any position other than the first. Some allowable characters are excluded from being the first character in the name. Literal characters are quoted, and ranges are shown within square brackets.  
  
|Position in name|Allowed characters|  
|----------------------|------------------------|  
|Any position|["A"-"Z"], ["a"-"z"], "_", [0x00C0-0x02FF], [0x0370-0x037D], [0x037F-0x1FFF], [0x200C-0x200D], [0x2070-0x218F], [0x2C00-0x2FEF], [0x3001-0xD7FF], [0xF900-0xEFFF]|  
|Any position except first|"-", ".", ["0"-"9"], 0x00B7, [0x0300-0x036F], [0x203F-0x2040]|  
  
 Best practice in English for an element or attribute name (a node name in the schema tree view) can be summarized as:  
  
-   Use alphanumeric characters, except do not begin a name with a numeral.  
  
-   Use the underscore (_),hyphen (-), period (.), and middle dot (·).  
  
-   Do not use white space.  
  
-   Use meaningful words or combinations of words in natural languages.  
  
## See Also  
 [Node Name Property](../core/node-name-property.md)   
 [How Node Name Characters Get Encoded](../core/how-node-name-characters-get-encoded.md)