---
description: "Learn more about: sbpibegt"
title: "sbpibegt2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# sbpibegt
The application calls the **sbpibegt** function to get a buffer element to append to an existing buffer.  
  
## Syntax  
  
```  
  
VOID sbpibegt(   
PTRBFELT *eltptr   
);  
```  
  
#### Parameters  
 *eltptr*  
 Pointer to a pointer to an element. On return, this points to a pointer to the element obtained, or to NULL if an element was not obtained (an internal error).  
  
## Remarks  
 This function should only be used to get extra elements for an existing buffer. The [sepdbubl](../core/sepdbubl1.md) function should be used to get a new buffer.  
  
 The new element should be added to the chain of elements from the existing buffer header and the count of the number of elements updated.  
  
 This function is typically used when a received buffer is being reused to transmit a message that is longer than the incoming message.
