---
title: "Flat File Message Headers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1981daaf-149a-426d-9a2f-5fcf64bce185
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Flat File Message Headers
The parsing of the optional flat file instance message header by the flat file disassembler is controlled by the flat file schema that you have configured in the **Header schema** design-time property of the flat file disassembler or the **XMLNORM.HeaderSpecName** message context property. If you have not specified a schema using one of these two methods, the flat file disassembler assumes that the flat file instance message does not contain a header.  

## Outbound messages  
 For outbound flat file instance messages, you can configure the flat file assembler to produce a header by specifying the appropriate schema in its **Header Specification Name** design-time property or the **XMLNORM.HeaderSpecName** message context property. For more information about setting message context properties, see **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  

## Inbound messages  
 Data found in inbound flat file instance message headers can be preserved and utilized in two different ways. First, flat file instance message headers can be saved in their entirety within the message context of the body for later restoration as the header of a corresponding outbound flat file instance message. You can use the **Preserve header** property of the receive pipeline to specify that the header should be preserved. And if a header is specified in the flat file assembler, the preserved header will be used on the outbound message.  
  
 Second, individual items of data from a flat file instance message header can be copied to the message context associated with the flat file message body by specifying property promotion for one or more of the fields in the corresponding schema. For more information about promoting properties, see [Promoting Properties](../core/promoting-properties.md).  
  
## See Also  
 [Flat File Message Bodies](../core/flat-file-message-bodies.md)   
 [Flat File Message Trailers](../core/flat-file-message-trailers.md)   
 [Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md)   
 [How to Create Schemas for Flat File Messages](../core/how-to-create-schemas-for-flat-file-messages.md)