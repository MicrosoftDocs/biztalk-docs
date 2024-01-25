---
description: "Learn more about: Flat File Message Trailers"
title: "Flat File Message Trailers"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Flat File Message Trailers
As with flat file instance message headers, the parsing of the optional flat file instance message trailer by the flat file disassembler is controlled by the flat file schema that you have configured in the **Trailer schema** design-time property of the flat file disassembler or the **XMLNORM.TrailerSpecName** message context property. If you have not specified a schema using one of these two methods, the flat file disassembler will assume that the flat file instance message does not contain a trailer.  
  
 Unlike with flat file instance message headers, flat file instance message trailers can neither be saved and restored as a single unit, nor can they use property promotion to copy individual items of data to the message context associated with the flat file instance message body. However, a trailer can be added to an outbound flat file instance message by specifying the appropriate schema in the **Trailer schema** design-time property of the flat file assembler or the **XMLNORM.TrailerSpecName** message context property. The data that constitutes the variable portion of the trailer can be specified using property demotion from the message context of the flat file instance message body, or by specifying default or fixed values in the corresponding schema.  
  
## See Also  
 [Flat File Message Headers](../core/flat-file-message-headers.md)   
 [Flat File Message Bodies](../core/flat-file-message-bodies.md)   
 [Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md)   
 [How to Create Schemas for Flat File Messages](../core/how-to-create-schemas-for-flat-file-messages.md)
