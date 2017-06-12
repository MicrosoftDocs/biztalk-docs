---
title: "Trigger Events and Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "health care organizations, HL7 messages"
  - "trigger events"
  - "messages, trigger events"
  - "messages, about messages"
ms.assetid: e93b397c-8cbe-4589-aa88-e474d7722174
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Trigger Events and Messages
In a digital health care system, applications create HL7 messages because of a real-world event, such as the placing of a laboratory order or drug order. The HL7 organization has written the HL7 standard based on the assumption that an event in the real world of health care creates the need for data to flow among applications, even when these applications span heterogeneous systems. The HL7 standard calls this real-world event a *trigger event*. An automated system must systematically recognize the trigger event.  
  
 To expand this concept, consider the following scenario. On arrival at a hospital, a patient registers in a hospital using a patient administration software application. On committing the patient records, the application needs to inform other hospital applications (such as accounting, labs, and so on) about the registration of the patient. Sharing this information across applications is necessary so that the entities that use those applications can provide the patient with the required services. The act of registering a patient is a type of trigger event. A Web application typically creates this trigger event by creating an HL7 message containing the data for the patient record.  
  
 Trigger events always result in the creation of one or more messages that trigger an action in the application that processes the message. Trigger events are relevant in deployment scenarios where IT personnel have embedded [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) within the hospital line-of-business application. Even in such deployment scenarios, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not need to be aware of the trigger event, only the messages that the trigger event generates.  
  
## See Also  
 [Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [HL7 Messaging](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)