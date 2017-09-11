---
title: "Extending HL7 2.X Schemas with Z Objects | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "2.X schemas, Z objects"
  - "Z objects, extending 2.X schemas"
ms.assetid: 0980d919-eb81-4c65-b0f7-f17f7cfef6b3
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Extending HL7 2.X Schemas with Z Objects
The HL7 organization defines HL7 2.X schemas, and expects all senders and receivers to recognize and use these schemas as the organization defines them. Conforming to the schemas ensures for interoperability. However, the HL7 standard enables you to customize existing HL7 2.X schemas for your specific local purposes. You can also define entirely new schemas and objects. You do so with what the HL7 standard calls Z objects.  
  
 The HL7 standard does not define the value of Z objects. The published HL7 schemas do not include them. You define them locally, and use them by agreement with all local parties. The HL7 organization reserves all message type, trigger event, segment, data type, and table names beginning with "Z" for this local use. Because of the prefix, the HL7 standard calls these site-defined objects Z objects.  
  
> [!NOTE]
>  When you add a Z object to an existing HL7-defined schema, you may end up with multiple versions of that schema. The best way to handle these multiple versions is to use the Namespace feature in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. You can find this feature on the **Validation** tab in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer (at the party level). You will also need to change the namespace property within the schema that you deploy for that project.  
  
 In creating or processing Z objects, you should follow the rules that the HL7 organization has established for Z objects..  
  
 When you add a Z object to an existing schema or create a new Z message schema, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will use the schema with the Z object(s) to process the HL7-encoded message. This type of Z object is a declared Z object. You can also use an undeclared Z segment, which the integration engine will not process according to the message schema. For more information about this type of Z segment, see [Handling Undeclared Z Segments](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md).  
  
## In This Section  
  
-   [Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)  
  
-   [Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)  
  
-   [Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)  
  
-   [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)  
  
-   [Customizing Messages through Z Objects](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md)