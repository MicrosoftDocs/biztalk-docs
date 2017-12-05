---
title: "CMDSemRequest1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b356da1b-2209-4169-9cbd-d2f25427a06b
caps.latest.revision: 3
---
# CMDSemRequest
The **CMDSemRequest** function requests a RAM semaphore.  
  
## Syntax  
  
```  
  
USHORT FAR CMDSemRequest(  
ULONG FAR   
*ramSem,   
ULONG timeOut   
);  
```  
  
#### Parameters  
 *ramSem*  
 Address of the semaphore.  
  
 *timeOut*  
 Length of time in milliseconds to wait before returning.  
  
## Return Value  
 0  
 OK.  
  
 ERROR_SEM_TIMEOUT  
 Time-out expired before semaphore operation completed.  
  
 ERROR_SEM_OWNED  
 This thread or another thread owns the semaphore, and the calling thread specified zero time-out.