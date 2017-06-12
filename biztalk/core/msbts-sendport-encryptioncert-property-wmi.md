---
title: "MSBTS_SendPort.EncryptionCert Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5917c349-4c6a-43c2-9e6e-9d206bdbc17b
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendPort.EncryptionCert Property (WMI)
This property contains the Name of the certificate used for outbound encryption.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```
string EncryptionCert;  
```  
  
## Remarks  
 This property is read-write.  
  
 The default value for this parameter is "".  
  
 The syntax shown is language neutral.The maximum length for this property is 256 characters.  
  
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
  
 This property wraps the managed **Microsoft.BizTalk.ExplorerOM.SendPort.EncryptionCert** property.
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.