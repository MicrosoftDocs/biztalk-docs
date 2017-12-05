---
title: "CMDSemWait2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 992f1ec9-e43d-4a8d-bc45-3572bb0b74a8
caps.latest.revision: 3
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