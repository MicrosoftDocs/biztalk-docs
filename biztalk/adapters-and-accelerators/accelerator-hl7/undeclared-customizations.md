---
description: "Learn more about: Undeclared Customizations"
title: "Undeclared Customizations"
ms.date: "06/08/2017"
ms.prod: biztalk-server
ms.topic: article
---
# Undeclared Customizations
You can add data to a message without defining the format or nature of the data. You do so by using undeclared Z segments. Undeclared Z segments are unexpected instances at the end of a message. The parser/XML validator does not validate the segment. It is not defined by any schema. Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) treats the segment as a binary large object (BLOB).  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] passes undeclared Z segment data through as the third part of a three-part message. The three parts are the header, the body, and the undeclared Z segment, also called the Z part. A segment ID beginning with the letter "Z", for instance, "ZPD" for custom patient demographics information, identifies the Z part.  
  
## See Also  
 [Declared Customizations](../../adapters-and-accelerators/accelerator-hl7/declared-customizations.md)   
 [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)
