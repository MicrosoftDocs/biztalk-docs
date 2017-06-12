---
title: "MSBTS_ReceiveLocation.SrvWinStopDT Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3961c0d9-7e16-4495-809a-49f37db649f8
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocation.SrvWinStopDT Property (WMI)
Contains the end time of a service window when the receive location should deactivate.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
datetime SrvWinStopDT;  
```  
  
## Remarks  
 Date part of the property is not used.  
  
 This property is read-write.  
  
 For more information about the format of the datetime value, see the Platform SDK: Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=24855](http://go.microsoft.com/fwlink/?LinkID=24855).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.