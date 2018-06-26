---
title: "Specification of Field Positions within Positional Records | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33c2eee3-ec30-46c5-a143-a3d2e2f265a6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Specification of Field Positions within Positional Records
To define a positional record, you must provide information about the positions and lengths of the fields within that record. If the record contains subrecords, the positions and lengths of the fields in the subrecord are rolled up to contribute to the information about the containing record.  
  
 The sum of the values you specify for the **Positional Offset** and **Positional Length** properties for a particular **Field Element** or **Field Attribute** node determines the number of characters dedicated to the corresponding field. The series of these sums across all of the fields in the record and any of its subrecords determine the boundaries of the fields in the records.  
  
> [!NOTE]
>  When the **Count Positions In Bytes** property of the **Schema** node is set to **Yes**, the **Positional Length** and **Position Offset** properties specify bytes rather than characters.  

See more details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## Positional Offset property  
 When the flat file disassembler is converting a flat file instance message into an equivalent XML instance message, the value you specify for the **Positional Offset** property defines a number of characters (or bytes) that are ignored and skipped over at that position in the instance message. In other words, any information occurring at that starting position and length (the latter as specified by the **Positional Offset** property) in the flat file instance message will not be copied into the XML version of the message.  
  
 When the flat file assembler is converting an XML instance message into an equivalent flat file instance message, the value you specify for the **Positional Offset** property defines a number of characters (or bytes) that are filled with space characters at that starting position within the flat file instance message being created. The space character is always used to fill offset positions; the character used is not configurable.  
  
 The **Positional Offset** property provides flexibility for interpreting the contents of positional records. Essentially, this property allows you to ignore any fixed length data that precedes the field for which it is set to a nonzero value. That fixed length data might be one or more entire fields of data or some type of constant data, such as a tag associated with the field, that does not need to be included in the XML equivalent of the flat file instance message. For more information, see the example that follows.  
  
## Positional Length property  
 When the flat file disassembler is converting a flat file instance message into an equivalent XML instance message, the value you specify for the **Positional Length** property defines the number of characters (or bytes) that are associated with the field at that position in the instance message. The information occurring at that starting position and length in the flat file instance message constitutes the data in the field, subject to the additional information provided by the associated **Justification** and **Pad Character** properties. For more conceptual information about justification and field padding, see [Field Justification](../core/field-justification.md) and [Field Padding](../core/field-padding.md).  
  
 When the flat file assembler is converting an XML instance message into an equivalent flat file instance message, the value you specify for the **Positional Length** property defines a number of characters (or bytes) available for writing the data associated with that field. If there are fewer data characters than the specified length of the field, the relevant pad character is used to fill up the difference. If there are more data characters than the specified length of the field, the beginning or end of the data is truncated based on the setting of the **Justification** property and not included in the flat file instance message being constructed.  
  
> [!NOTE]
>  The trailing portion of left-aligned data is truncated and discarded. The leading portion of right-aligned data is truncated and discarded.  
  
## Example  
 Consider the following field definitions for a record.  
  
|Field node name|Offset|Length|Pad Character|Justification|  
|---------------------|------------|------------|-------------------|-------------------|  
|Field1|0|6|Default (space)|Left|  
|Field2|0|4|*|Right|  
|Field3|2|6|*|Left|  
|Field4|4|6|Default (space)|Right|  
  
 And the following stream of characters is encountered at the starting point of a record with these field definitions (the first line is for counting character positions).  
  
```  
123456789012345678901234567890123456789012345678901234567890  
abc   **12345678**skip  here  
```  
  
 When these field definitions are applied to this sample record data, the flat file disassembler produces the following XML equivalent (with the data shown in bold type).  
  
```  
<Field1>abc</Field1>  
<Field2>12</Field2>  
<Field3>5678</Field3>  
<Field4>here</Field4>  
```  
  
 The following observations are relevant to how this data is parsed:  
  
- The characters associated with Field1 (length 6 with no offset) are "`abc` ", but the spaces are not included in the XML because the space character is the (default) pad character for Field1 and Field1 is defined as left-aligned.  
  
- The characters associated with Field2 (length 4 with no offset) are "`**12`", but the asterisks are not included in the XML because the asterisk character is the pad character defined for Field2 and Field2 is defined as right-aligned.  
  
- The characters associated with Field3 (length 6 plus an offset of 2) are "`345678**`", but the 3 and 4 are not included in the XML because of the offset. The asterisks are also not included in the XML because the asterisk character is the pad character defined for Field2 and Field2 is defined as left-aligned.  
  
- The characters associated with Field4 (length 6 plus an offset of 4) are "`skip  here`", but the character sequence "`skip`" is not included in the XML because of the offset. The two space characters are also not included in the XML because the space character is the (default) pad character for Field4 and Field4 is defined as right-aligned.  
  
  If the XML produced by the flat file disassembler in this example is passed to the flat file assembler using the same field definitions, the same flat file data is produced, with two exceptions: the discarded offset sequences 34 and skip are filled with space characters (indicated with the `^` character in the line following the data).  
  
```  
123456789012345678901234567890123456789012345678901234567890  
abc   **12  5678**      here  
          ^^      ^^^^  
  
```  
  
## See Also  
- [Field Considerations](../core/field-considerations.md)    
- [Field Justification](../core/field-justification.md)   
- [Field Padding](../core/field-padding.md)   
- More info on the following properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:  
    - Count Positions In Bytes (Node Property of Flat File Schemas)  
    - Justification (Node Property of Flat File Schemas)  
    - Pad Character (Node Property of Flat File Schemas) 
    - Positional Offset (Node Property of Flat File Schemas)
    - Positional Length (Node Property of Flat File Schemas)