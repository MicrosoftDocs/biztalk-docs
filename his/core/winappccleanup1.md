---
description: "Learn more about: WinAPPCCleanup"
title: "WinAPPCCleanup1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1e34065-9a97-45ca-b288-d9cd246ca3af
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# WinAPPCCleanup
The **WinAPPCCleanup** function terminates and deregisters an application from a Windows APPC implementation.  
  
## Syntax  
  
```  
  
BOOL WINAPI WinAPPCCleanup(  
void  
);  
  
```  
  
## Return Value  
 The return value specifies whether the deregistration was successful. If the value is nonzero, the application was successfully deregistered. The application was not deregistered if a value of zero is returned.  
  
## Remarks  
 Use **WinAPPCCleanup** to indicate deregistration of a Windows APPC application from a Windows APPC implementation.  
  
 Conversations that are still active will be terminated and TPs ended. This function is equivalent to issuing [TP_ENDED](../core/tp-ended1.md) (HARD) on all TPs owned by the application.  
  
## See Also  
 [WinAPPCStartup](../core/winappcstartup1.md)
