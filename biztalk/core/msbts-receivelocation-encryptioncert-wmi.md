---
title: "MSBTS_ReceiveLocation.EncryptionCert (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6484cfd0-20c5-4650-bb42-61f4c797bafc
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocation.EncryptionCert (WMI)
This property contains the Name of the certificate used for outbound encryption.  
  
## Syntax  
  
```  
  
String EncryptionCert;  
```  
  
## Remarks  
 This property is read/write.  
  
 The default value for this parameter is "".  
  
 The syntax shown is language neutral.  
  
 The maximum length for this property is 256 characters.  
  
 The string must be constructed as shown below with appropriate values filled in and no extra spaces:  
  
```  
"E=, C=, S=, L=, O=, OU=, CN="  
```  
  
 For example, the following string specifies a certificate for a fictitious sample:  
  
```  
"E=lab, C=US, S=Wa, L=Redmond, O=Microsoft, OU=BizTalk, CN=EncryptSample"  
```  
  
> [!NOTE]
>  The certificate must be specified in this order and without extra spaces and must not be longer than 256 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.