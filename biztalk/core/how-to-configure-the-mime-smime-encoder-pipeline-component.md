---
title: "How to Configure the MIME-SMIME Encoder Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, encrypting digital signatures"
  - "pipeline components, MIME/SMIME Encoder"
  - "Partner Management, security"
  - "MIME/SMIME Encoder [pipeline component], configuring"
  - "messages, encoding"
  - "messages, multi-parts"
ms.assetid: dcbb08e8-d300-4e7f-9c1c-907fb602e721
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the MIME-SMIME Encoder Pipeline Component
Use the MIME/SMIME Encoder pipeline component to encode and encrypt outgoing messages and to sign outgoing messages. This component is useful when you require secured document interchange between BizTalk Server and external partners. You can also use this component to send BizTalk Server multi-part messages.  

> [!NOTE]
>  In BizTalk 2006, the MIME/SMIME encoder pipeline component will not have native 64-bit support.  This means that this component must be run in a 32-bit emulation mode process (WOW64).  This implies that the host instance in which this encoder component (or the send pipeline of which it is a part) runs must be running in 32-bit emulation mode.  Be aware of the performance (and other) implications of this restriction for other elements of BizTalk running in this same host instance.  

### To configure the properties for the MIME/SMIME Encoder pipeline component  

1. Drag the MIME/SMIME Encoder pipeline component into the Encode stage of a send pipeline.  

2. In the Properties window, in the **Pipeline Component Properties** section, do the following.  


   |             Use this             |                                                                                                                                                                                                                                                                                                                              To do this                                                                                                                                                                                                                                                                                                                               |
   |----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Add Signing Cert To Message**  |                                                                                                                                                                                                                    If the **Signature Type** property is not **NoSign**, you can select whether to add the signing certificate to the signed message by setting the **Add Signing Cert to Message** property.<br /><br /> Default value: **True**                                                                                                                                                                                                                     |
   |    **Check revocation list**     |                                                                                                                                                                                                                                                                   Specifies whether to check the certificate revocation list while processing a SMIME message.<br /><br /> Default value: **True**                                                                                                                                                                                                                                                                    |
   |  **Content transfer encoding**   |                                                                                                                                                                                                                                                     Indicates the encoding format.<br /><br /> Options: Base64, QuotedPrintable, SevenBit, EightBit, Binary, and UUEncode.<br /><br /> Default value: **Base64**                                                                                                                                                                                                                                                      |
   |      **Enable encryption**       |                                                                                                                                     Set to **True** if you want to encrypt the outgoing message. If this option is enabled, the user can select the encryption algorithm to use by setting the **Encryption algorithm** property. For message encryption, the MIME/SMIME Encoder pipeline component uses the public key certificate that is associated with a send port in BizTalk Explorer.<br /><br /> Default value: **False**                                                                                                                                     |
   |     **Encryption algorithm**     |                                                                            Define the encryption algorithm.<br /><br /> This property can only be set if **Enable encryption** is set to **True**.<br /><br />**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] and newer versions**, AES encryption is automatically included. Options include: DES3, DES, RC2, AES128 (default), AES192, and AES256.<br /><br />For previous [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] versions, options include: DES3 (default), DES, RC2.                                                                             |
   | **Send body part as attachment** |                                                                                                                                        Set to **True** if you want to send the body party of a BizTalk message as a MIME attachment.<br /><br /> Default value: **False** **Important:**  You should not set this property to **True** when sending messages between BizTalk Servers. Otherwise, the message decoding will require custom coding because the message is interpreted on the receive side as a two-part message.                                                                                                                                        |
   |        **Signature Type**        | If you want to sign the outgoing message, select a signing format with this property. This property has three values:<br /><br /> -   **NoSign**. The message will not be signed.<br />-   **ClearSign**. The signature will be appended to the message. **ClearSign** cannot be used if **Enable Encryption** is set to **True**.<br />-   **BlobSign**. The signature will be appended to the message and the message will be encoded.<br /><br /> For message signing, the MIME/SMIME Encoder component uses the private key client certificate that is associated with BizTalk Group in the BizTalk Administration console.<br /><br /> Default value: **NoSign** |

   To set the file name for MIME attachments, use the **FileName** property in the **System** namespace for the message part.  

## See Also  
 [MIME-SMIME Encoder Pipeline Component](../core/mime-smime-encoder-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [MIME-SMIME Property Schema and Properties](../core/mime-smime-property-schema-and-properties.md)   
 [MIME (BizTalk Server Sample)](../core/mime-biztalk-server-sample.md)