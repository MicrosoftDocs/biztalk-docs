---
title: "CMDSemWait1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a89986ef-b59c-4a2b-b8d7-94db83031790
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
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