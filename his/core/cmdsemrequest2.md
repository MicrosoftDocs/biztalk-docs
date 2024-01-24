---
description: "Learn more about: CMDSemRequest"
title: "CMDSemRequest2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
