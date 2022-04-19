---
description: "Learn more about: WinAPPCCancelAsyncRequest"
title: "WinAPPCCancelAsyncRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c82d700-a02e-451c-8a47-1e18d12b7dda
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# WinAPPCCancelAsyncRequest
The **WinAPPCCancelAsyncRequest** function cancels an outstanding [WinAsyncAPPC](../core/winasyncappc1.md)-based request.  
  
## Syntax  
  
```  
  
    int WINAPI WinAPPCCancelAsyncRequest(   
HANDLE hAsyncTaskID);  
```  
  
#### Parameters  
 *hAsyncTaskID*  
 Supplied parameter. Specifies the asynchronous task to be canceled.  
  
## Return Value  
 The return value specifies whether the asynchronous request was canceled. If the value is zero, the request was canceled. Otherwise, the value is one of the following:  
  
 WAPPCINVALID  
 An error code indicating that the specified asynchronous task identifier was invalid.  
  
 WAPPCALREADY  
 An error code indicating that the asynchronous routine being canceled has already completed.  
  
## Remarks  
 An asynchronous task previously initiated by issuing one of the **WinAsyncAPPC**, **WinAsyncAPPCEx**, or **WinAsyncAPPCIOCP** functions can be canceled prior to completion by issuing the **WinAPPCCancelAsyncRequest** function, specifying the asynchronous task identifier as returned by the initial function in *hAsyncTaskID*.  
  
 If the outstanding verb relates to a conversation (for example, [SEND_DATA](../core/send-data1.md) or [RECEIVE_AND_WAIT](../core/receive-and-wait2.md)), the verb is purged and the session is closed. If the verb relates to a TP (for example, [RECEIVE_ALLOCATE](../core/receive-allocate1.md) or [TP_STARTED](../core/tp-started2.md)), the TP is ended. In both cases, while the implementation closes conversations and sessions as cleanly as possible, it does not flush send buffers, wait for confirmations, and so on. This call is synchronous, and after the processing described above is complete, a completion message is posted for the canceled verb.  
  
 If an attempt to cancel an existing asynchronous **WinAsyncAPPC** routine fails with an error code of WAPPCALREADY, one of two things has occurred. Either the original routine has already completed and the application has dealt with the resulting message, or the original routine has already completed and the resulting message is still waiting in the application window queue.
