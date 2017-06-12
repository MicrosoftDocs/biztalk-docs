---
title: "MSBTS_SendHandler2.HostNameToSwitchTo Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4f9a5ad-ab84-4ad7-835c-c58365947473
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendHandler2.HostNameToSwitchTo Property (WMI)
This property contains the name of the BizTalk Host that this transport handler should switch to. To switch this transport handler to a different host, you must update this property with the name of the new host.  
  
## Syntax  
  
```  
  
stringHostNameToSwitchTo;  
```  
  
## Remarks  
 The syntax shown is language neutral.  
  
 This property may be written to switch the transport handler to a different host.  
  
 The maximum length for this property is 80 characters.  
  
 The default value for this property is "".  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.