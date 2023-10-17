---
description: "Learn more about: MIME-SMIME Decoder Pipeline Component"
title: "MIME-SMIME Decoder Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components, MIME/SMIME Decoder"
  - "MIME/SMIME Decoder [pipeline component]"
ms.assetid: ff6c963c-1b5c-4be4-9eef-3ec9a018e7fd
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MIME-SMIME Decoder Pipeline Component
The MIME/SMIME Decoder component provides MIME decoding functionality for messages. This pipeline component can be placed into the Decode stage of a receive pipeline, and it supports 7bit, 8bit, binary, quoted-printable, UUEncode, and base64 decoding. Localized data character set changes will not affect the decoding.  
  
 The MIME/SMIME Decoder component can decrypt and sign-validate an incoming message. Decryption certificates are used from the personal certificate store of the current user under which the service is running. Sign-validation certificates are used from the Address Book store of the local computer or from the message itself.  
  
 On successful decryption of a message, the MIME/SMIME Decoder pipeline component associates the thumbprint of the decryption certificate used to decrypt the message as a predicate of the message. This means that any service (orchestration or send port) that is subscribing to that message must be associated with a host that owns that key. Associations between hosts and keys can be completed in the BizTalk Administration console as a property of the host. For more information about configuring the host in the BizTalk Administration console, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).  
  
 The MIME/SMIME Decoder pipeline component is the only out-of-the-box receive pipeline component that handles multi-part messages, including multi-part MIME/SMIME messages. The pipeline component parses the message and creates an equivalent multi-part BizTalk message. A multi-part BizTalk message has one unique part named the body part. All other pipeline components, such as the XML Disassembler pipeline component, only process the body part of the BizTalk Message. Also the MessageType corresponding to the BizTalk body part is used for routing the message to subscribers.  
  
 The following conditions are evaluated by the MIME/SMIME Decoder pipeline component to identify the BizTalk BodyPart corresponding to a multi-part MIME message. The order of the condition evaluation is as follows:  
  
1.  The first MIME/SMIME part that has the Content-Description header set to "body" (case-insensitive).  
  
2.  The first MIME/SMIME part that has the Content-Type header set to "text/xml"(case-insensitive).  
  
3.  The first MIME/SMIME part that has the Content-Type header set to "text/" (case-insensitive).  
  
4.  The first MIME/SMIME part.  
  
> [!NOTE]
>  The order of the parts in the output BizTalk message is same as the order of MIME/SMIME parts in the MIME/SMIME message.  
  
> [!NOTE]
>  If the multi-part BizTalk message is being subscribed or consumed by an orchestration, the number of parts in the message has to match the number of parts in the message that activates the orchestration.  
  
 For information about configuring the MIME/SMIME Decoder pipeline component, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md). For more information about BizTalk Server support for decryption, sign-validation, and usage of certificates, see [Security for Sending and Receiving Messages](../core/security-for-sending-and-receiving-messages.md).  
  
## See Also  
 [Pipeline Components](../core/pipeline-components.md)   
 [MIME-SMIME Property Schema and Properties](../core/mime-smime-property-schema-and-properties.md)   
 [MIME (BizTalk Server Sample)](../core/mime-biztalk-server-sample.md)
