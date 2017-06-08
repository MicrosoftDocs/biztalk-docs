---
title: "MIME-SMIME Decoder Pipeline Component Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.BizTalk.Component.MIME_SMIME_Decoder"
ms.assetid: b272610f-f6ad-4466-9931-b96595ed4cc1
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MIME-SMIME Decoder Pipeline Component Properties
Use the MIME/SMIME decoder pipeline component to provide MIME decoding functionality to messages.  
  
 The MIME/SMIME decoder pipeline component is intended for use in the Decode stage of a Receive pipeline.  
  
 The properties of the MIME/SMIME decoder pipeline component can be set in the Properties window of Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable MIME/SMIME decoder pipeline component properties.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Allow non MIME message**|Set this property to True if you expect that the Receive pipeline may get messages that are not MIME encoded. This option is useful when the MIME/SMIME decoder component is used in a pipeline that receives messages in different forms, for example MIME encoded or standard XML. By default this property is set to False, meaning that component will generate an error if it receives a non-MIME encoded message on input.<br /><br /> Default Value: False|  
|**Body part content type**|Indicates the content type of the MIME part. The MIME part with this content type will become the body part of the BizTalk message.<br /><br /> Default value: None|  
|**Body part index**|Indicates the 1-based index into the MIME part list. The MIME part at this index in the list will become the body part of the BizTalk message. To disable the selection of body part by index, use a value of 0.<br /><br /> Default value: 0|  
|**Check revocation list**|Set this property to True if you want to check the revocation list for the certificates that senders use for signing messages that are being sent to BizTalk Server. Enabling this option decreases the performance of the component.<br /><br /> Default Value: True|  
  
## See Also  
 [Using Pipeline Designer](../core/using-pipeline-designer.md)   
 [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)   
 [MIME-SMIME Decoder Pipeline Component](../core/mime-smime-decoder-pipeline-component.md)