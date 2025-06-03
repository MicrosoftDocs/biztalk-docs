---
description: "Learn more about: Validating Messages"
title: "Validating Messages"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: concept-article
---
# Validating Messages
Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) supports sending acknowledgments (ACK) for inbound messages from an application or trading partner in the form of an HL7 XML receipt that might need conversion to an HL7 encoded ACK message. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] typically generates a receipt after it checks the inbound message against the relevant inbound (trading-partner format) document specification. When all the segments pass validation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] returns a receipt that indicates acceptance to the application. Otherwise, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates a receipt indicating error or failure/reject.  
  
 The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ACK transmission reports syntactical and schematic errors against the HL7 standard. If the validation fails, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] places the document in the suspended message queue and returns a receipt detailing the rejection. The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parser performs validation that involves checking data types, syntax, and the schema validation. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] records any schematic errors that occur in parsing in the receipt along with the location details.  
  
 At configure time, you need to create the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] artifacts required for responding with an ACK. The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] parser creates the HL7 canonical ACK XML instance. BizTalk converts this to the required version format in an appropriate BizTalk map and validates the destination format. The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer then converts the message into an HL7-encoded instance.  
  
> [!NOTE]
>  If there is a conflict between the delimiters of an inbound message and those specified in the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] configuration, then [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will generate an ACK message that uses the same delimiters of the inbound message and overrides the configuration settings.  
  
## See Also  
 [Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [ACK Message Modes](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)
