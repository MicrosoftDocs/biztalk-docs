---
description: "Learn more about: sbpiberl"
title: "sbpiberl2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
 This function should only be used to release surplus elements from a buffer. The [sepdburl](../core/sepdburl2.md) function should be called to release the entire buffer.  
  
 The released element should first be removed from the element chain and the count of the number of elements updated.  
  
 This function is typically used when a received buffer is being reused to transmit a message that is shorter than the incoming message.
