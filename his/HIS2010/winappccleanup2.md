---
title: "WinAPPCCleanup2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1498250b-2ce7-49a6-85af-e3d0d5d19547
caps.latest.revision: 3
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
  
 Conversations that are still active will be terminated and TPs ended. This function is equivalent to issuing [TP_ENDED](../HIS2010/tp-ended2.md) (HARD) on all TPs owned by the application.  
  
## See Also  
 [WinAPPCStartup](../HIS2010/winappcstartup2.md)