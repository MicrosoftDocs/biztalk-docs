---
title: "MSBTS_HostInstance.HostName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95fb1572-7ff1-4568-87ca-f368fdc6dad1
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.HostName Property (WMI)
Contains the name of the BizTalk host to which this BizTalk host instance belongs.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string HostName;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 The maximum length for this property is 80 characters.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.