---
title: "MDN Messages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 16ac6253-0be5-4636-b102-bf5af8956261
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MDN Messages
The Message Disposition Notification (MDN) is the acknowledgment sent in response to an AS2 message. If an MDN is enabled, the AS2 transmission is not complete until the MDN has been received and verified. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will always attempt to return an MDN to indicate the status of message processing, even if an error occurred in processing the AS2 message.  
  
 The MDN provides verification of the following:  
  
-   **That the original message was successfully received by the receiving party**. The sender of the original message verifies this by comparing the MessageID of the original sent message with the original-message-id field that the receiver included in the MDN.  
  
-   **That the integrity of the data exchanged was verified by the receiving partner**. The sender of the original message verifies this by comparing the MIC that was calculated from the original sent message payload, with the MIC that the receiver calculated on the received message payload and included in the Received-content-MIC field of the MDN (if signed).  
  
-   **That there is a non-repudiation of receipt**. The sender does this by verifying the signed MDN with the receiving partner's public key, and by verifying that the returned MIC value in the MDN is the same as the MIC for the original message payload stored in the non-repudiation database.  
  
    > [!NOTE]
    >  A synchronous MDN serves as an HTTP Response, e.g., 200 OK.  
  
    > [!NOTE]
    >  For more information about receive-side processing of MDNs, see [Processing an Incoming MDN](../core/processing-an-incoming-mdn.md). For more information about send-side processing of MDNs, see [Sending an Outgoing MDN](../core/sending-an-outgoing-mdn.md).  
  
## Properties Used to Generate the MDN  
 The AS2Receive receive pipeline will generate an MDN using a party's AS2 agreement properties if the **Use agreement settings for validation and MDN instead of message header** property is selected on the one-way agreement tab in the **Agreement Properties** dialog box. In this instance, the AS2-From property in the message header will be used in generating the MDN, but other properties will be taken from the party's AS2 agreement settings.  
  
 If the option to override AS2 property is not selected, or the party’s AS2 agreement is available, the receive pipeline will generate the MDN using the AS2 header tags in the incoming message.  
  
 An MDN can be signed, but it cannot be encrypted or compressed.  
  
## MDN Context Properties  
 Context properties used in processing MDN messages include properties that can be promoted as well as properties that are not publicly exposed, but can be viewed in suspended and tracked messages. For a list of these context properties, see [AS2 Context Properties](../core/as2-context-properties.md).  
  
 Both the DispositionMode and DispositionType context properties must be promoted in order for an MDN to be generated. If an error occurs in the AS2 or EDI payload, the DispositionType property will indicate the error. You can see this property in the **Message Details** dialog box that is displayed (via the Service Details dialog box) from the Suspended service instances in the **Group Hub** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. If an error occurs in the header, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will indicate the error in the DispositionType property, and will attempt to send the MDN, but depending on the error, may not be able to do so.  
  
## MDN Headers  
 The MDN contains the following headers:  
  
- **HTTP/AS2 headers**. For more information, see [AS2 Messages](../core/as2-messages.md).  
  
- **Transfer Layer**. This includes the Content-Type header that includes the signed multipart message, the algorithm for the MIC, the signature formatting protocol, and the outermost multipart boundary sub-headers.  
  
- **First Part**. The first part of the multipart signed message is the embedded MDN. It is human readable.  
  
- **Second Part**. The second part of the multipart signed message contains the digital signature, a reference to the original message, the disposition type and status, and the MIC value. It is machine readable.  
  
  The AS2-From header, AS2-To header, and MessageID context property are used to correlate an MDN to the AS2 message that it is responding to. The Original-Message-ID header in an MDN comes from the Message-ID header of the AS2 message that the MDN is responding to.  
  
## MIC  
 The Message Integrity Check (MIC) is used to verify that an MDN correlates to the original sent message payload. The MIC digest is included in the Received-Content-MIC extension field in the second part of the multipart signed MDN message.  
  
 If an MDN is enabled, when the AS2 send pipeline processes an outbound message, it computes a MICHashValue from the message payload. The send pipeline saves the hash value in the EdiInt_Mic table of the BizTalkMsgBoxDb database. AS2 messages are tracked in this table, identified uniquely by the AS2From, AS2To, and MessageID values, with an accompanying MICHashValue column. The receiver of the message calculates the MIC hash value when it processes the message payload, and includes the hash value in the MDN that it returns. The sender of the original message will compare the MIC hash value in the MDN that it receives with the hash value that it saved. If they match, it disposes of the MDN, deletes the entry in the EdiInt_Mic table, and the transmission is complete.  
  
 The MIC is base64 encoded. The algorithm to be applied for the MIC can be SHA1 or MD5. It is determined from the **Signing Algorithm** drop-down (enabled if **Request Signed MDN** property is checked) in the **Sender MDN Settings** page of the one-way agreement tab in the **Agreement Properties** dialog box. It is also determined from the Signed-Receipt-MICalg AS2 header of the original message.  
  
## See Also  
 [AS2 Messages](../core/as2-messages.md)   
 [Processing an Incoming MDN](../core/processing-an-incoming-mdn.md)   
 [Sending an Outgoing MDN](../core/sending-an-outgoing-mdn.md)