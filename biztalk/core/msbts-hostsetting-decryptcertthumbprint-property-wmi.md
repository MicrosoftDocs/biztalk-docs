---
title: "MSBTS_HostSetting.DecryptCertThumbprint Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9f22e37-8d2b-4182-9e56-2017baf3e75f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostSetting.DecryptCertThumbprint Property (WMI)
Contains the thumbprint of the decryption certificate.  
  
> [!NOTE]
>  The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
string DecryptCertThumbprint;  
```  
  
## Remarks  
 This property is read-write.  
  
 The certificate thumbprint is a digest of the certificate data and is found in the certificate details expressed as a hexadecimal value. For example: 'FD36 90F0 EB49 F7B8 D3AB 1C69 8E02 ED84 5738 7868'.  
  
 The maximum length for this property is 80 characters.  
  
 For sample code using the **MSBTS_HostSetting** class, see [Creating, Updating, and Deleting a Host Instance Using WMI](../core/creating-updating-and-deleting-a-host-instance-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.