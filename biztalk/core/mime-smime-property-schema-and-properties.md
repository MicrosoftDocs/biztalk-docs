---
title: "MIME-SMIME Property Schema and Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26dd25b9-7eb8-4354-9929-dc1985dd1d77
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MIME-SMIME Property Schema and Properties

## Namespace properties
The **http://schemas.microsoft.com/BizTalk/2003/mime-properties** namespace contains properties you can use to set message and part context properties for the MIME/SMIME Encoder pipeline component. The MIME/SMIME Encoder uses these properties to generate the appropriate MIME/SMIME headers in the message that is created. The following table describes the MIME/SMIME properties.  
  
|Property|Scope|Type|Description|  
|--------------|-----------|----------|-----------------|  
|**FileName**|Per message part|xs:string|Sets the file name header of the MIME/SMIME part.|  
|**ContentID**|Per message part|xs:string|Sets the Content-ID header of the MIME/SMIME part.|  
|**ContentDescription**|Per message part|xs:string|Sets the Content-Description header of the MIME/SMIME part.|  
|**ContentTransferEncoding**|Per message part|xs:string|Sets the Content-Transfer-Encoding header of the generated MIME/SMIME part.<br /><br /> This value overrides the **Content transfer encoding** value configured in Pipeline Designer. For a multi-part message, you can use different encodings for different MIME/SMIME parts.|  
|**ContentLocation**|Per message part|xs:string|Sets the Content-Location header of the generated MIME/SMIME part.|  
|**IsMIMEEncoded**|Per message part|xs:boolean|Specifies whether the message has a MIME/SMIME payload. The MIME component writes to this value, so you do not have to set it.|  
  
 The MIME/SMIME Encoder also uses the following part properties from the **System** namespace.  
  
|Property|Type|Description|  
|--------------|----------|-----------------|  
|ContentType|xs:string|Corresponds to the Content-Type header of the generated MIME/SMIME part.|  
|FileName|xs:string|Corresponds to the file name.|  
  
## See Also  
 [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)   
 [How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)   
 [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)   
 [MIME (BizTalk Server Sample)](../core/mime-biztalk-server-sample.md)   
 **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]