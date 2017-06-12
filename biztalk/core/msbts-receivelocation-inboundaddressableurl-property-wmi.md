---
title: "MSBTS_ReceiveLocation.InboundAddressableURL Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 396a28bc-5f53-4e24-be7f-7dc12d77140f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocation.InboundAddressableURL Property (WMI)
Contains a URL that can be used by external parties to send documents to the receive location.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string InboudAddressableURL;  
```  
  
## Remarks  
 This property is read-write.  
  
 Value of this property is usually provided by the transport component, based on the adapter-specific configuration.  
  
 The maximum length for this property is 256 characters.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.