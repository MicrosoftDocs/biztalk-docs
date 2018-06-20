---
title: "Escape Characters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3af800b9-d31b-487a-9a06-6eda47d1574e
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Escape Characters

## Overview
An escape character is a single character that suppresses any special meaning of the character that follows it. For example, if you define a flat file record as having the following characteristics:  
  
- Name = Record1  
  
- Delimited  
  
- Child delimiter = comma character (,)  
  
- Child order = prefix  
  
- Escape character = backslash character (\\)  
  
- Tag = RECORD1  
  
- Two fields named Field1 and Field2  
  
  Then the following flat file data applies for the record.  
  
```  
RECORD1,testfield1\,testfield1,testfield2  
                  ^^  
  
```  
  
 The data will be disassembled into the following fragment of XML.  
  
```  
<Record1>  
    <Field1>testfield1,testfield1</Field1>  
    <Field2>testfield2</Field2>  
</Record1>  
  
```  
  
 Note that the escape character sequence `\,` indicated on the line following the flat file record, has been converted to a single comma character without the escape character in the data for Field1 in the equivalent XML record. Furthermore, that comma character was not interpreted as a field delimiter like the other two commas are.  
  
 When the flat file assembler performs the reverse operation, converting the XML version of the record to its equivalent flat file record, the escape character will be inserted before the comma in the middle of Field1, thereby indicating that it should be interpreted as data rather than as a field delimiter.  
  
 When creating a flat file schema using BizTalk Editor, you can define a default escape character for the entire schema using the **Default Escape Character** and **Default Escape Character Type** properties of the **Schema** node. Then, you can configure each individual record in the schema to either use this default escape character or a custom, record-specific escape character using the **Escape Character]** and **Escape Character Type** properties of the **Record** node.  
  
## See Also  
- [Ways to Interpret Special Characters as Part of a Field Value](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)  
- Escape character properties  [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    - Default Escape Character (Node Property of Flat File Schemas)
    - Default Escape Character Type (Node Property of Flat File Schemas)
    - Escape Character (Node Property of Flat File Schemas)  
    - Escape Character Type (Node Property of Flat File Schemas)