---
description: "Learn more about: Message Types and Events"
title: "Message Types and Events"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: concept-article
---
# Message Types and Events
The HL7 standard has grouped messages that relate to a particular grouping of real-world events together as *message type* ADT. These messages involve trigger events, such as patient administration. Version 2.4 of the HL7 standard defines more than 100 message types, each of which the HL7 organization has assigned a unique three-character message type code. As versions of the HL7 standard have evolved, the HL7 organization has added new message types to provide new capabilities.  
  
 All message types contain message events, also called *events*. You can think of an event as a unique type of message grouped within a particular message type. For example, the Admin/Visit Notification (message event A01) and Discharge/End Visit (message event A03) are unique messages contained by the Patient Administration message type (ADT). The HL7 organization has assigned each message event a unique three-character event code.  
  
 Only one message type can contain a particular message event. Message types can contain multiple message events. However, the structure of a particular message event can vary between versions of the HL7 standard.  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [Trigger Events and Messages](../../adapters-and-accelerators/accelerator-hl7/trigger-events-and-messages.md)   
 [HL7 Messaging](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)
