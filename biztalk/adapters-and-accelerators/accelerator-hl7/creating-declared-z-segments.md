---
title: "Creating Declared Z Segments | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Z objects, creating segments"
  - "segments, creating Z segments [Z objects]"
  - "Z segments, creating"
  - "creating, Z segments [Z objects]"
ms.assetid: afd1b7b7-089e-4c6a-a063-e708431bb888
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Declared Z Segments
You can create declared Z segments at any level of a schema (unlike undeclared Z segments, which must be the last part of a multi-party message, following the body part).  
  
### To create a Z segment in BizTalk Editor  
  
1.  In Solution Explorer of Visual Studio, right-click the schema to which you want to add a Z segment, and then click **Open**.  
  
2.  In BizTalk Editor, right-click the node with the name of the schema, point to **Insert Schema Node**, and then click **Child Record**.  
  
3.  Name the record starting the name with three alphanumeric digits, in capitals, with the first digit being "Z". (The Z segment tag must include three characters.) Insert an underscore (_), and then add a short description of the segment. The description should be one or a series of words, without spaces, with the first letter of each word capitalized. The last word should be "Segment". (An example is "ZPP_PatientPreferencesSegment.) Press **Enter**.  
  
4.  In the Properties pane, type the properties you want for the Z segment, including **Data Structure Type** (schema name or xsd:anyType), **Max Occurs**, and **Min Occurs**.  
  
    > [!NOTE]
    >  If you enter a data structure type for the record, you will not be able to add a child field element.  
  
5.  In BizTalk Editor, right-click the name of the Z segment, point to **Insert Schema Node**, then click **Child Field Element**.  
  
6.  Type the name of the field, starting the name with the first three digits of the segment name, followed by a period and the number of the field, followed by an underscore and then a short description of the field. The description should be one or a series of words, without spaces, with the first letter of each word capitalized. Press **Enter**.  
  
7.  In the Properties pane, type the properties you want for the Z segment, including **Data Type**, **Nillable**, **Fixed**, **Max Occurs**, and **Min Occurs**.  
  
8.  To create a field with components, create the field as a record, and then create a child element of that record for each component. To create a field with subcomponents, create the field and components as records, and the subcomponents as child elements. Note that subcomponents cannot be composite data types. For example, for the segment named ZPP_PatientPreferencesSegment, you might create a ZPP.1_Dietary field and a PD.1 Allergies component with a PD.1.1_FoodGroupAllergy subcomponent. The PD.1.1_FoodGroupAllergy subcomponent would have to be a simple data type.  
  
## See Also  
 [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)   
 [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)   
 [Handling Undeclared Z Segments](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)