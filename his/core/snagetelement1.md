---
description: "Learn more about: SNAGetElement"
title: "SNAGetElement1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40961ec9-29f2-4083-b088-a220c950e686
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# SNAGetElement
The **SNAGetElement** function is called by an application to get a buffer element to append to an existing buffer.  
  
```  
VOID SNAGetElement(  
PTRBFELT *eltptr  
);  
```  
  
## Parameters  
 *eltptr*  
 Pointer to a pointer to an element. On return, this points to a pointer to the element obtained, or to NULL if an element was not obtained (an internal error).  
  
## Remarks  
 This function should only be used to get extra elements for an existing buffer. [SNAGetBuffer](../core/snagetbuffer1.md) should be used to get a new buffer.  
  
 The new element should be added to the chain of elements from the existing buffer header and the count of the number of elements updated.  
  
 This function is typically used when a received buffer is being reused to transmit a message that is longer than the incoming message.
