---
title: "MIME-SMIME Encoder Pipeline Component Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.BizTalk.Component.MIME_SMIME_Encoder"
ms.assetid: b5efd9df-c30c-46db-ab59-2dd1e9fe5224
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MIME-SMIME Encoder Pipeline Component Properties
Use the MIME/SMIME encoder pipeline component to provide MIME encoding functionality to messages.  
  
 The MIME/SMIME encoder pipeline component is intended for use in the Encode stage of a Send pipeline.  
  
 The properties of the MIME/SMIME encoder pipeline component can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable MIME/SMIME encoder pipeline component properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Add signing certification to message**|Select whether to add the signing certificate to the signed message, if the **Signature Type** property is not NoSign, by setting the **Add signing cert to the message** property.<br /><br /> Default Value: True|  
|**Check Revocation list**|Indicate whether to check the Certificate Revocation List while processing an SMIME message.<br /><br /> Default Value: True|  
|**Content transfer encoding**|Indicate the encoding format.<br /><br /> Options: Base64, QuotedPrintable, SevenBit, EightBit, Binary, and UUEncode.<br /><br /> Default Value: Base64|  
|**Enable encryption**|Set this property to True if you need to encrypt the outgoing message. If this option is enabled, then the user can select the encryption algorithm to use by setting the **Encryption algorithm** property. For message encryption, the MIME/SMIME pipeline component uses the public key certificate that is associated with a send port in BizTalk Explorer.<br /><br /> Default Value: False|  
|**Encryption algorithm**|Define the encryption algorithm.<br /><br /> This property can only be set if Enable Encryption is set to True.<br /><br /> Options: DES3, DES, RC2.<br /><br /> Default Value: DES3|  
|**Send body part as attachment**|Set this property to True if you want to send the body party of BizTalk message as a MIME attachment.<br /><br /> Default Value: False|  
|**Signature type**|Select a signing format by setting this property, if you need to sign the outgoing message. This property has three values:<br /><br /> -   NoSign. The message will not be signed.<br />-   ClearSign. The signature will be appended to the messages.<br />-   BlobSign. The signature will be appended to the message and the message will be encoded. For message signing, the MIME/SMIME component uses the private key client certificate that is associated with the BizTalk group in the BizTalk Server Administration Console.<br /><br /> Default Value: NoSign|  
  
## See Also  
 [Using Pipeline Designer](../core/using-pipeline-designer.md)   
 [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)   
 [MIME-SMIME Encoder Pipeline Component](../core/mime-smime-encoder-pipeline-component.md)