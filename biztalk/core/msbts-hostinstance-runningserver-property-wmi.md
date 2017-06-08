---
title: "MSBTS_HostInstance.RunningServer Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00b939e8-0800-4d8a-b09b-ddf399c19190
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_HostInstance.RunningServer Property (WMI)
Contains the name of the server on which the host instance runs.  
  
## Property Declaration  
 *The syntax shown is language neutral.*  
  
```  
string RunningServer;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 The maximum length for this property is 63 characters.  
  
 For samples illustrating the **MSBTS_HostInstance** class, see [WMI Script Samples](../core/wmi-script-samples.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.