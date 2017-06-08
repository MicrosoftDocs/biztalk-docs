---
title: "Escape Characters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
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
An escape character is a single character that suppresses any special meaning of the character that follows it. For example, if you define a flat file record as having the following characteristics:  
  
-   Name = Record1  
  
-   Delimited  
  
-   Child delimiter = comma character (,)  
  
-   Child order = prefix  
  
-   Escape character = backslash character (\\)  
  
-   Tag = RECORD1  
  
-   Two fields named Field1 and Field2  
  
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
  
 When creating a flat file schema using BizTalk Editor, you can define a default escape character for the entire schema using the [Default Escape Character](../core/default-escape-character-node-property-of-flat-file-schemas.md) and [Default Escape Character Type](../core/default-escape-character-type-node-property-of-flat-file-schemas.md) properties of the **Schema** node. Then, you can configure each individual record in the schema to either use this default escape character or a custom, record-specific escape character using the [Escape Character](../core/escape-character-node-property-of-flat-file-schemas.md) and [Escape Character Type](../core/escape-character-type-node-property-of-flat-file-schemas.md) properties of the **Record** node.  
  
## See Also  
 [Ways to Interpret Special Characters as Part of a Field Value](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)   
 [Default Escape Character (Node Property of Flat File Schemas)](../core/default-escape-character-node-property-of-flat-file-schemas.md)   
 [Default Escape Character Type (Node Property of Flat File Schemas)](../core/default-escape-character-type-node-property-of-flat-file-schemas.md)   
 [Escape Character (Node Property of Flat File Schemas)](../core/escape-character-node-property-of-flat-file-schemas.md)   
 [Escape Character Type (Node Property of Flat File Schemas)](../core/escape-character-type-node-property-of-flat-file-schemas.md)