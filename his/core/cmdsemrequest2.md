---
title: "CMDSemRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62a6c529-df9c-429c-a5dc-2ff8a1aa89e2
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
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