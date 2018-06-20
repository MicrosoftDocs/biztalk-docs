---
title: "Send-Side Processing of an Outgoing EDI Message over AS2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfb63b22-6e2e-4d4f-b028-301c8d4d53b0
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Send-Side Processing of an Outgoing EDI Message over AS2
Send-side processing of an EDI message over AS2 includes sending an AS2 message with the EDI payload and receiving MDN and EDI acknowledgments (if enabled).  
  
 The AS2EDISend send pipeline sends an assembled EDI/AS2 message to the receiving trading partner over HTTP/HTTPS. The AS2EDIReceive receive pipeline receives an MDN returned in response to the AS2 message, and an EDI acknowledgment returned in response to the EDI message. Each of these pipelines processes an AS2 message and processes the EDI payload within an AS2 message. You can include these pipelines in an HTTP two-way solicit response send port, or in a one-way HTTP send port and a one-way HTTP receive port.  
  
 To send an EDI interchange over AS2, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will perform the following steps:  
  
-   Processing the EDI payload for sending  
  
-   Sending the AS2 message  
  
-   Receiving the returned MDN  
  
-   Receiving the returned EDI acknowledgment  
  
## Processing the EDI Payload for Sending  
 Before creating an AS2 message, the AS2EdiSend pipeline must process the EDI interchange. If outbound batching is enabled, transaction sets will be batched as described in [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md). The EDI Assembler will create the EDI interchange as described in [How the EDI Assembler Works](../core/how-the-edi-assembler-works.md).  
  
## Sending the AS2 Message  
 The AS2 Encoder in the AS2 send pipeline first performs agreement resolution to determine the agreement properties to be used to process the outgoing message. For more information, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).  
  
 The AS2 Encoder builds the set of HTTP headers required to send an AS2 message. It adds these headers to the `HTTP.UserHttpHeaders` context property, which is a single string of header values. The AS2 Encoder builds the following AS2 headers in `HTTP.UserHttpHeaders`. These headers must be in the AS2 messages.  
  
- AS2-To  
  
- AS2-From  
  
- AS2-Version  
  
- MessageID  
  
- OriginalMessageID (for MDNs only)  
  
  If the **Request MDN** property is checked, the pipeline will set the Disposition-Notification-To, Receipt-Delivery-Option, and Signed-Receipt-MICalg AS2 headers in the message to the values in the corresponding properties; and it will set the Signed-Receipt-Protocol AS2 header to "pcks7-signature" if the **Request signed MDN** property is checked.  
  
  If the `HTTP.UserHttpHeaders` context property does not exist, the AS2 Encoder will create it. If `HTTP.UserHttpHeaders` already exists, the AS2 Encoder will use it, rather than creating it. If you create `HTTP.UserHttpHeaders`, write headers to it, and then write it to the context of the message, the AS2 Encoder will use those headers, and they will take priority over headers from other sources. The exception to that is the AS2-From header, which is always taken from the agreement properties.  
  
  If an AS2 header is not in `HTTP.UserHttpHeaders`, the AS2 Encoder will add it from single context properties. This means that you can add AS2 headers by promoting or writing them to the context of the message (if they are not already in `HTTP.UserHttpHeaders`). If an AS2 header is neither in `HTTP.UserHttpHeaders`, nor present as a property in the context, the AS2 Encoder will add it from agreement properties into `HTTP.UserHttpHeaders`.  
  
  After the AS2 Encoder builds the headers in the `HTTP.UserHttpHeaders` property, it writes it to the context of the message. The HTTP Adapter picks up `HTTP.UserHttpHeaders`, and prepends the header values from `HTTP.UserHttpHeaders` into the message.  
  
> [!NOTE]
>  AS2 transport is intended to work only with the HTTP adapter. However, if you manually set the appropriate context properties, you can use the FILE Adapter to transport AS2 messages. For more information, see [Sending an AS2 Message over a FILE Send Port](../core/sending-an-as2-message-over-a-file-send-port.md).  
  
## Processing the Returned MDN  
 If an MDN is enabled, the receive pipeline associated with the two-way send port receives the MDN from the party that receives the AS2 message.  
  
> [!NOTE]
>  For more information about the processing that the AS2 send pipelines perform on incoming MDNs, see [Sending an Outgoing MDN](../core/sending-an-outgoing-mdn.md).  
  
## Processing the Returned EDI Acknowledgment  
 If an EDI acknowledgment is enabled, the receive pipeline associated with the two-way send port also receives an EDI acknowledgment from the receiver of the EDI message (because it filters on the BizTalk EDI ACK message type). For more information, see [Processing a Received Acknowledgment](../core/processing-a-received-acknowledgment.md).  
  
## See Also  
 [How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md)