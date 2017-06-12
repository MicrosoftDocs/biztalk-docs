---
title: "MSBTS_ServiceInstanceSuspendedEvent.HostName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b1ba4f8-408d-4170-a328-2a2e37ccc135
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_ServiceInstanceSuspendedEvent.HostName Property (WMI)
Contains the name of the BizTalk Host that corresponds to this queue. The syntax shown is language neutral.  
  
## Syntax  
  
```  
  
string HostName;  
```  
  
## Remarks  
 This property is read-only.  
  
 The maximum length for this property is 80 characters.  
  
 For sample code illustrating the **MSBTS_ServiceInstanceSuspendedEvent** class, see [Listening for a Suspended Event Using WMI](../core/listening-for-a-suspended-event-using-wmi.md).  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.