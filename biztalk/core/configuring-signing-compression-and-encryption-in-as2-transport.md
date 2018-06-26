---
title: "Configuring Signing, Compression, and Encryption in AS2 Transport | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc3537a7-c065-4a33-a375-29e7902b5ffa
caps.latest.revision: 15
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Signing, Compression, and Encryption in AS2 Transport
You can configure digital signatures, signature verification, encryption, and decryption from within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console. This configuration requires that you set the appropriate properties for the AS2 pipelines and BizTalk parties.  
  
## Using AS2 Pipelines  
 To help secure an inbound AS2 message, use an AS2 receive pipeline (AS2EdiReceive or AS2Receive) in your receive location. The AS2 Decoder decrypts, decompresses, and/or performs signature verification on AS2 messages. For more information on how it does so, see the "AS2 Decoder" section of [AS2 Receive Components](../core/as2-receive-components.md).  
  
 To help secure an outbound AS2 message, use an AS2 send pipeline (AS2EdiSend or AS2Send) in your send port. The AS2 Encoder signs, compresses, and encrypts outbound AS2 messages. For more information on how it does so, see the "AS2 Encoder" section of [AS2 Send Components](../core/as2-send-components.md).  
  
> [!IMPORTANT]
>  Once a message has been signed, the signature blob must not be changed. If changed, the signature would be corrupted. The boundary header, or anything outside the boundary headers, can be changed, but anything within the boundary headers must not be changed.  
  
## Setting AS2 Agreement Properties  
 You configure signature and encryption processing by setting AS2 agreement properties as follows:  
  
- To sign, compress, and/or encrypt an outbound message, check the **Message should be signed**, **Message should be compressed**, and **Message should be encrypted** properties on the **Validation** page of the one-way agreement tab (for the outgoing AS2 message) in the **Agreement Properties** dialog box.  
  
- To request a signed MDN in response to an outbound message, check the **Request MDN** and **Request signed MDN** properties on the **Acknowledgements (MDNs)** page of the one-way agreement tab of the **Agreement Properties** dialog box.  
  
- To specify that an inbound message is signed, compressed, and/or encrypted, check the **Use agreement settings for validation and MDN instead of message header** property, the **Message should be signed** property, the **Message should be compressed** property, and the **Message should be encrypted** property on the **Validation** page of the one-way agreement tab (for the incoming AS2 message) in the **Agreement Properties** dialog box.  
  
  > [!NOTE]
  >  When the **Use agreement settings for validation and MDN instead of message header** property is selected, all header details of the incoming message are ignored and the message is processed based on the agreement settings.  
  
- To specify a signed MDN in response to an inbound message, when the inbound message properties are overridden by selecting the **Use agreement settings for validation and MDN instead of message header** property, check the **Request Signed MDN** property on **Acknowledgements (MDNs)** page of the **Agreement Properties** dialog box.  
  
  > [!NOTE]
  >  When the **Use agreement settings for validation and MDN instead of message header** property is selected, all header details of the incoming message are ignored and the message is processed based on the agreement settings.  
  
- To specify a signed MDN in response to an inbound message, when the inbound message properties are not overridden (the **Use agreement settings for validation and MDN instead of message header** is cleared), but the message headers do not specify signing, check the **Sign requested MDN if Disposition-Notification-Option header is not present or if Signed-Receipt-Protocol header is set to optional** property on the **Receiver MDN Settings** page of the **Agreement Properties** dialog box.  
  
- To specify a different signing certificate than the one specified in the BizTalk Group properties for outgoing AS2 messages, select **Override Group Signature Certificate** in the **Signature Certificate** page of the one-way agreement tab of the **Agreement Properties** dialog box, and specify a signing certificate. If this property is set, whichever AS2 message that resolves to the agreement will be signed using the certificate provided in the **Signature Certificate** page and not by the certificate provided as part of the BizTalk Group properties.  
  
  For more information about setting up party properties, see [Configuring AS2 Properties](../core/configuring-as2-properties.md).  
  
## See Also  
 [AS2 Security](../core/as2-security.md)   
 [Configuring Certificates for AS2](../core/configuring-certificates-for-as2.md)   
 [AS2 Messages](../core/as2-messages.md)   
 [AS2 Receive Components](../core/as2-receive-components.md)   
 [AS2 Send Components](../core/as2-send-components.md)   
 [Configuring AS2 Properties](../core/configuring-as2-properties.md)