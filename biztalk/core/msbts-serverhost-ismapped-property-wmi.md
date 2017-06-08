---
title: "MSBTS_ServerHost.IsMapped Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0c967535-3cea-42b2-a852-4a0013557c64
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServerHost.IsMapped Property (WMI)
Indicates whether the specified server works with the specified MessageBox.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
boolean IsMapped;  
```  
  
## Remarks  
 BizTalk Server consumes messages from the MessageBox when **IsMapped** is set to **true**; when set to **false**, BizTalk Server does not consume messages from the MessageBox.  
  
 This property is read-only.  
  
 For samples illustrating the **MSBTS_ServerHost** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.