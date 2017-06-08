---
title: "MSBTS_Host.AuthTrusted Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5cdb4fc-aa4d-4b27-845d-d93b4dc590c6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_Host.AuthTrusted Property (WMI)
Indicates whether a tracking service can be trusted to collect authentication information. The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
boolean AuthTrusted;  
```  
  
## Remarks  
 This property is read-write.  
  
 Each host can be marked as authentication trusted. These hosts are permitted to indicate that a sender of a message, which the trusted host is queuing, is an entity other than the host itself. In other words, the service accounts of an authentication trusted host are trusted to place a sender's security ID (SSID) on a message that maps to a user other than to the host specifically. For more information, see [Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md).  
  
> [!NOTE]
>  You can mark any host instance as authentication trusted. However, authentication trusted host instances cannot use the same service account(s) as non-authentication trusted host instances.  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.