---
title: "MSBTS_ReceiveHandler.HostNameToSwitchTo Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b274a30-bfbe-4d6b-a7db-0c7567db70d6
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveHandler.HostNameToSwitchTo Property (WMI)
Contains the name of the BizTalk Host that this adapter handler should switch to.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string HostNameToSwitchTo = "";  
```  
  
## Remarks  
 This property is optional.  
  
 To switch this adapter to a different host, you must update this property with the name of the new host. This property is writeable during an update.  
  
 The maximum length for this property is 80 characters.  
  
 For samples illustrating the **MSBTS_ReceiveHandler** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.