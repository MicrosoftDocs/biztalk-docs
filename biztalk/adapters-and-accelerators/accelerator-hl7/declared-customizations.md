---
title: "Declared Customizations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "declared customizations"
  - "Z objects, declared customizations"
  - "customizing, Z objects"
  - "customizing, declared customizations"
ms.assetid: 484655e9-8bfa-4643-bbe6-4ef69cbd83ad
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Declared Customizations
With declared customizations, you have the flexibility of modifying or adding to HL7 messages. You can even define a new type of message. You can do this in any of the following ways:  
  
- Changing the definition of a message by defining a new message type or trigger event  
  
- Adding a new segment to an existing message type  
  
- Changing the data type of an existing message part (segment, field, component, or subcomponent)  
  
- Changing the potential values that you can use in an existing message part  
  
  > [!NOTE]
  >  You can change the enumeration values used in declared Z objects or the standard objects in HL7 schemas. To do so, see [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md).  
  
  You modify or add to HL7 messages by adding, maintaining, and associating custom objects within the currently defined message types. The HL7 standards call these custom objects "Z objects" to distinguish them from existing objects that conform to the HL7 standard. You use BizTalk Editor to define Z objects. You also use BizTalk Editor to work with features that propagate updates to a Z object across all the trigger events and abstract messages that include it. For more information about creating Z objects, see [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md).  
  
  You can use Z objects to give local definitions to segments that you use in ways not specified in the HL7 standard. You make these changes to the schemas that the BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Setup Wizard installed on your computer. You can then share these modified schemas with other [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] installations with which you exchange messages.  
  
## Types of Z Objects  
 The HL7 standard (2.X) currently supports the following forms of customization:  
  
-   **Custom trigger events.** If you are at a local area and need a new message structure, or want to support a trigger event that is not included within the standard, you can create a new trigger event using a Z prefix, for example, Z05. In this case, you must create a new local message schema by defining the abstract message and the pattern of included segments.  
  
-   **Custom segments.** If you are at a local area, in the context of an already supported trigger event, and in need of additional data, you can create a new segment or segments and include the wanted data elements within the segment. You must specify the elements within the segment using existing HL7 data types. You can create custom Z segments in BizTalk Editor, by creating a new record in the schema. For more information, see [Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md). Alternatively, you can add a Z segment through the Access database, and then adding that Z segment to the message structure. For more information, see [Resolving Database Errors](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md).  
  
-   **Custom data subtypes.** HL7 provides a list of supported data types, for example, formatted text, scanned image, audio data. However, if you want to define additional data types, you can do so by prefixing the mnemonic used with a "Z", thereby creating a Z data type.  
  
    > [!NOTE]
    >  It is not permissible, within the confines of the standard, to create new data types or to add elements to an existing segment. Still less is it permissible to take an element that is not currently used and to redefine it to meet some additional purpose. On the other hand, organizations that support legacy interfaces may need to accommodate such practices.  
  
-   **Custom tables.** Many existing objects within messages have a limited range of specific values, as defined by enumerations in tables defined by HL7 common schemas. You can modify these enumerations to enable additional values by creating Z tables.  
  
## See Also  
 [Undeclared Customizations](../../adapters-and-accelerators/accelerator-hl7/undeclared-customizations.md)   
 [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)