---
title: "MIME-SMIME Encoder Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components, MIME/SMIME Encoder"
  - "MIME/SMIME Encoder [pipeline component]"
  - "BTS.EncryptionCert property"
ms.assetid: 397505e6-47d0-4b63-9197-814ee4388369
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MIME-SMIME Encoder Pipeline Component
The MIME/SMIME Encoder component can be placed into the Encode stage of a send pipeline. It supports 7bit, 8bit, binary, quoted-printable, base64, and UUencode encoding. Localized data character set changes do not affect the encoding.  
  
 This component can be used to either MIME encode, sign or encrypt an outgoing message with encryption and signing certificates.  
  
 If there is an encoding component in the send pipeline that is configured to sign messages, and the BizTalk group that includes the host running the pipeline is not configured with a signing certificate, the outgoing message will be suspended (with the appropriate error) to the suspended queue of the host that is running the pipeline. If the signing certificate cannot be found in the personal certificate store of the current user under which the service is running, the message will be suspended to the suspended queue of the host that is running the pipeline.  
  
 If there is an encoding component in the outbound pipeline configured to encrypt outbound messages, and the certificate cannot be found in the certificate store, the message will be suspended to the suspended queue of the host that is running the pipeline.  
  
 To perform response encryption on a request-response port that is receiving signed and encrypted messages, a custom pipeline component must be added to the pipeline before the MIME/SMIME Encoder pipeline component. This custom pipeline component must identify the thumbprint corresponding to the encryption certificate and set it to the **BTS.EncryptionCert** property on the message context. For more information about message context properties, see [How to Modify Group Properties](../core/how-to-modify-group-properties.md).  
  
 For information about configuring the MIME/SMIME Encoder pipeline component, see [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md). For more information about BizTalk Server support for encryption, signing, and usage of certificates, see [Security for Sending and Receiving Messages](../core/security-for-sending-and-receiving-messages.md).  
  
## See Also  
 [Pipeline Components](../core/pipeline-components.md)   
 [MIME-SMIME Property Schema and Properties](../core/mime-smime-property-schema-and-properties.md)   
 [MIME (BizTalk Server Sample)](../core/mime-biztalk-server-sample.md)