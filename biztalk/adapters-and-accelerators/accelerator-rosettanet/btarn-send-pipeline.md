---
title: "BTARN Send Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML Assembler"
  - "send pipelines, message flow"
  - "DOCTYPE headers"
  - "MIME/SMIME Encoder"
  - "send pipelines, BTARN"
  - "BTARN, send pipelines"
  - "XML Preprocessor"
  - "messages, message flow"
ms.assetid: 88562132-0ea4-4b5a-9445-b69f6c84e5ea
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BTARN Send Pipeline
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] prepares a RosettaNet Implementation Framework (RNIF) message for transmission in the RNIFSend pipeline (RNIFSend.btp). The send pipeline includes the following:  
  
-   XML preprocessor  
  
-   XML assembler  
  
-   Multipurpose Internet Mail Extensions/Secure Multipurpose Internet Mail Extensions (MIME/SMIME) encoder  
  
## XML Preprocessor  
 The XML preprocessor adds a DOCTYPE header to the message. The header identifies the document type definition (DTD) schema associated with the message. The RNIF specification requires the presence of a DOCTYPE header for RNIF transmission.  
  
## XML Assembler  
 The XML assembler is based on the BizTalk Server XML assembler. It transfers properties from the message context back into envelopes and documents. It assembles the message from its XML parts and attachments. It does not perform message validation.  
  
 For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] XML assembler, see "XML Assembler Pipeline Component" in BizTalk Server Help.  
  
## MIME/SMIME Encoder  
 The MIME/SMIME encoder is based on the BizTalk Server MIME/SMIME Encoder. Depending on the protocol settings in the trading partner agreement, and the settings of the BizTalk Server MIME/SMIME Encoder, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] encoder performs the following:  
  
- Adds an 8-byte binary header to the message, as required for RNIF 1.1 messages.  
  
- Encodes the message parts, and calculates the digest.  
  
- Encrypts the payload (service content plus attachments), or the payload container (service content plus service header plus attachments). If you have set the **Encode all ports** setting on the **Protocol** tab of the trading partner agreement to `False`, the encoder will encrypt only the payload. If you have set the **Encode all ports** setting to `True`, the encoder will encrypt the payload container.  
  
  For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] MIME/SMIME Encoder, see "MIME/SMIME Encoder Pipeline Component" in BizTalk Server Help.  
  
## Message Flow  
 The message flow through the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send pipeline is as follows:  
  
1.  If you have set the **Encode all parts** setting of the trading partner agreement to `True`, the MIME/SMIME encoder will encode all message parts. It will use the encoding method set in the `Encoding` property of the agreement.  
  
2.  For RNIF 2.01, if the message is an action message and there is an attachment, the encoder will do the following for each attachment:  
  
    1.  If the attachment is binary, the encoder will encode it.  
  
    2.  The encoder will generate a content ID for the attachment.  
  
    3.  The encoder will create a MIME part for the attachment.  
  
3.  For RNIF 2.01, the pipeline will encrypt message parts and build the RNIF message depending on the setting of **Is Persistent Confidentiality Required** (as set in the process configuration settings):  
  
    1.  If you have set **Is Persistent Confidentiality Required** to **Payload**, the encoder will encrypt the service content and the attachments. The assembler will then add the service header, delivery header, and preamble to construct the final RNIF message.  
  
    2.  If you have set **Is Persistent Confidentiality Required** to **Payload Container**, the encoder will encrypt the service header, service content, and the attachments. The assembler will then add the delivery header and preamble to construct the final RNIF message.  
  
    3.  If you have set **Is Persistent Confidentiality Required** to **None**, the assembler will add the service header, delivery header, and preamble to the service content and the attachments (without encryption) to construct the final RNIF message.  
  
4.  For RNIF 1.1, the assembler will construct the final RNIF message without encryption.  
  
5.  The encoder will sign the message in the following case:  
  
    1.  The message is a signal message, and the **Non-Repudiation Required** property (in the process configuration settings) is `True`.  
  
    2.  The message is an action message, and the **Non-Repudiation of Origin and Content** property (in the process configuration settings) is `True`.  
  
6.  For RNIF 2.01, the encoder will calculate the digest on the first body part of the MIME message, and persist the digest. It will calculate the digest using the method set in the `Digest` method property in the trading partner agreement (SHA-1 or MD5).  
  
## See Also  
 [Message Processing in BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)