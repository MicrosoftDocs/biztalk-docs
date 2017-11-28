---
title: "Creating Custom Data Types in Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "2.X schemas, creating Z data types [Z objects]"
  - "data types, creating [Z objects]"
  - "Z objects, creating Z data types"
ms.assetid: e545c849-d414-4d5d-bb56-d3f9d5238c70
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Custom Data Types in Schemas
You can create a custom data type in the datatypes_\<*version*\>.xsd common schema. You can base a custom data type on an existing data type, a base data type, or on an enumeration defined in a table.  
  
### To create a Z data type  
  
1.  In Solution Explorer of Visual Studio, open the common data-type schema file (**datatypes_\<*version*\>.xsd**), and then click **Open**.  
  
2.  In BizTalk Editor, right-click **HL7DefinedDataTypes**, point to **Insert Schema Node**, and then click **Child Record** to create a component data type, or click **Child Element** to create a simple data type.  
  
3.  Name the data type with a three-character tag starting with "Z".  
  
4.  In the Properties pane, type the values you want for **Base Data Type**, **Data Type**, and other properties, as needed.  
  
## See Also  
 [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)   
 [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)   
 [Handling Undeclared Z Segments](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)