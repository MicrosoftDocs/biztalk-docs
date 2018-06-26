---
title: "Wrap Characters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7268f46-9bf6-4c76-9b3a-b4ee0e8db997
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Wrap Characters

## Overview
A wrap character is a single character that is used to wrap the data characters in a field for the purpose of suppressing any special meaning that any of those data characters would otherwise have. For example, if you define a flat file record as having the following characteristics:  
  
- Name = Record1  
  
- Delimited  
  
- Child delimiter = comma character (,)  
  
- Child order = infix  
  
- Escape character = backslash character (\\)  
  
- Tag = RECORD1  
  
- Three fields named Field1, Field2, and Field3, each defined to use the number sign character (#) as their wrap character.  
  
  Then the following flat file data applies for the record.  
  
```  
RECORD1#field1#,#field2#,#field3#  
  
```  
  
 The data is disassembled into the following fragment of XML.  
  
```  
<Record1>  
    <Field1></Field1>  
    <Field2></Field2>  
    <Field3></Field3>  
</Record1>  
  
```  
  
 Note that the wrap characters (#) surrounding the bolded data characters field1, field2, and field3 have been removed.  
  
 When the flat file assembler performs the reverse operation, converting the XML version of the record to its equivalent flat file record, the wrap characters are inserted before and after the data characters of each of the fields, yielding the original sequence of flat file characters.  
  
 The defined escape character can be used in conjunction with the defined wrap character. For example, suppose the value of Field1 is changed as follows (shown in bold type).  
  
```  
<Record1>  
    <Field1></Field1>  
    <Field2>field2</Field2>  
    <Field3>field3</Field3>  
</Record1>  
  
```  
  
 When this XML fragment is assembled, using the record and field definitions provided, the following sequence of flat file characters is produced (the escaped number sign character sequence is shown in bold type).  
  
```  
RECORD1#field1#,#field2#,#field3#  
  
```  
  
 When creating a flat file schema using BizTalk Editor, you can define a default wrap character for the entire schema using the **Default Wrap Character** and **Default Wrap Character Type** properties of the **Schema** node. Then, you can configure each individual field in the schema to either use this default wrap character or a custom, field-specific wrap character using the **Wrap Character** and **Wrap Character Type** properties of the **Field Element** or **Field Attribute** nodes in flat file schemas.
  
## See Also  
- [Ways to Interpret Special Characters as Part of a Field Value](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)  
- Wrap character properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    -  Default Wrap Character (Node Property of Flat File Schemas
    -  Default Wrap Character Type (Node Property of Flat File Schemas
    -  Wrap Character (Node Property of Flat File Schemas  
    -  Wrap Character Type (Node Property of Flat File Schemas