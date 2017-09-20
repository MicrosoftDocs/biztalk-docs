---
title: "EDI Headers and Trailers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cf1dae3-9570-413d-a85d-94dcbb561906
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# EDI Headers and Trailers
The parts of an EDI interchange are delimited by headers and trailers that must conform to the X12 or EDIFACT standards. The interchange control header and trailer occur just once; the functional group and transaction set headers and trailers are repeated if the transaction sets and groups are batched within the interchange. Each of the headers and trailers consists of a series of data elements that contain information about the content that the header and trailer contain.  
  
 The headers and trailers for both X12 and EDIFACT are similar. The major difference is the UNA Service String Advice header for EDIFACT, which defines the separators used in the interchange. In X12 encoding, the separators are defined in the ISA Interchange Control Header.  
  
 The interchange control and functional group headers and trailers are denoted as envelope segments. When BizTalk Server splits an incoming interchange as transaction sets, it saves these envelope segments as context properties. Key envelope properties that are useful for routing are available as individual properties. This does not occur when the interchange is preserved, in which case the envelope data is part of the message itself.  
  
 When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates an outgoing message, it bases the headers and trailers on trading partner agreements (or global agreements if no party has been determined).  
  
 The header and trailer fields, and the separator characters used to separate them in interchanges, are both defined in the agreement between the two parties. A separator character must not be used in the definition of any of the interchange, group, or transaction set header or trailer fields, as defined for the agreement. If they are, the interchange will fail processing either in the EDI Assembler of the sending [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or in the disassembler of the receiving party. The interchange will fail in the EDI Assembler if it is an outbound batch, because the Assembler will validate the envelope against the header control (service) schema. If the interchange is unbatched, the EDI Assembler will serialize it, but it will fail processing in the disassembler at the receiving agreement.  
  
## X12 Headers and Trailers  
 The headers and trailers for an X12-encoded message are as follows:  
  
```  
ISA Interchange Control Header  
  GS Functional Group Header  
    ST Transaction Set Header  
    SE Transaction Set Trailer  
  GE Functional Group Trailer  
IEA Interchange Control Trailer  
```  
  
 If an ISA header is followed immediately by an IEA trailer, the interchange is empty. If a transaction set exists, the GS header and GE trailer must be present; otherwise, they are conditional.  
  
 The ISA interchange control header fields in an X12-encoded message are of fixed length. For some of the fields, you can enter a value less than the fixed length of the field. If you do so, the interchange must contain trailing spaces (for a string field) or leading zeroes (for a numerical field) so that each field is of the required length. When creating an outbound interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will enter trailing spaces or leading zeroes to create an interchange control header of the right length. The GS group header fields and the ST transaction set header fields are not of fixed length.  
  
 In X12 encoding, the functional security header, functional assurance header, functional security value segment, and functional security trailer segments are beyond the scope of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2. If an interchange with these segments is received, it will be suspended with an error log indicating that these are unidentified segments.  
  
 The ST01 field is the transaction set ID Code; the ST02 field is the transaction set control number. The ST03 field is the schema version identifier. The SE01 field indicates the number of segments included in the transaction set; the SE02 field is the same as the ST02 field (the transaction set control number). When parsing an incoming message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will verify that the number of segments in the transaction set corresponds to the value of the SE01 field. When generating an outgoing message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will set the SE01 field to the correct number of segments in the transaction set.  
  
 An XML transaction set being serialized into an outgoing EDI interchange should have a transaction set header and trailer. However, the EDI Assembler will process the message if it does not have a transaction set header or trailer. Transaction set header and trailer segments in X12 and EDIFACT schemas are optional for XML transaction sets. If a transaction does not have a header or trailer, the EDI Assembler in the EDISend or AS2EDISend send pipeline will add transaction set header and trailer values to it. These values will be based on mappings or calculations. The EDI Assembler will do this for interchange XML (a preserved batch), batched transaction set XML, and transaction set XML. For more information, see [X12 Transaction Set Header and Trailer Segments](../core/how-the-edi-assembler-works.md#BKMK_X12) or [EDIFACT Transaction Set Header and Trailer Segments](../core/how-the-edi-assembler-works.md#BKMK_EDIFACT).  
  
## EDIFACT Headers and Trailers  
 The headers and trailers for an EDIFACT-encoded message are as follows:  
  
```  
UNA Service String Advice  
UNB Interchange Control Header  
  UNG Functional Group Header  
    UNH Message Header  
    UNT Message Trailer  
  UNE Functional Group Trailer  
UNZ Interchange Control Trailer  
```  
  
 The UNA header is not required. The UNB header is required. If the UNA header is present, it contains the delimiters to use when processing the incoming message; otherwise the separators defined for the EfactDelimiters pipeline property will be used.  
  
 If a UNB header is followed immediately by a UNZ trailer, the interchange is empty. If a UNG header is followed immediately by a UNE trailer, the group is empty. The UNG header and UNE trailer pair are conditional and do not have to be present in a message.  
  
## See Also  
 [EDI Message Structure](../core/edi-message-structure.md)