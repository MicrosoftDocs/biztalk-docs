---
title: "How to Configure the MIME-SMIME Decoder Pipeline Component | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, attachments"
  - "pipeline components, MIME/SMIME Decoder"
  - "MIME/SMIME Decoder [pipeline component], configuring"
  - "messages, verifying"
  - "messages, decoding"
  - "messages, digital signatures"
  - "messages, security"
ms.assetid: bfd44893-f1c3-4524-abc6-f820b8c0ef07
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the MIME-SMIME Decoder Pipeline Component
The MIME/SMIME Decoder pipeline component is used for decoding and decrypting MIME/SMIME encoded messages and for verifying digital signatures of signed messages. This component is useful when secured document interchange is needed between external partners and BizTalk Server. This component can also be used for receiving messages with attachments.  
  
> [!NOTE]
>  In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the MIME/SMIME decoder pipeline component does not have native 64-bit support.  This means that this component must be run in a 32-bit emulation mode process (WOW64).  This implies that the host instance in which this decoder component (or the receive pipeline of which it is a part) runs must be running in 32-bit emulation mode.  Be aware of the performance (and other) implications of this restriction for other elements of BizTalk running in this same host instance.  
> 
> [!NOTE]
>  The MIME/SMIME decoder component is also used within the POP3 adapter.  As a result, the same native 64-bit support restriction exists for the host instance in which the POP3 adapter runs.  See related information about the POP3 adapter in [POP3 Adapter](../core/pop3-adapter.md).  
  
### To configure the properties for the MIME/SMIME Decoder pipeline component  
  
1.  Drag the MIME/SMIME Decoder pipeline component into the Decode stage of a receive pipeline.  
  
2.  In the Properties window, in the **Pipeline Component Properties** section, do the following.  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |**Allow Non MIME Message**|Set this property to **True** if you expect that the receive pipeline may get messages that are not MIME encoded. This option is useful when the MIME/SMIME Decoder pipeline component is used in a pipeline that receives messages in different forms, for example, MIME encoded or plain XML. By default, this property is set to **False**, meaning that the component generates an error if it receives a non-MIME encoded message on input. **Note:**  The MIME decoder scans the first 1024 bytes of the incoming message to search for the "MIME-Version" header. If this header is not found, the message is treated as a non-MIME message. <br /><br /> Default value: **False**|  
    |**Body part content type**|Indicates the content type of the MIME part. The MIME part with this content type will become the body part of the BizTalk message.<br /><br /> Default value: None|  
    |**Body part index**|Indicates the 1-based index into the MIME part list. The MIME part at this index in the list will become the body part of the BizTalk message. To disable the selection of body part by index, use a value of **0**.<br /><br /> Default value: **0**|  
    |**Check Revocation List**|Set this property to **True** if you want to check the certificate revocation list for the certificates that senders use for signing messages that are being sent to BizTalk Server. Disabling this option increases the performance of the component.<br /><br /> The certificate revocation list associated with a certificate is downloaded from a remote Web site (for example, Verisign.com). If the BizTalk Server cannot connect to the remote Web site, the message fails in the pipeline.<br /><br /> Default value: **True**|  
  
## See Also  
 [MIME-SMIME Decoder Pipeline Component](../core/mime-smime-decoder-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [MIME-SMIME Property Schema and Properties](../core/mime-smime-property-schema-and-properties.md)   
 [MIME (BizTalk Server Sample)](../core/mime-biztalk-server-sample.md)