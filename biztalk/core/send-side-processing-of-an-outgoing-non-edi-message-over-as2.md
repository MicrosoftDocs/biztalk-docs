---
title: "Send-Side Processing of an Outgoing Non-EDI Message over AS2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f19b7df-fe6d-4105-8a44-3d6db0bba451
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Send-Side Processing of an Outgoing Non-EDI Message over AS2
The AS2 pipelines shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be used to process an EDI message or a non-EDI message over AS2 transport. Different pipelines are used for the two different types of payloads. You use the AS2EdiSend pipeline to process an outgoing EDI message over AS2, and the AS2Receive pipeline to receive the associated MDN (if enabled). You use the AS2Send pipeline to process an outgoing non-EDI message over AS2, and the AS2Receive pipeline to receive the associated MDN (if enabled). The non-EDI message can be any binary payload.  
  
 The AS2Send send pipeline assembles the non-EDI payload and encodes the AS2 message. The AS2Receive receive pipeline decodes the MDN response. You can include these pipelines in an HTTP two-way solicit response send port (for synchronous MDNs), or in a one-way HTTP send port and a one-way HTTP receive port (for asynchronous MDNs).  
  
 To send an EDI interchange over AS2, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will perform the following steps:  
  
-   Processing the non-EDI payload for sending  
  
-   Sending the AS2 message  
  
-   Receiving the returned MDN  
  
## Processing the Non-EDI Payload for Sending  
 Before creating the AS2 message, a send port must pick up the non-EDI payload, using an appropriate filter expression to subscribe to the messages. You can use a two-way send port or a one-way send port, depending upon whether the MDN will be synchronous or asynchronous. The AS2Send pipeline will then process the non-EDI payload into an AS2 message.  
  
## Sending the AS2 Message  
 The AS2 Encoder in the AS2 send pipeline first performs agreement resolution to determine the agreement properties to be used to process the outgoing message. For more information, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).  
  
 The AS2 Encoder builds the set of HTTP headers required to send an AS2 message. It adds these headers to the `HTTP.UserHttpHeaders` context property, which is a single string of header values. The AS2 Encoder builds the following AS2 headers in HTTP.UserHttpHeaders. These headers must be in the AS2 messages.  
  
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
  
## See Also  
 [How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md)