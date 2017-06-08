---
title: "MSBTS_ReceiveLocation.SrvWinStartDT Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3057540b-8c4f-4daa-802b-9357e56bbdda
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ReceiveLocation.SrvWinStartDT Property (WMI)
Contains the start time of a service window when the receive location should activate.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
datetime SrvWinStartDT;  
```  
  
## Remarks  
 Date part of the property is not used.  
  
 This property is read-write.  
  
 For more information about the format of the datetime value, see the Platform SDK: Windows Management Instrumentation documentation at [http://go.microsoft.com/fwlink/?LinkID=24855](http://go.microsoft.com/fwlink/?LinkID=24855).  
  
## Requirements  
 **Header:** Declared in BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.