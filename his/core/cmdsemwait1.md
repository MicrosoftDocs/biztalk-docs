---
description: "Learn more about: CMDSemWait"
title: "CMDSemWait1"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# CMDSemWait
The **CMDSemWait** function waits until a RAM semaphore is cleared.  
  
## Syntax  
  
```  
  
USHORT FAR CMDSemWait(   
ULONG FAR *ramSem,   
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
