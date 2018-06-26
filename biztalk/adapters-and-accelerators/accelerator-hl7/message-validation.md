---
title: "Message Validation | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "validating, messages"
  - "messages, validating"
ms.assetid: 720ab16a-7ab4-4741-9951-9ab10a2c4c24
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Validation
Message validation occurs for incoming and outgoing HL7 messages with HL7 2.X receive and send pipelines. You can configure validation for only the MSH (header) segment, or for the entire message body. In addition, it is possible to validate against unique localized versions of the schema. You accomplish this by defining a unique namespace value, and using this namespace value within both the HL7 messaging configuration (at the party level) and the target namespace property of the actual schema that defines the message. At run time, Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses the combination of namespace and the root reference property for the schema to select the appropriate schema for message parsing and validation.  
  
 The parser and serializer perform validation based on the settings for the party associated with a message. Other party settings, including batching, acknowledgment, and message-header override affect how the parser or serializer performs validation.  
  
> [!NOTE]
>  The serializer performs a series of steps, including (if applicable) performing header overrides from an MSH map, and performing XML validation. If the header override and validation processes are both enabled, and the header override process enters an incorrect value into a header field, the message will fail validation, even if the message were to pass body validation.  
  
## See Also  
 [MSH Override](../../adapters-and-accelerators/accelerator-hl7/msh-override.md)