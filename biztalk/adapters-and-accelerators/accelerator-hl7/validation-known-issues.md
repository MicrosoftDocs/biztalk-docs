---
description: "Learn more about: Validation Known Issues"
title: "Validation Known Issues"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: article
---
# Validation Known Issues
This section contains useful information that may help you avoid validation errors.  
  
## Disabling XML validation  
 The "Validate Body Segments" flag in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer controls the XML body validation and does not include validation of unexpected delimiters and trailing delimiters. If a message does not have the proper delimiters, the message cannot be successfully parsed. If a message cannot be successfully parsed, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] cannot generate valid intermediate XML. Disabling the "Validate Body Segments" flag results in the following:  
  
1.  Empty required fields.  
  
2.  Data types not validated.  
  
3.  Segment structure is not validated (order of segments is not validated).  
  
## V2.XML ACKs with multiple errors will fail validation  
 If an incoming V2.XML message contains more than one error, the Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) parser may generate a V2.XML acknowledgment (ACK) with more than one error in the error field. Such a V2.XML ACK will fail validation, because the HL7 standard specifies that the parser can report only one error in a V2.XML ACK error field.  
  
## Two parsing errors are logged when messages in the Batch In/Batch Out scenario contain validation errors  
 When the first message in the Batch In/Batch Out scenario (multiple messages batched without batch headers) contains validation errors, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logs two errors in the Event Log. The first error pertains to the first message in the batch, and the second error pertains to the remainder of the messages.  
  
## Restrictions in validating field length  
 Fields associated with HL7 complex data types are comprised of components and subcomponents. HL7 rules specify the length and optionality at the field level and not at the component/subcomponent level. For example in V2.4, HL7 governs MSH3 to be of HD data type and 180 characters maximum length. HD is a composite data type with HD1 set as IS, HD2 set as ST, and HD3 set as ID. The field length restriction implies that the data in the three components (including the two component separators) should be less than or equal to 180. However, the optionality of the three data types is not specified; which means that all or some components may exist. Additionally, data types ST and IS are user defined and therefore [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] cannot be aware of the length distribution across the three components, since these are normally site defined.  
  
 Due to these and other complications, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not validate the field length. However, you can apply length restrictions at each individual component/subcomponent (of data type simple) using BizTalk Editor in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will validate these during processing.  
  
## Validation of batch and file headers/trailers are affected by enabling fragmentation  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not validate batch and file headers/trailers when the FHS3 field contains a party that has fragmentation enabled.  
  
## See Also  
 [Known Issues](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)
