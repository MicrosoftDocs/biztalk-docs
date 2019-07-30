---
title: "WinAPPCIsBlocking1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c3bf50d-d99e-4d46-aeb0-8e2d4831bf95
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# WinAPPCIsBlocking
The **WinAPPCIsBlocking** function determines if a thread is executing while waiting for a previous blocking call to finish.  
  
## Syntax  
  
```  
  
BOOL WINAPI WinAPPCIsBlocking(  
void  
);  
  
```  
  
## Return Value  
 The return value specifies the outcome of the function. If the value is nonzero, there is an outstanding blocking call awaiting completion. A zero indicates the absence of an outstanding blocking call.  
  
## Remarks  
 Although a call issued on a blocking function appears to an application as though it blocks, the Windows APPC DLL has to relinquish the processor to allow other applications to run. This means that it is possible for the application that issued the blocking call to be re-entered, depending on the message(s) it receives. In this instance, the **WinAPPCIsBlocking** call can be used to determine whether the application task currently has been re-entered while waiting for an outstanding blocking call to finish. Note that Windows APPC prohibits more than one outstanding blocking call per thread.  
  
 The Windows APPC DLL prohibits more than one blocking call per thread and returns AP_THREAD_BLOCKING if this occurs.  
  
## See Also  
 [WinAPPCSetBlockingHook](../core/winappcsetblockinghook1.md)   
 [WinAPPCUnhookBlockingHook](../core/winappcunhookblockinghook2.md)   
 [WinAPPCCancelBlockingCall](../core/winappccancelblockingcall1.md)