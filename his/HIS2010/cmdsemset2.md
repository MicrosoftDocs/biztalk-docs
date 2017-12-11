---
title: "CMDSemSet2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d98ebd7-ff10-43b4-b8f8-1c3c0c5c4a87
caps.latest.revision: 3
---
# CMDSemSet
The **CMDSemSet** function sets a RAM semaphore.  
  
## Syntax  
  
```  
  
USHORT FAR CMDSemSet(   
ULONG FAR *ramSem   
);  
```  
  
#### Parameters  
 *ramSem*  
 Address of the semaphore.