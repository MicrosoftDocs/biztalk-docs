---
title: "Encoding Characters using Free Text | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a69dffe1-3fb2-4902-a9a2-093f3ea7b11f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Encoding Characters using Free Text
Starting with [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)], “FreeText” can be used in a field or segment. Data in the “FreeText” field/segment is not parsed.  
  
## What you need to know  
  
||Behavior|Example|  
|-|--------------|-------------|  
|~: Repetition separator|In a field, Repetition (~) is treated as a repeating delimiter. In a non-free segment, Repetition (~) is treated as a repeating delimiter. In a free segment, Repetition (~) is treated as part of Free Text, not a new repetition.|In the following example, FRE is free Segment. It can have any character as free text, including ~. Any additional repetitions (~) are not considered a repetition delimiter and are treated as the Free Text content. Validation succeeds even if the child of the Free Segment is non-repeatable and contains repetition (~). FRE example:<br /><br /> **FRE&#124; Foo&^&#124;Foo&^&#124;Foo&^&#124;Foo&^~Foo&^&#124;Foo&^&#124;Foo&^&#124;Foo&^**<br /><br /> In the following example, EVN4 is defined as free text because it contains *&^*. When the “&#124;” delimiter is encountered, it is treated as the end of the current Free Text. EVN example:<br /><br /> **EVN&#124;&#124;&#124;&#124;Foo&^Foo&^Foo&^Foo&^Foo&^&#124;&#124;**<br /><br /> In the following example, the first child of EVN5 is defined as free text because it contains *&*. When the “^” delimiter is encountered, it is treated as the end of the current Free Text. EVN5 example:<br /><br /> **EVN&#124;&#124;&#124;&#124; &#124; Foo&Foo&Foo&Foo&Foo&^5.2&#124;**<br /><br /> In the following example, 5.2.1 and 5.2.2 cannot have any delimiters as Free Text, even if it is defined as FreeText in the schema. 5.2.1 and 5.2.2 example:<br /><br /> **EVN&#124;&#124;&#124;&#124; &#124; Foo1^5.2.1&5.2.2&#124;**<br /><br /> In the following example, assume EVN4 can be repeated and is of the Free Text type. *Foo1&^* is treated as the first repetition and *Foo2&^* is treated as the second repetition. If EVN4 is not repeatable (MaxOccurs = 1), then the validation fails if it contains ~, even if it is of Free Text type (like in the cases of non-Free Text fields). EVN4 example:<br /><br /> **EVN &#124;&#124;&#124;&#124; Foo1&^~ Foo2&^ &#124;&#124;**|  
|&#124;: Field separator|If a field delimiter is missing after the segment tag of a free segment, Validation succeeds.|In the following examples, FRE is a Free Text type. Free Text content can be started immediately after the FRE segment Tag, with or without “&#124;” field delimiter. Both examples succeed:<br /><br /> **FREabc** <br /> **FRE&#124;abc**<br /><br /> In the following examples, validation succeeds:<br /><br /> Input message to DASM: **FRE&#124;abcd**<br />Output from DASM: **\<SegmentData\>&#124;abcd\</SegmentData\>**<br />Output from ASM: **FRE&#124;abcd**<br /><br /> Input message to DASM: **FREabcd**<br />Output from DASM: **\<SegmentData\>abcd\</SegmentData\>**<br />Output from ASM: **FREabcd**|  
|Parent-Child optional|The parent-child optional validation rules still apply.|Assume the parent is optional and one of its children is mandatory, then:<br /><br /> -   If none of the other children and the mandatory child are not populated, then message validation succeeds.<br />-   If at least one child is populated, then the mandatory child should also be populated. Otherwise, message validation fails.<br /><br /> In the following example, Field 1 as optional. Its *1.a* child is optional and is the Free Text type. Its *1.b* child is mandatory:<br /><br /> **xyz&#124;1.a^1.b&#124;2**<br /><br /> In the following sample message, *dfssdf**&**sdf* is considered as one single element - 1.a. The parser checks if 1.b exists. When the *&#124;* is reached, it assumes 1.b is not populated and message validation fails:<br /><br /> **xyz&#124;dfssdf&sdf&#124;2**|  
|MSH, FSH, and BSH segments|Free Text is ignored for all fields. These segments correspond to the header section. Validation occurs as it normally would, even if they are defined as Free Text.||  
|\\: Escape character|If there are even number of “\” in the element, validation succeeds (even if they are not contiguous). If there are odd number, validation fails. The same behavior continues for non- Free Text fields. With Free Text fields, there is no validation on the number; it treated as Free Text content.||  
  
 [Message Delimiters](../../adapters-and-accelerators/accelerator-hl7/message-delimiters.md) provides more information on the separators in these examples.  
  
## Using Free Text  
  
1.  In the project in Visual Studio, open the schema.  
  
2.  Right-click a record, select **Insert Schema Node**, select **Child Field Element**.  
  
3.  In Properties, select **Data Type**, and then select **Free Text (SimpleType)**.  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)