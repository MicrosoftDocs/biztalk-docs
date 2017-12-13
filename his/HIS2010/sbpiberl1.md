---
title: "sbpiberl1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67f3441c-1752-4f49-a32a-203f21d9cb79
caps.latest.revision: 3
---
# sbpiberl
The application calls the **sbpiberl** function to release a buffer element from an existing buffer.  
  
## Syntax  
  
```  
  
VOID sbpiberl(   
PTRBFELT *eltptr   
);  
```  
  
#### Parameters  
 *eltptr*  
 Pointer to a pointer to the element to be released.  
  
## Remarks  
 This function should only be used to release surplus elements from a buffer. The [sepdburl](../HIS2010/sepdburl1.md) function should be called to release the entire buffer.  
  
 The released element should first be removed from the element chain and the count of the number of elements updated.  
  
 This function is typically used when a received buffer is being reused to transmit a message that is shorter than the incoming message.