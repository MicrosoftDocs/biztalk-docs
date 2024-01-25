---
description: "Learn more about: Flat File Message Bodies"
title: "Flat File Message Bodies"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Flat File Message Bodies
A flat file instance message body, which is required, is what the flat file disassembler processes into one or more XML instance messages. To know what data to expect in an inbound flat file instance message body, you must configure the flat file disassembler with the flat file schema that corresponds to the body. You can specify the schema by using the **Document schema** design-time property of the flat file disassembler or the **XMLNORM.DocumentSpecName** message context property. Because flat file instance messages must have a body part, you must configure the appropriate schema using one of these two methods.  
  
 For outbound flat file instance messages, the flat file assembler can dynamically determine the appropriate flat file schema for the body of the instance message. The flat file assembler determines the appropriate schema from the message type, which is a combination of the target namespace and the name of the root element, both of which must be present in the XML version of the outbound message. Alternatively, you can explicitly configure the flat file schema to be used by configuring the **Document schema** design-time property of the flat file assembler or the **XMLNORM.DocumentSpecName** message context property.  
  
 Data found in inbound flat file instance message bodies can be copied to the corresponding message context by specifying property promotion in the flat file schema being used by the flat file disassembler to process the inbound instance message. Likewise, data in the message context can be copied back into outbound flat file instance messages by specifying property demotion in the flat file schema being used by the flat file assembler to process the outbound message.  
  
## See Also  
 [Flat File Message Headers](../core/flat-file-message-headers.md)   
 [Flat File Message Trailers](../core/flat-file-message-trailers.md)   
 [Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md)   
 [How to Create Schemas for Flat File Messages](../core/how-to-create-schemas-for-flat-file-messages.md)
