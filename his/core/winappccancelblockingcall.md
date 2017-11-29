---
title: "WinAPPCCancelBlockingCall1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2c60152-c42f-458e-a70a-a726e6bc72ce
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# WinAPPCCancelBlockingCall
The **WinAPPCCancelBlockingCall** function cancels any outstanding blocking operation for its thread. Any outstanding blocked call canceled will cause an error code of WAPPCCANCEL to be generated.  
  
## Syntax  
  
```  
  
BOOL WINAPI WinAPPCCancelBlockingCall(  
void  
);  
  
```  
  
## Return Value  
 The return value specifies whether the cancellation request was successful. If the value is zero, the request was canceled. Otherwise, the value is the following:  
  
 WAPPCINVALID  
 An error code indicating that there is no outstanding blocking call.  
  
## Remarks  
 If the outstanding verb relates to a conversation (for example, [SEND_DATA](../core/send-data.md) or [RECEIVE_AND_WAIT](../core/receive-and-wait.md)), the verb is purged and the session is closed. If the verb relates to a TP (for example, [RECEIVE_ALLOCATE](../core/receive-allocate.md) or [TP_STARTED](../core/tp-started.md)), the TP is ended. In both cases, while the implementation brings down conversations and sessions as cleanly as possible, it does not flush send buffers, wait for confirmations, and so on. This call is synchronous and after the processing described above is complete, the function is finished.  
  
 In Microsoft Windows, a multithreaded application can have multiple blocking operations outstanding, but only one per thread. To distinguish between multiple outstanding calls, **WinAPPCCancelBlockingCall** cancels the outstanding operation on the current, or calling, application thread if one exists; otherwise, it fails. By default in Windows, Windows APPC suspends the calling application thread while an operation is outstanding. As a result, the thread on which the blocking operation was initiated will not regain control (and therefore, will not be able to issue a call to **WinAPPCCancelBlockingCall**) unless a blocking hook is registered for the thread using [WinAPPCSetBlockingHook](../core/winappcsetblockinghook.md).